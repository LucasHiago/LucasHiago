<div align="center">

# 🧠 Step-AI Infinity Memory

**Memória de longo prazo para agentes de IA. Sem janela de contexto como teto.**

Camada de memória persistente, recuperável e versionada — o agente lembra do que importa entre sessões, projetos e modelos.

![Python](https://img.shields.io/badge/Python_3.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL_+_pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MCP](https://img.shields.io/badge/Model_Context_Protocol-1A1A1A?style=flat-square)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

</div>

---

> **Contexto não é memória.** A janela do LLM é um buffer volátil; memória é o que sobrevive ao fim da sessão.

O **Step-AI Infinity Memory** é a camada de memória do ecossistema Steply para agentes de IA. Ele resolve o problema central de qualquer agente sério em produção: a janela de contexto é finita e efêmera, mas o conhecimento que o agente acumula — preferências do usuário, decisões tomadas, fatos do domínio, histórico de interações — precisa persistir e ser recuperado sob demanda, sem estourar tokens.

A ideia de "infinity" não é janela de contexto infinita (isso é marketing). É **recuperação seletiva sobre um acervo ilimitado**: a memória cresce sem limite no banco, mas só o que é relevante para o turno atual entra no contexto do modelo.

---

## 🎯 O problema

- **Janela de contexto é teto, não memória.** Tudo que sai da janela é esquecido.
- **Stuffing de histórico não escala.** Reenviar a conversa inteira a cada turno é caro, lento e degrada com o tamanho.
- **Memória ingênua vira ruído.** Salvar tudo e recuperar por similaridade pura traz lixo irrelevante para o contexto.
- **Sem rastreabilidade.** Quando o agente "decide" algo com base no que lembra, você precisa saber *o que* ele lembrou e *por quê*.

---

## 🧩 Os quatro tipos de memória

O Step-AI não trata memória como um blob único. Separa por natureza e ciclo de vida:

| Tipo | O que guarda | Ciclo de vida |
|------|--------------|---------------|
| **Working** | Estado do turno/sessão atual | Volátil — vive enquanto a sessão existe |
| **Episódica** | Eventos e interações datadas ("o usuário pediu X em tal data") | Longa, com decaimento por relevância |
| **Semântica** | Fatos consolidados do domínio e do usuário | Persistente, consolidada a partir de episódios |
| **Procedural** | Padrões de "como fazer" — playbooks que o agente aprendeu | Persistente, reforçada por uso |

A consolidação **episódica → semântica** é o coração do sistema: episódios repetidos e confirmados viram fatos estáveis, reduzindo ruído ao longo do tempo.

---

## 🏗️ Arquitetura

```text
            ┌──────────────────────────────────────┐
            │             Agente (LLM)             │
            │   Claude · LangGraph · ReAct loop    │
            └───────────────┬──────────────────────┘
                            │ MCP (stdio)
                ┌───────────▼────────────┐
                │   step-ai memory MCP    │
                │   server (tools)        │
                │  remember · recall ·    │
                │  forget · consolidate   │
                └───────────┬─────────────┘
        write path  ┌───────┴────────┐  read path
                    ▼                ▼
        ┌────────────────┐   ┌─────────────────────┐
        │ ingest +       │   │ retrieval pipeline   │
        │ embed (MiniLM) │   │ vetor + filtros +    │
        │ + dedupe       │   │ recência + rerank    │
        └───────┬────────┘   └──────────┬───────────┘
                ▼                        ▼
        ┌──────────────────────────────────────────┐
        │      PostgreSQL + pgvector (pg16)         │
        │  memories(embedding, type, scope, ts,     │
        │           salience, source, meta)         │
        └──────────────────────────────────────────┘
```

### Write path (lembrar)
1. **Captura** — o agente chama `remember(...)` com o conteúdo e metadados (escopo, tipo, fonte).
2. **Embed** — gera embedding local (MiniLM-L6-v2, 384d) — sem custo de API por escrita.
3. **Dedupe** — verifica similaridade com memórias existentes; se já existe equivalente, reforça `salience` em vez de duplicar.
4. **Persist** — grava em `memories` com `type`, `scope`, `timestamp`, `salience` e `meta`.

### Read path (recuperar)
1. **Busca vetorial** — top-k por similaridade de cosseno (pgvector, índice HNSW/IVFFlat).
2. **Filtros** — por `scope` (usuário/projeto/global) e `type`, antes do rank.
3. **Recência + saliência** — score combina similaridade, decaimento temporal e `salience`.
4. **Rerank + budget** — corta para caber no orçamento de tokens; só o essencial entra no contexto.

---

## 🛠️ Interface MCP

Exposto via **Model Context Protocol** — qualquer agente compatível (Claude Code, clientes MCP) usa a memória como um conjunto de tools, sem acoplar ao runtime do agente:

| Tool | Descrição |
|------|-----------|
| `remember(content, type, scope, meta?)` | Persiste uma memória (com dedupe e embed automático). |
| `recall(query, scope?, type?, k?)` | Recupera as memórias mais relevantes para a consulta. |
| `forget(id \| filter)` | Remove memórias por id ou por filtro (esquecimento explícito). |
| `consolidate(scope)` | Roda a passagem episódica → semântica, comprimindo histórico em fatos. |

---

## 🧰 Stack

- **Python 3.10+** — runtime do servidor.
- **PostgreSQL 16 + pgvector** — store único para vetores e metadados (sem banco vetorial separado).
- **MiniLM-L6-v2 (384d)** — embeddings locais, baratos e rápidos.
- **MCP (stdio)** — protocolo de integração com agentes.
- **Docker Compose** — `up -d` e a memória está de pé.

> Mesma fundação do [`agentes-langchain-lab`](https://github.com/LucasHiago/agentes-langchain-lab): Postgres + pgvector + MiniLM. Aqui ela vira **infraestrutura compartilhável**, não experimento.

---

## 🧱 Modelo de dados (esboço)

```sql
CREATE TABLE memories (
  id         UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  scope      TEXT NOT NULL,              -- user:123 | project:asteroth | global
  type       TEXT NOT NULL,              -- working | episodic | semantic | procedural
  content    TEXT NOT NULL,
  embedding  VECTOR(384) NOT NULL,
  salience   REAL NOT NULL DEFAULT 1.0,  -- reforçada por uso/dedupe
  source     TEXT,                       -- de onde veio (sessão, tool, usuário)
  meta       JSONB NOT NULL DEFAULT '{}',
  created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
  accessed_at TIMESTAMPTZ
);

CREATE INDEX ON memories USING hnsw (embedding vector_cosine_ops);
CREATE INDEX ON memories (scope, type);
```

---

## 🧭 Princípios de design

- **Recuperar pouco e certo vence recuperar muito.** Precisão de contexto importa mais que recall bruto.
- **Esquecer é uma feature.** Memória sem poda vira ruído; decaimento e `forget` são parte do design.
- **Escopo explícito.** Memória de usuário, de projeto e global nunca se misturam por acidente.
- **Auditável.** Toda recuperação que influencia uma decisão do agente deixa rastro (`source`, `meta`).
- **Modelo-agnóstico.** A memória sobrevive à troca de LLM — o conhecimento não pertence ao modelo.

---

## 🚦 Status

> 🔒 Projeto interno Steply — em desenvolvimento. Este documento descreve a arquitetura e as decisões; o código vive em repositório privado.

**Roadmap resumido:** write/read path básico → consolidação episódica→semântica → políticas de decaimento e poda → multi-tenant por escopo → métricas de qualidade de recuperação.

---

<div align="center">

<sub><i>Contexto é o que o modelo vê agora. Memória é o que ele sabe.</i></sub>

</div>
