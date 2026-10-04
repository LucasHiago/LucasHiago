<div align="center">

<img src="https://asteroth.com.br/img/letters.webp" alt="Asteroth — planeta esférico, mundo player-driven" width="100%" />

# Steply &amp; LucasHiago

**Arquitetura, produto e código com propósito.**

12+ anos resolvendo problemas reais com engenharia sólida — não com framework da moda.

<br />

[![Steply](https://img.shields.io/badge/Steply-steply.com.br-0A84FF?style=for-the-badge)](https://steply.com.br)
[![Manifesto](https://img.shields.io/badge/Pessoal-lucashiago.com.br-1A1A1A?style=for-the-badge)](https://www.lucashiago.com.br)
[![Asteroth](https://img.shields.io/badge/Asteroth-asteroth.com.br-8B0000?style=for-the-badge)](https://asteroth.com.br)
[![Athena](https://img.shields.io/badge/Athena-athena.steply.com.br-F85050?style=for-the-badge)](https://athena.steply.com.br)
[![Kraked](https://img.shields.io/badge/Kraked-kraked.online-5B2A86?style=for-the-badge)](https://kraked.online)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lucashdsf/)
[![Sponsor](https://img.shields.io/badge/Sponsor-EA4AAA?style=for-the-badge&logo=githubsponsors&logoColor=white)](https://github.com/sponsors/LucasHiago)

</div>

---

Dois universos que se cruzam: **Steply** — operação de outsourcing técnico e desenvolvimento de produto para fundadores que precisam de execução, não de promessa — e **LucasHiago**, a identidade técnica por trás das decisões. Backend que é regra de negócio, frontend que é estado e performance, infra que existe pra **não** ser percebida.

> **Código é uma consequência. Arquitetura é uma decisão. Produto é um compromisso.**

---

## 🛠️ Stack

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Angular](https://img.shields.io/badge/Angular_16+-DD0031?style=flat-square&logo=angular&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000?style=flat-square&logo=nextdotjs&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=flat-square&logo=laravel&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL_+_pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-000?style=flat-square&logo=rust&logoColor=white)
![Electron](https://img.shields.io/badge/Electron-47848F?style=flat-square&logo=electron&logoColor=white)
![WebRTC](https://img.shields.io/badge/WebRTC_+_mediasoup-333?style=flat-square&logo=webrtc&logoColor=white)
![ONNX](https://img.shields.io/badge/ONNX_Runtime-005CED?style=flat-square&logo=onnx&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Blender](https://img.shields.io/badge/Blender-E87D0D?style=flat-square&logo=blender&logoColor=white)

Angular quando o projeto exige estado complexo e vida longa · Next.js quando a prioridade é performance e SEO · NestJS no coração de quase tudo · PostgreSQL quando o domínio é sério, `+ pgvector` quando entra IA · C++ no engine do Asteroth · Rust quando o binário precisa ser local, leve e seguro (harness-jev) · Electron nos apps de desktop (Athena, Kraked) · Python no eixo de IA e gamedev tooling.

---

## 🆕 No que estou trabalhando agora <sub>(2025–2026)</sub>

Além de operar a Steply, mantenho frentes próprias que mudaram como eu trabalho: **Athena**, a IDE de comando para agentes de código; **Kraked**, plataforma de comunidade com voz, tela e lojas; um **MMORPG autoral em engine própria**; um **framework de processo spec-driven**; e um **eixo de IA aplicada** que hoje gira em torno de **Jev e Laya**, decisores que escolhem a rota antes de o agente agir.

### 🦉 Athena: centro de comando para agentes de código &nbsp;<sub>🔒 · alpha.12</sub>

IDE desktop (Electron) para quem trabalha com vários agentes ao mesmo tempo (Claude Code, Codex e outros via ACP). Cada projeto tem os terminais reais dos agentes, o histórico de prompts, os arquivos alterados com diff e stage, e os **PRDs viram fila de execução**: a Athena quebra o PRD em itens, entrega um por vez ao agente, acompanha o turno e para quando algo pede decisão humana.

🌐 **[athena.steply.com.br](https://athena.steply.com.br)** &nbsp;·&nbsp; alpha.12 em 03/10/2026, com atualização pelo próprio app (sha256 conferido)

<details>
<summary><b>O que a Athena faz hoje</b></summary>

<br />

- **PRD como fila e piloto.** Checklist montado do texto quando o PRD não tem itens; fila que não trava quando o agente espera um comando em segundo plano; pergunta com opção recomendada e sem risco segue sozinha, e o que é arriscado (produção, push forçado, dependência nova, migration, apagar) espera você.
- **Piloto e modo noturno com trava.** Comando perigoso é recusado na hora, sem ficar pendurado esperando aprovação.
- **Athena Remote (Android).** A Athena do PC no celular: projetos, PRDs, terminais dos agentes, decisões, diff e stage, uso das contas. Pareamento por código, **X25519 + AES-256-GCM de ponta a ponta**, relay no VPS que só repassa e não lê nada. O app se atualiza sem reinstalar, com pacote assinado em **Ed25519**.
- **Projeto do zero com harness.** Cria git, README, `.gitignore`, publica no GitHub ou GitLab e já liga o harness da Steply (plugin do Claude Code + `AGENTS.md` para Codex) no 1º commit.
- **Contas e uso.** Vários logins do Claude Code e do Codex, plano, conta ativa e consumo da sessão (5 h) e da semana, com alerta em 80% e 95%.
- **Memória por projeto** com anonimização antes da injeção, timeline por PRD, Explorer com prévia de CSV e XLSX, busca via ripgrep, worktrees com resolução de conflito 3-way, issues do GitHub, GitLab e Azure DevOps.
- **Laya como backend de decisão padrão** (ver abaixo).

A camada de memória que deu origem a ela está descrita em [`docs/step-ai-infinity-memory.md`](docs/step-ai-infinity-memory.md).

</details>

### 🐙 Kraked: comunidades com voz, tela e loja &nbsp;<sub>🔒 · v1.1.065</sub>

Plataforma de comunicação em tempo real: servidores, canais de texto e voz, chamadas, compartilhamento de tela e **lojas dentro do servidor**. App desktop para Windows, Linux e macOS com auto-update, versão web e uma build **Lite** para PC fraco.

🌐 **[kraked.online](https://kraked.online)** &nbsp;·&nbsp; [novidades de cada versão](https://kraked.online/changelog) · instaladores e auto-update servidos do próprio VPS

<details>
<summary><b>Por dentro</b></summary>

<br />

- **Stack:** Electron + React no cliente, NestJS + Socket.IO + TypeORM + PostgreSQL na API, **mediasoup** como SFU embarcado no app, TURN/STUN próprio com relays em enxame e credencial por pessoa.
- **Chamada que respeita a máquina:** teto de CPU medido no app inteiro (padrão 10%), só desce o vídeo que está na tela e no tamanho do quadro. Sala de 3 com câmera caiu de ~0,95 para ~0,4 núcleo.
- **Tela até 60 fps / 1440p**, com prioridade e banda escolhíveis. No Linux, o som da tela é só do programa escolhido: o PipeWire duplica o stream para um sink que só o Kraked ouve, sem levar a voz da sala.
- **Exibição sincronizada:** o servidor guarda só o ponto do vídeo e cada um toca na própria máquina. Vídeo do computador transmitido para a sala sem passar por servidor.
- **Lojas:** vitrine por servidor, Pix com mensalidade e carência, carteira interna com saldo travado 7 dias, direito de arrependimento (art. 49 do CDC) com devolução que não passa pelo vendedor.
- **Cargos e permissões** granulares por servidor e canal, convite público, menções, diagnóstico da chamada ponta a ponta.

</details>


### 🜏 Asteroth — MMORPG isométrico em planeta esférico

Em desenvolvimento desde **2012**, em engine própria **C++**, sem publisher, sem prazo imposto. O diferencial não é estética: o jogador caminha em volta de uma **esfera real** — horizonte curvo, sol nascendo, duas luas atravessando o céu. **Não é skybox falso, é geometria de planeta.** Civilização 100% player-driven, panteão de 26 governantes.

📖 **[`asteroth-public`](https://github.com/LucasHiago/asteroth-public)** — lore, panteão e 17 concept arts &nbsp;·&nbsp; 🔒 `asteroth-learnings` — ~147 docs de pesquisa + pipeline `lowpoly_generator` &nbsp;·&nbsp; 🔒 `Asteroth` — engine + jogo

<details>
<summary><b>Abrir os três repositórios do projeto</b></summary>

<br />

**🌍 [`asteroth-public`](https://github.com/LucasHiago/asteroth-public) — o canal externo.** Aqui não tem código de jogo, tem **mundo**:
- **Lore cosmogônica** ([`LORE.md`](https://github.com/LucasHiago/asteroth-public/blob/main/LORE.md)) — a origem das partículas, Asteroth como entidade, o planeta físico.
- **Os Governantes** ([`GOVERNANTES.md`](https://github.com/LucasHiago/asteroth-public/blob/main/GOVERNANTES.md)) — panteão de 26 entidades, cada uma com condição de despertar própria.
- **Mecânicas** ([`GAMEPLAY.md`](https://github.com/LucasHiago/asteroth-public/blob/main/GAMEPLAY.md)) — classes, fama, ciclo `explorar → coletar → construir → defender → ser invadido → reconstruir`.
- **Contos** ([`stories/`](https://github.com/LucasHiago/asteroth-public/tree/main/stories)) e **17 concept arts** ([`concepts/worlds/`](https://github.com/LucasHiago/asteroth-public/tree/main/concepts/worlds)), cada um com vinheta curta.

<p align="center">
  <img src="assets/cthulhu.png" width="120" alt="Cthulhu" />
  <img src="assets/azazel.png" width="120" alt="Azazel" />
  <img src="assets/beelzebub.png" width="120" alt="Beelzebub" />
  <img src="assets/metatron.png" width="120" alt="Metatron" />
  <img src="assets/hastur.png" width="120" alt="Hastur" />
</p>
<p align="center"><sub>5 dos 26 governantes do panteão de Asteroth</sub></p>

**🧪 `asteroth-learnings` 🔒 — pesquisa fundacional.** ~147 documentos em 9 pilares (renderização iso, movimento iso, networking, ECS, física, mundo esférico, biomas, infra MMO, integração de stack). Highlight: o **`lowpoly_generator`**, pipeline em produção que converte sprite-sheet ortográfica em mesh low-poly 3D fiel à arte:

```text
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

A descoberta central: **CV clássico (visual hull + primitives + shrinkwrap) bate na parede em fidelidade artística.** A solução foi inverter o paradigma — usar o pipeline pra preparar inputs alinhados (3 vistas em escala métrica + landmarks) e delegar a inferência 3D pra uma IA multi-view. **Híbrido CV + IA generativa** entrega resultado em segundos.

**🔒 `Asteroth` — engine + jogo (privado).** Engine própria em C++, atualmente na **Fase 0: Fundação 3D** (pipeline de renderização — cubo isométrico, depth test, sistema de mesh). Roadmap até infra MMO (Fase 5) e conteúdo (Fase 6+). Stack consolidada em ~22 libs C++ defensivamente avaliadas (Flecs, Jolt, GNS, etc).

</details>

### 🏛️ Steply SDD Harness — spec-driven development como SO do processo &nbsp;<sub>🔒</sub>

O arcabouço que rege como Steply (e Asteroth) saem do papel. Não é metodologia em slide — é um conjunto de regras, templates e ferramentas executáveis que estrutura **épico → issue → spec → código**, tudo rastreável via GitHub CLI e versionado no Git. Porque **arquitetura sem processo vira folclore.**

<details>
<summary><b>O que ele entrega</b></summary>

<br />

- **Hierarquia explícita**: Fase (F#) → Épico (E# = Milestone + Discussion) → Issue → PR. Nenhuma issue órfã.
- **Templates de épico e spec** que padronizam tracking entre Asteroth, Steply e laterais.
- **Style guide arquitetural** — design system Steply replicável (CSS variables, dark/light, tokens).
- **Tooling automatizado** (`bulk_create_epics.py`, `spec_report.py`, `sync_design_specs.py`) — épicos em lote, relatórios de progresso, sincronização de specs entre repos.
- **ERD versionado** como source-of-truth de domínio + **roteiros de implantação** (n8n em VPS e AWS).

Força clareza de escopo antes do commit, deixa rastro auditável das decisões e reduz drasticamente o custo de onboard em projetos longos.

</details>

### 🤖 IA aplicada — MCP, Blender e agentes

Não como buzzword. Como ferramenta de produção.

<details>
<summary><b>🎬 <code>anime-maker</code> — pipeline <code>prompt → MP4</code> via MCP + Blender 🔒</b></summary>

<br />

Pipeline pra **criar animes** controlando Blender remotamente via **Model Context Protocol** (MCP stdio):

1. IA gera concept art 2D do personagem (Fal.ai)
2. IA converte imagem → modelo 3D rigado (Meshy.ai, image-to-3d + auto-rigging)
3. Blender controlado via MCP monta a cena, aplica animação pronta (walk/run)
4. Render **NPR vanilla** (Toon BSDF via Shader-to-RGB + ColorRamp + Freestyle), câmera ortográfica pra "sensação 2D" anime
5. Frames PNG + MP4 (ffmpeg) saem prontos por episódio

CLI Typer end-to-end. Stack: Python 3.10+ · Typer · MCP · Blender · Meshy.ai. É a **prova de conceito** de que MCP + Blender + image-to-3D monta um pipeline cinematográfico controlado por linguagem natural, sem operador artista no loop.

</details>

<details>
<summary><b>🧠 <code>agentes-langchain-lab</code> — agentes do zero, sem framework escondendo as engrenagens 🔒</b></summary>

<br />

```text
   pergunta ──► researcher ───► writer ──► resposta
                 │ tool: search_docs
                 ▼
           PGVector (pg16) ← embeddings MiniLM (384d)
```

- Orquestração: **LangGraph** (`StateGraph`) — fluxo entre agentes explícito e inspecionável
- Agentes: **LangChain** `create_react_agent` (loop ReAct)
- LLM: **Claude Haiku 4.5** · Vector store: **PostgreSQL + pgvector** · Embeddings: **MiniLM-L6-v2** local
- Infra: Docker Compose, `up -d` e tá pronto

O ponto: trocar peças (LLM, tool, vetor, política de roteamento) e ver o efeito imediato, sem framework de alto nível escondendo o que acontece.

</details>

<details>
<summary><b>🐱 <code>harness-jev</code> + Jev + Laya: um seletor escolhe a rota antes de o agente agir 🔒</b></summary>

<br />

Workspace de código **local-first para Linux, em Rust**, porte de um código-base MIT. Roda os agentes que já uso (Claude Code, Codex, Cursor, Grok, Hermes, pi via ACP) e um loop DeepSeek embutido. Antes de cada tarefa, um **seletor** escolhe entre as rotas que o host preparou, ou se abstém, e o host confere a escolha antes de aplicar.

| modo | onde roda | o que decide |
| --- | --- | --- |
| **Laya** (padrão) | local, CPU | se a tarefa pede mudança ou é pergunta; o host escolhe o foco de cada passo pelo progresso do turno |
| **Jev** (opt-in) | hospedado (TypeSafe) | rota de código e foco, com a chave guardada em arquivo 0600 |
| Normal | | pula o seletor |

- **Laya em ONNX Runtime, dentro do processo:** sem Python e sem GPU. Modelo de ≈380 MB conferido por SHA-256; com o serviço local (socket Unix 0600, sem porta de rede) cada decisão cai de ~1,4 s / 290 MB para **~0,2 s / 37 MB**. Contra um `laya-serve` em GPU fp16: **~20–30 ms**.
- **Medido antes de usar.** `tools/laya-eval` separa `dev` e `holdout`: perguntas de foco e de modelo foram **abandonadas** (18% e "escolhe ponta para tudo"); ficou só "mudança ou pergunta?", com 80% de acerto e **100% de precisão ao aplicar** no holdout.
- **Seleção nunca concede permissão.** Escolha inválida, velha ou abstenção cai na rota original; o host recusa sozinho `push --force`, push em `main`, `reset --hard`, `rm -rf` amplo e escrita em `.env` ou chaves.
- Instalação em um comando, instalador visual em Electron e AppImage com o modelo embutido.
- **`laya-serve` no meu PM2** com um porteiro que acorda o modelo sob demanda e desliga depois de 10 min parado, travado no checkpoint multilíngue em fp16 (VRAM de 1,25 GB para 0,63 GB). Athena e harness-jev consomem o mesmo serviço.

Laya é um modelo aberto ([NandhaKishorM/laya](https://github.com/NandhaKishorM/laya), Apache-2.0); o meu trabalho é o porte para ONNX, a integração, a avaliação e o serviço.

</details>

<details>
<summary><b>📈 <code>neotrader</code>: Jev e Laya fora do código, decidindo entrada no mercado 🔒</b></summary>

<br />

Robô de day trade na Nelogica (ProfitDLL). A estratégia propõe a entrada, o **Jev** confirma ou manda esperar e o gestor de risco tem a última palavra. Os padrões em que o Jev disse "seguir" e o mercado deu razão viram **critérios da Laya**, que roda local em ~30 ms, sem custo por pergunta.

```text
negócio → candle → estratégia → risco (veto) → Jev/Laya → risco (ordem) → corretora
                                                  ↓
                    caderno (resposta do Jev + desfecho) → critérios da Laya
```

Os dois falam o mesmo protocolo (`/v1/systemone`: estado + perguntas tipadas, resposta com probabilidade), em cascata ou em corrida. Qualquer dúvida vira **esperar**, e o decisor nunca libera o que o risco vetou. Python 3.11+, sem dependência em tempo de execução.

</details>

📚 **[`SKILLS`](https://github.com/LucasHiago/SKILLS)** — skills públicas no padrão Claude Code, baseadas nos artigos do `lucashiago.com.br` e focadas em fluxo Steply.

---

## 🧠 Filosofia de engenharia

- Simplicidade antes de abstração
- Escala pensada desde o MVP
- Código legível vence código esperto
- Frontend não é só UI — é estado, performance e experiência
- Backend não é CRUD — é regra de negócio
- Infra existe para **não ser percebida**

---

<details>
<summary><h3>📦 Ecossistema &amp; histórico — produtos em produção e no forno</h3></summary>

<br />

**Steply em produção e em desenvolvimento:**

- **Athena** e **Kraked** — os dois produtos de desktop descritos acima.
- **`services.steply.pm2`** — orquestração PM2 dos serviços Steply (realtime chat com WebRTC + ICE relay, blog publisher SSR, integrações).
- **`build-market-business` (frontend / dashboard)** — produto B2B em React.
- **`main.steply.build`** — site institucional · **`lp.email.sender`** — disparador de campanhas próprio · **[`lucashiago.resume`](https://github.com/LucasHiago/lucashiago.resume)** — currículo como HTML versionado.
- **[`integration-mercado-pago-nestjs`](https://github.com/LucasHiago/integration-mercado-pago-nestjs)** — integração de pagamentos NestJS.

**Históricos que ainda ensinam (e às vezes ainda rodam em produção):**

- **[`galax-api`](https://github.com/LucasHiago/galax-api) / [`galax-commerce`](https://github.com/LucasHiago/galax-commerce)** — núcleo NestJS + camada de e-commerce desacoplada, backend-first.
- **Poker Electron** — desktop multiplataforma, prova de que Electron não é gambiarra quando bem arquitetado.
- **NFMEI** — sistema fiscal pra microempreendedores, simplificando o que sistemas enterprise complicam.
- **Fashion Manager** — gestão de coleções e estoque; o desafio era traduzir negócio específico pra software sem forçar o cliente a se adaptar.
- **docsModule (NestJS)** — módulo reutilizável de documentação viva de APIs.

</details>

<details>
<summary><h3>🏗️ Consultoria &amp; operação técnica</h3></summary>

<br />

Além dos projetos autorais, entro em projetos onde o escopo já estava atrasado, o código já estava frágil e a arquitetura já tinha dado sinais de colapso.

Aplicações típicas: sistemas administrativos, backoffices complexos, dashboards operacionais, migração de legado, reestruturação de código caótico, performance tuning de banco — prazo curto com impacto real.

</details>

---

## 📖 Livro autoral

Sou autor de um livro próprio. Não é tutorial de framework — é sobre **fundamentos reais de software, engenharia e pensamento técnico**: como pensar sistemas antes de escrever código, como evitar decisões técnicas irreversíveis, como diferenciar complexidade necessária de complexidade inútil. Escrito a partir de projetos reais — os que escalaram, os que quebraram, os que ensinaram mais do que sucesso.

> Software não é sobre ferramentas. É sobre decisões.

---

## 🧭 O fio condutor

Todos esses projetos compartilham algo: código que alguém vai manter, arquitetura que explica decisões, produto que respeita o usuário, engenharia que respeita o tempo. Nem tudo vira vitrine — mas tudo vira **base**.

**Steply é o veículo. Athena e Kraked são o produto. Asteroth é a obra de longo prazo. LucasHiago é o arquiteto.**

---

<div align="center">

[![Steply](https://img.shields.io/badge/Steply-steply.com.br-0A84FF?style=for-the-badge)](https://steply.com.br)
[![Pessoal](https://img.shields.io/badge/Pessoal-lucashiago.com.br-1A1A1A?style=for-the-badge)](https://www.lucashiago.com.br)
[![Asteroth](https://img.shields.io/badge/Asteroth-asteroth.com.br-8B0000?style=for-the-badge)](https://asteroth.com.br)
[![Athena](https://img.shields.io/badge/Athena-athena.steply.com.br-F85050?style=for-the-badge)](https://athena.steply.com.br)
[![Kraked](https://img.shields.io/badge/Kraked-kraked.online-5B2A86?style=for-the-badge)](https://kraked.online)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lucashdsf/)

<br /><br />

<sub><i>Software não é arte abstrata. É engenharia aplicada ao mundo real.<br />Projetos passam. Arquitetura fica.</i></sub>

</div>
