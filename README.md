# 🚀 Steply & LucasHiago
Arquitetura, produto e código com propósito

Este repositório representa dois universos que se cruzam: **Steply**, uma operação de tecnologia focada em execução real de produto, e **LucasHiago**, a identidade técnica por trás das decisões, arquitetura e código.

Não é sobre frameworks da moda.
É sobre **resolver problemas reais com engenharia sólida**.

---

## 🌐 Os dois lados

### 🔗 Steply
**Site:** https://steply.com.br

Operação de **outsourcing técnico e desenvolvimento de produto** focada em startups, empresas em crescimento e fundadores que precisam de execução, não de promessa.

A Steply nasce da dor clássica do mercado:
- Projetos que não saem do papel
- Código sem dono
- Arquitetura improvisada
- Times inchados sem eficiência

A proposta: **engenharia responsável, entrega contínua e visão de negócio**.

### 🔗 LucasHiago
**Site:** https://www.lucashiago.com.br

Manifesto técnico. Não é portfólio genérico, é um mapa mental de como eu penso software, produto, arquitetura e crescimento. Mora aqui:

- Estudos e experimentos
- Provas de conceito
- Manifestos e artigos técnicos
- Ideias que ainda não viraram produto

---

## 🧠 Filosofia de Engenharia

> Código é uma consequência.
> Arquitetura é uma decisão.
> Produto é um compromisso.

Princípios que guiam tudo aqui:

- Simplicidade antes de abstração
- Escala pensada desde o MVP
- Código legível vence código esperto
- Frontend não é só UI, é estado, performance e experiência
- Backend não é CRUD, é regra de negócio
- Infra existe para **não ser percebida**

---

## 🆕 Marcos recentes (2025–2026)

Os últimos meses foram um salto: além de operar a Steply, abri três frentes próprias que mudaram como eu trabalho — **um framework de processo (SDD harness)**, **um MMORPG autoral em planeta esférico (Asteroth)** e **um eixo IA aplicada com MCP + Blender + agentes**. Cada uma vira seção abaixo, com a foto real do que existe hoje.

---

## 🏛️ Steply SDD Harness — `steply-sdd-harness-arch`

> Spec-Driven Development como sistema operacional do processo.

O harness é o **arcabouço de spec-driven development** que rege como Steply (e Asteroth) saem do papel. Não é metodologia em slide — é um conjunto de regras, templates e ferramentas executáveis que estrutura **épico → issue → spec → código**, com tudo rastreável via GitHub CLI (`gh`) e versionado no Git.

### O que ele entrega

- **Hierarquia explícita**: Fase (F#) → Épico (E# = Milestone + Discussion) → Issue → PR. Nenhuma issue órfã. Todo épico tem dois artefatos no GitHub (Milestone como fonte de verdade do status + Discussion como checklist viva do escopo).
- **Templates de épico e spec** (`docs/templates/EPIC.md`, `EPICS.md`) que padronizam tracking entre Asteroth, Steply e laterais.
- **Style guide arquitetural** (`STYLE_GUIDE.md`) — design system Steply replicável (CSS variables, dark/light, tokens) e padrões de stack para dashboards e produtos do ecossistema.
- **Tooling automatizado** (`tools/`): `bulk_create_epics.py`, `spec_report.py`, `sync_design_specs.py` — épicos em lote, relatórios de progresso, sincronização de specs entre repos.
- **ERD versionado** como source-of-truth de domínio (`erd/source-of-truth/`, `erd/changelog.json`).
- **Roteiros de implantação** (n8n VPS e AWS) prontos para reproduzir infra de automação.

### Por que existe

Porque **arquitetura sem processo vira folclore**. O harness força clareza de escopo antes do commit, deixa rastro auditável das decisões e reduz drasticamente o custo de onboard em projetos longos como o Asteroth.

---

## 🜏 Asteroth — MMORPG isométrico em planeta esférico

> Em desenvolvimento desde 2012, em engine própria C++, sem publisher, sem prazo imposto.

O Asteroth não é mais "ideia + concept art". É um projeto vivo, dividido em três repositórios complementares, e estruturado pelo SDD harness acima.

### 🌍 [`asteroth-public`](https://github.com/LucasHiago/asteroth-public) — o canal externo

Espaço público do mundo. Aqui não tem código de jogo, tem **mundo**:

- **Lore cosmogônica** ([`LORE.md`](https://github.com/LucasHiago/asteroth-public/blob/main/LORE.md)) — a origem das partículas, Asteroth como entidade, o planeta físico (esfera real, sol, duas luas, civilização 100% player-driven).
- **Os Governantes** ([`GOVERNANTES.md`](https://github.com/LucasHiago/asteroth-public/blob/main/GOVERNANTES.md)) — panteão de 26 entidades (Cthulhu, Azazel, Beelzebub, Metatron, Hastur, Abaron, Abaddon, Mammon, Baphomet, Asratheet + 16 regentes menores), cada um com condição de despertar própria.
- **Mecânicas** ([`GAMEPLAY.md`](https://github.com/LucasHiago/asteroth-public/blob/main/GAMEPLAY.md)) — classes, fama, ciclo `explorar → coletar → construir → defender → ser invadido → reconstruir`.
- **Contos** ([`stories/`](https://github.com/LucasHiago/asteroth-public/tree/main/stories)) — material narrativo curto, candidato a virar livro.
- **Conceitos visuais** ([`concepts/worlds/`](https://github.com/LucasHiago/asteroth-public/tree/main/concepts/worlds)) — 17 concept arts do mundo, cada uma com vinheta curta.
- **Status pública** via [`CHANGELOG.md`](https://github.com/LucasHiago/asteroth-public/blob/main/CHANGELOG.md).

### 🧪 [`asteroth-learnings`](https://github.com/LucasHiago/asteroth-learnings) — pesquisa fundacional

Repositório de pesquisa técnica do projeto. ~147 documentos divididos em 9 pilares (renderização iso, movimento iso, networking, ECS, física, mundo esférico, biomas, infra MMO, integração de stack).

Highlight: o **`lowpoly_generator`** — pipeline em produção que converte sprite-sheet ortográfica (front/side/back, escala em metros) em mesh low-poly 3D fiel à arte:

```
sprite sheet ortográfico
   ↓ slice_sheets.py (Blender)
slices + metadata (bbox + m_per_px)
   ↓ 01_extract/ — 8 features por slice
silhouette · keypoints · edges · palette · depth · normals · parts · symmetry
   ↓ 02_fuse/ — landmarks 3D + visual hull
   ↓ 06_ai/run_hunyuan_cloud.py
Hunyuan3D-2 multi-view via HF Space (~5s)
   ↓ postprocess: decimate (~2k tris) + rescale métrico
character.glb pronto pra engine
```

A descoberta central da pesquisa: **CV clássico (visual hull + primitives + shrinkwrap) bate na parede em fidelidade artística**. A solução foi inverter o paradigma — usar nosso pipeline pra preparar inputs alinhados (3 vistas em escala métrica + landmarks) e delegar a inferência 3D pra uma IA multi-view. **Híbrido CV + IA generativa** entrega resultado em segundos.

A stack escolhida pro engine está consolidada em `research/10-integration/` (~22 libs C++ defensivamente avaliadas — Flecs, Jolt, GNS, etc).

### 🔒 [`Asteroth`](https://github.com/LucasHiago/Asteroth) — engine + jogo (privado)

Engine própria em C++. Atualmente na **Fase 0: Fundação 3D** (pipeline de renderização — cubo isométrico, depth test, sistema de mesh). Roadmap segue até MMO infra (Fase 5) e conteúdo (Fase 6+).

Diferencial técnico do mundo: o jogador caminha em volta de uma esfera real, com horizonte curvo, sol nascendo e duas luas atravessando o céu — **não é skybox falso, é geometria de planeta**.

---

## 🤖 Eixo IA aplicada — MCP, Blender e agentes

Não como buzzword. Como ferramenta de produção.

### 🎬 `anime-maker` — pipeline `prompt → MP4` via MCP + Blender

Pipeline pra **criar animes** controlando Blender remotamente via **Model Context Protocol** (MCP stdio):

1. IA gera concept art 2D do personagem (Fal.ai)
2. IA converte imagem → modelo 3D rigado (Meshy.ai, image-to-3d + auto-rigging)
3. Blender controlado via MCP monta a cena, aplica animação pronta (walk/run)
4. Render **NPR vanilla** (Toon BSDF via Shader-to-RGB + ColorRamp + Freestyle) frame a frame, câmera ortográfica para a "sensação 2D" anime
5. Frames PNG + MP4 (ffmpeg) saem prontos por episódio

CLI Typer end-to-end: `anime-maker init → character build → scene new → scene add-character → animate → render`. Stack: Python 3.10+ · Typer · MCP · Blender · Meshy.ai.

Este projeto é a **prova de conceito** de que MCP + Blender + image-to-3D dá pra montar um pipeline cinematográfico controlado por linguagem natural, sem operador artista no loop.

### 🧠 `agentes-langchain-lab` — agentes do zero, sem framework escondendo as engrenagens

Lab pessoal pra estudar **orquestração de agentes** com peças trocáveis:

```
   pergunta ──► researcher ───► writer ──► resposta
                 │ tool: search_docs
                 ▼
           PGVector (pg16) ← embeddings MiniLM (384d)
```

- Orquestração: **LangGraph** (`StateGraph`) — fluxo entre agentes explícito e inspecionável
- Agentes: **LangChain** `create_react_agent` — loop ReAct ("pensa → chama tool → observa")
- LLM: **Claude Haiku 4.5** (barato pra iterar)
- Vector store: **PostgreSQL + pgvector** (sem subir mais uma peça de infra)
- Embeddings: **MiniLM-L6-v2** local (zero API key extra)
- Infra: Docker Compose, `up -d` e tá pronto

O ponto: trocar peças (LLM, tool, vetor, política de roteamento) e ver o efeito imediato, sem framework de alto nível escondendo o que está acontecendo.

### 📚 [`SKILLS`](https://github.com/LucasHiago/SKILLS) — skills públicas

Skills (no padrão Claude Code) baseadas nos artigos do `lucashiago.com.br`, focadas em fluxo Steply. Repositório público.

---

## 🛠️ Stack principal

### 🎨 Frontend

**Angular 16+** — usado quando o projeto exige estado complexo, forms robustos, longa vida útil e escalabilidade de equipe. Signals, Standalone Components, SCSS com design system próprio, PWA first, arquitetura orientada a domínio.

**React / Next.js** — usado quando a prioridade é performance, SEO, time-to-market, dashboards e produtos B2B. App Router, Server Components, TanStack Query, Bryntum Gantt, integração pesada com APIs e estados complexos.

### ⚙️ Backend

**NestJS** — o coração de quase tudo. Arquitetura clara, escala natural, código previsível, ótimo pra times. DTOs bem definidos, Guards e Interceptors, domain-driven migrations, integração com filas, workers e IA. APIs pensadas pra evolução, não só pra funcionar hoje.

**Laravel** — usado estrategicamente em sistemas administrativos, backoffices e projetos legados bem tratados. Laravel 9+, Vue 2.7, Policies bem definidas, permissões com Spatie.

### 🗄️ Banco

**PostgreSQL** quando o projeto é sério — domínios customizados, tipos fortes, triggers conscientes, migrações versionadas. **+ pgvector** quando entra IA/RAG.
**MySQL / MariaDB** quando o contexto pede compatibilidade ou legado — diagnóstico de performance, slow query log, índices bem pensados, sem `SELECT *`.

### ☁️ DevOps & Infra

Docker & Docker Compose · PM2 · Vercel · Linux first · monitoramento real, não só dashboard bonito · scripts próprios pra diagnóstico e manutenção · **n8n self-hosted** em VPS e AWS (roteiros prontos no SDD harness).

Infra aqui não é luxo. É **fundação**.

### 🤖 IA & Automação

- LLMs locais (Ollama)
- Claude API (Anthropic) — Opus/Sonnet/Haiku por tier de tarefa, prompt caching obrigatório
- **MCP** — Model Context Protocol como ponte para Blender, Google Drive, Canva e tooling próprio
- LangGraph + LangChain pra agentes orquestrados
- pgvector pra RAG
- TTS com Piper
- IA integrada ao produto, não jogada por cima

### 🎮 Gamedev

C++ próprio (engine Asteroth) · GDScript (Godot) · Blender via Python `bpy` e via MCP.

---

## 📦 Outros projetos & produtos

Ecossistema Steply em produção e em forno:

- **`services.steply.pm2`** — orquestração PM2 dos serviços Steply (realtime chat com WebRTC + ICE relay, blog publisher SSR, integrações).
- **`build-market-business-frontend` / `-dashboard`** — produto B2B em React.
- **`main.steply.build`** — site institucional.
- **`-F-DevSRC`** — base TypeScript.
- **`integration-mercado-pago-nestjs`** — integração de pagamentos NestJS.
- **`lp.email.sender`** — disparador de campanhas próprio.
- **`lucashiago.resume`** — currículo enquanto HTML versionado.

Históricos que ainda ensinam (e às vezes ainda rodam em produção):

- **galax-api / galax-commerce** — núcleo NestJS + camada de e-commerce desacoplada, backend-first.
- **Poker Electron** — desktop multiplataforma, prova de que Electron não é gambiarra quando bem arquitetado.
- **NFMEI** — sistema fiscal pra microempreendedores, simplificando o que sistemas enterprise complicam.
- **Fashion Manager** — gestão de coleções e estoque, o desafio era traduzir negócio específico pra software sem forçar o cliente a se adaptar.
- **docsModule (NestJS)** — módulo reutilizável de documentação viva de APIs, pensado pra padronizar Swagger em projetos grandes sem poluir controllers.

---

## 🏗️ Consultoria & operação técnica

Além dos autorais, atuo entrando em projetos onde:

- O escopo já estava atrasado
- O código já estava frágil
- A arquitetura já tinha dado sinais de colapso

Aplicações típicas: sistemas administrativos, backoffices complexos, dashboards operacionais, migração de legado, reestruturação de código caótico, performance tuning de banco, prazo curto com impacto real.

---

## 📖 Livro autoral

Sou autor de um livro próprio. Não é tutorial de framework, é sobre **fundamentos reais de software, engenharia e pensamento técnico** — como pensar sistemas antes de escrever código, como evitar decisões técnicas irreversíveis, como diferenciar complexidade necessária de complexidade inútil, como arquitetura, produto e negócio se cruzam no mundo real.

Escrito a partir de projetos reais — os que escalaram, os que quebraram, os que ensinaram mais do que sucesso.

> Software não é sobre ferramentas. É sobre decisões.

---

## 🧭 O fio condutor

Todos esses projetos compartilham algo:

- Código que alguém vai manter
- Arquitetura que explica decisões
- Produto que respeita o usuário
- Engenharia que respeita o tempo

Nem tudo vira vitrine. Mas tudo vira **base**.

Steply é o veículo. Asteroth é a obra de longo prazo. LucasHiago é o arquiteto.

---

## 📫 Contato

- Site Steply: https://steply.com.br
- Site pessoal: https://www.lucashiago.com.br
- Asteroth: https://asteroth.com.br
- LinkedIn: https://www.linkedin.com/in/lucashdsf/
- GitHub Sponsors: https://github.com/sponsors/LucasHiago

---

> Software não é arte abstrata.
> É engenharia aplicada ao mundo real.
>
> Projetos passam.
> Arquitetura fica.
