# Changelog

Versões do plugin `fluxo-produto-plaenge`. Formato: [versionamento semântico](https://semver.org/lang/pt-BR/).

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
