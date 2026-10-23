# Changelog

Versões do plugin `fluxo-produto-plaenge`. Formato: [versionamento semântico](https://semver.org/lang/pt-BR/).

## [0.6.0] — 2026-10-23

### Adicionado
- Etapa 1 gera o `01-persona.md`, ao lado do contexto, do benchmark e do roteiro: uma persona
  por persona do MD de Persona, com síntese em 10 itens, jornada, origem e pendências. Sem MD
  de Persona (ou para perfil da TAP sem persona no MD), a persona é gerada a partir da TAP, só
  com o que a TAP diz e o resto `[pendente]`. Formato em `references/estrutura-persona.md`.
- O `01-persona.md` é incremental e sem versão, como o contexto: a etapa 2 o atualiza com o que
  a entrevista de cada persona revelou, e as etapas 3 e 4 o consultam (dispositivo, local de
  trabalho, familiaridade com tecnologia).

### Alterado
- As personas saem do contexto: a seção 10.2 deixa de existir e a seção 10 volta a ser uma
  tabela de perfis, com a coluna Persona apontando para o `01-persona.md`. O contexto continua
  consolidando por tema o que as personas relatam (§5, §7, §12, §14). Gates 1 e 2, pacote de
  entrada, roteiro, fluxograma e README atualizados.
- Contexto do Projeto passa a ser um arquivo único e incremental, sem número de versão: cada
  etapa atualiza no lugar só as seções afetadas e registra a alteração no novo Registro de
  alterações (data, etapa, seções, o que mudou). O marco de validação deixa de ser a v1.0 e
  passa a ser o Status (Rascunho → Validado). Convenções, etapas 2 a 5, Gate 2, pacote de
  entrada, `estado.md`, fluxograma e README atualizados. Os demais artefatos `.md` continuam
  versionados.
- Benchmark fica só em `01-benchmark.md`, com versão própria: a seção 15 (Benchmark de
  mercado) sai do contexto e as seções 16–21 passam a 15–20 (Lacunas e gaps agora é a 15).
  Contextos de projetos já em andamento mantêm a numeração antiga.

## [0.5.0] — 2026-10-23

### Adicionado
- MD de Persona como entrada da etapa 1, ao lado da TAP: síntese do perfil em 10 itens e fluxo
  de trabalho / mapa de jornada. Modelo em `skills/entendimento-tap/assets/modelo-persona.md`.
- Referência `persona.md` (etapa 1): natureza da fonte, item → seção do contexto, cruzamento
  com a TAP, completude, gatilhos de entrevista e tratamento da ausência.
- Contexto do Projeto: seção 10 dividida em 10.1 Perfis (com coluna Persona) e 10.2 Personas
  (síntese e jornada por persona). Nenhuma seção renumerada.

### Alterado
- Etapa 1: o MD de Persona é copiado para `fontes/`, inventariado como FON e consolidado no
  contexto; a entrevista em profundidade passa a ser por persona. Sem o MD, a etapa segue e
  registra a ausência como lacuna crítica, com pergunta e material a pedir.
- Orquestrador: abertura confere o MD de Persona e indica o modelo; pacote de entrada e Gate 1
  atualizados.
- Fluxograma com a verificação do MD de Persona na abertura.
- Prontidão para protótipo (etapa 2): o item de perfis verifica a seção 10.1, como antes da
  divisão da seção 10.

## [0.4.0] — 2026-10-23

### Adicionado
- Suporte ao GitHub Copilot (VS Code e CLI) pelo mesmo marketplace e a outras ferramentas que
  leem skills `SKILL.md` (Codex, Cursor, Gemini CLI). Instruções de instalação por ferramenta no
  README.
- Seção "Ferramentas da plataforma" no orquestrador, com equivalência de ferramentas e execução
  das etapas na própria sessão quando não houver subagentes.

### Alterado
- Agentes renomeados para `agents/<agente>.agent.md`, sem `tools` nem `model` no cabeçalho.
- Skills e referências citam a ação (perguntar, chamar subagente, buscar na web) em vez de
  ferramentas exclusivas do Claude (`AskUserQuestion`, `Agent`, `Skill`, `SendUserMessage`,
  `WebSearch`/`WebFetch`).
- Script do documento ADS chamado pelo caminho da pasta da skill, sem depender de
  `${CLAUDE_PLUGIN_ROOT}`, e com `python` como comando padrão.
- `plugin.json` declara o servidor MCP do Figma (`mcpServers`).

## [0.3.0] — 2026-10-23

### Alterado
- Marketplace renomeado de `plaenge-local` para `plaenge-produto`. Quem instalou pelo nome
  antigo precisa remover o marketplace antigo e instalar de novo (ver README → Instalação).

### Adicionado
- Seção de instalação, instalação automática por projeto e versionamento no README.
- Este CHANGELOG.

### Corrigido
- Linha final do README gravada em UTF-16.

## [0.2.0] — 2026-10-23

- Entrevista em profundidade, roteiro de reunião revisado e novas referências de técnicas de
  entrevista (etapa 1).
- Estrutura da pasta do projeto e exigências do benchmark detalhadas.
- Fluxograma do fluxo de produto (`docs/fluxograma.md`).

## [0.1.0] — 2026-10-22

- Primeira versão: orquestrador `fluxo-produto` e as cinco etapas (Entendimento da TAP,
  Reunião de entendimento, Protótipo, Requisitos e Documento de especificação ADS).
