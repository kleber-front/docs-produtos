# Fluxo de Produto — Grupo Plaenge

Fluxo de agentes que leva um projeto da TAP ao Documento de especificação ADS.

| # | Etapa | Skill | Agente | Entrega |
|---|-------|-------|--------|---------|
| — | Orquestrador | `fluxo-produto` | — | `estado.md`, gates, rodadas de perguntas |
| 1 | Entendimento da TAP | `entendimento-tap` | `agente-entendimento-tap` | Contexto do Projeto v0.x, benchmark, roteiro da reunião |
| 2 | Reunião de entendimento | `reuniao-entendimento` | `agente-reuniao-entendimento` | Ata, Contexto v1.0, prontidão para protótipo |
| 3 | Protótipo | `prototipo-navegavel` | `agente-prototipo` | Protótipo React, mapa de telas, capturas, Design System, telas no Figma |
| 4 | Requisitos | `requisitos-projeto` | `agente-requisitos` | RN, RF por tela, RNF, RT, técnicos (DT, INT, ENT, infra/segurança), CT |
| 5 | Documentação | `documentacao-especificacao` | `agente-documentacao` | `.docx` no modelo ADS |

Depois da etapa 5, o orquestrador pode seguir para `estruturacao-backlog` e
`preparacao-estimativa`, se essas skills estiverem instaladas no ambiente.

## Instalação

O mesmo repositório funciona como marketplace de plugins para o **GitHub Copilot** (VS Code e
CLI) e para o **Claude Code**. Para outras ferramentas que leem skills no formato `SKILL.md`,
veja [Outras ferramentas](#outras-ferramentas).

O repositório é privado: é preciso ter acesso de leitura a ele e o git autenticado na máquina
(`gh auth login` ou credencial do Git for Windows).

### GitHub Copilot no VS Code

Requer o VS Code com o GitHub Copilot Chat e a opção `chat.plugins.enabled` ligada.

1. Adicione o marketplace no `settings.json` do usuário (ou do workspace):

   ```json
   "chat.plugins.marketplaces": ["kleber-front/docs-produtos"]
   ```

2. Na visão **Extensions**, procure por `@agentPlugins`, encontre `fluxo-produto-plaenge` e
   clique em **Install**. Confirme o aviso de confiança do marketplace.
3. Para instalar sem marketplace, rode no Command Palette **Chat: Install Plugin From Source**
   e informe `https://github.com/kleber-front/docs-produtos`.

Plugins instalados pelo Copilot CLI também aparecem automaticamente no VS Code.

### GitHub Copilot CLI

```
copilot plugin marketplace add kleber-front/docs-produtos
copilot plugin install fluxo-produto-plaenge@plaenge-produto
```

Confira com `copilot plugin list` e, numa sessão, com `/skills list` e `/agent`.
Para receber versões novas: `copilot plugin marketplace update plaenge-produto` e
`copilot plugin update fluxo-produto-plaenge`.

### Claude Code

```
/plugin marketplace add kleber-front/docs-produtos
/plugin install fluxo-produto-plaenge@plaenge-produto
```

Depois de instalar, reinicie o Claude Code e confira em `/plugin` se o `fluxo-produto-plaenge`
aparece habilitado. Para receber versões novas: `/plugin marketplace update plaenge-produto`.

Para que o Claude Code ofereça o plugin a quem abrir um repositório da equipe, inclua no
`.claude/settings.json` desse repositório:

```json
{
  "extraKnownMarketplaces": {
    "plaenge-produto": {
      "source": { "source": "github", "repo": "kleber-front/docs-produtos" }
    }
  },
  "enabledPlugins": {
    "fluxo-produto-plaenge@plaenge-produto": true
  }
}
```

### Outras ferramentas

Codex, Cursor, Gemini CLI e outros assistentes que leem skills no formato `SKILL.md`:

1. Clone o repositório.
2. Copie as pastas de `skills/` para a pasta de skills da ferramenta (do usuário ou do
   projeto), mantendo uma pasta por skill com o `SKILL.md` dentro.
3. Se a ferramenta suportar agentes personalizados, copie também `agents/*.agent.md` para a
   pasta de agentes dela. Sem agentes, o orquestrador executa cada etapa na própria sessão
   (ver "Ferramentas da plataforma" em `skills/fluxo-produto/SKILL.md`).
4. Configure o servidor MCP do Figma (`https://mcp.figma.com/mcp`, HTTP), se a ferramenta
   suportar MCP.

Para atualizar, rode `git pull` no clone e copie as pastas de novo.

### Compatibilidade entre ferramentas

As skills e os agentes descrevem a ação (perguntar ao usuário, chamar subagente, buscar na
web) em vez do nome da ferramenta, para funcionar em qualquer assistente. Ao editar, mantenha
essa regra: não cite ferramentas de uma plataforma só sem indicar a alternativa. Agentes ficam
em `agents/` com extensão `.agent.md` e sem lista de `tools` nem `model` no cabeçalho, para
serem lidos tanto pelo Copilot quanto pelo Claude Code.

## Versionamento

O plugin segue [versionamento semântico](https://semver.org/lang/pt-BR/) (`MAIOR.MENOR.CORREÇÃO`).
O histórico fica no [CHANGELOG.md](CHANGELOG.md).

| Mudança | Sobe | Exemplo |
|---------|------|---------|
| Quebra o uso para quem já instalou ou para projetos em andamento: renomear skill, agente ou marketplace; mudar nomes de arquivos em `fluxo/<projeto>/` ou o formato do `estado.md` | MAIOR (MENOR enquanto estiver em `0.x`) | 0.3.0 → 0.4.0 |
| Nova etapa, skill, referência ou capacidade, sem quebrar o que existe | MENOR | 0.3.0 → 0.4.0 |
| Ajuste de texto, correção de regra ou de script, sem mudar o comportamento esperado | CORREÇÃO | 0.3.0 → 0.3.1 |

O Copilot e o Claude Code só entregam a atualização quando o número da versão muda. Mudanças
publicadas sem subir a versão não chegam a quem já instalou.

### Publicar uma versão nova (mantenedor)

1. Suba o campo `version` em `.claude-plugin/plugin.json` e em `.claude-plugin/marketplace.json`.
   Os dois precisam ter o mesmo valor.
2. Registre as mudanças no topo do [CHANGELOG.md](CHANGELOG.md).
3. Faça commit e push na `main` e crie a tag: `git tag v0.3.0 && git push origin v0.3.0`.
4. Avise a equipe para atualizar o plugin (comandos em [Instalação](#instalação), por ferramenta).

## Como usar

- Fluxo completo: "Inicia o fluxo do projeto X" + anexar a TAP.
- Etapa avulsa: chame a skill pelo nome (ex.: "faz o entendimento desta TAP").
- Retomar: "continua o fluxo do projeto X" — o orquestrador lê `fluxo/<projeto>/estado.md`.

## Arquivos gerados (por projeto, em `fluxo/<projeto>/`)

`estado.md` · `fontes/` · `01-contexto-projeto.md` · `01-benchmark.md` · `01-roteiro-reuniao.md` ·
`02-ata-reuniao.md` · `02-prontidao-prototipo.md` · `prototipo/` · `03-mapa-telas.md` ·
`03-capturas/` · `03-validacao-prototipo.md` · `design-system.md` · `04-requisitos.md` ·
`05-especificacao-<projeto>.docx`

## Requisitos do ambiente

- Pesquisa web habilitada (benchmark da etapa 1).
- Node.js e npm (protótipo); Playwright/Chromium para capturas.
- Conector do Figma (incluído no plugin, `https://mcp.figma.com/mcp`): autentique com a conta
  Figma da Plaenge na primeira vez. Usado na etapa 3 para enviar as telas do protótipo ao Figma.
  Recomendado: skills do Figma instaladas (`figma-generate-design` e `figma-use`).
- Python 3 com `python-docx` (comando `python`, `python3` ou `py`); LibreOffice para
  conferência em PDF (etapa 5).

## Modelo de documento

`skills/documentacao-especificacao/assets/modelo-especificacao-ads.docx`. Para trocar o modelo,
substitua o arquivo mantendo o título "Objetivo" como primeiro Título 1 do corpo e os controles
de conteúdo da capa (Projeto, Time de TI, Analista, Data de Publicação, Departamento,
Solicitante).
