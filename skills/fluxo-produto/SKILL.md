---
name: fluxo-produto
description: "Orquestra o fluxo de produto do Grupo Plaenge do início à especificação — Entendimento da TAP, Reunião de entendimento, Protótipo navegável, Requisitos (funcionais e técnicos) e Documento de especificação ADS — chamando um subagente por etapa, controlando gates, rodadas de perguntas, versões e retornos entre etapas. Use quando o usuário quiser \"iniciar um projeto novo\", \"rodar o fluxo\", \"começar pela TAP\", \"continuar o fluxo do projeto X\", \"em que etapa estamos\", \"próxima etapa\", ou anexar uma TAP/RAP pedindo o fluxo completo. Também use para retomar um projeto a partir do arquivo de estado.\n"
metadata:
  version: "0.1.0"
---

# Orquestrador do fluxo de produto

Conduza o projeto etapa por etapa. Não produza conteúdo de etapa: cada etapa é feita por um
subagente especializado. O papel aqui é preparar a entrada, chamar o agente certo, ler o bloco
de status, verificar o gate, levar as perguntas ao usuário e decidir — com ele — se avança.

Convenções comuns (marcas, IDs, bloco de status, modo subagente) em `references/convencoes.md`.
Leia antes de iniciar.

## Etapas

| # | Etapa | Agente | Skill | Saída principal | Gate |
|---|-------|--------|-------|-----------------|------|
| 1 | Entendimento da TAP | `agente-entendimento-tap` | `entendimento-tap` | `fontes/` + `01-contexto-projeto.md` (Rascunho) + `01-persona.md` (Rascunho) + `01-benchmark.md` + `01-roteiro-reuniao.md` | Contexto completo, personas geradas, benchmark feito, perguntas Q- com destinatário |
| 2 | Reunião de entendimento | `agente-reuniao-entendimento` | `reuniao-entendimento` | `01-contexto-projeto.md` (Validado) + `01-persona.md` (Validado) + `02-ata-reuniao.md` | Escopo e fora de escopo confirmados; checklist de prontidão para protótipo OK |
| 3 | Protótipo | `agente-prototipo` | `prototipo-navegavel` | `prototipo/` + `03-mapa-telas.md` + `design-system.md` | Toda tela ligada ao contexto; validação com negócio registrada |
| 4 | Requisitos | `agente-requisitos` | `requisitos-projeto` | `04-requisitos.md` | Todo RF OK com CT; todo RF não OK em pendência com destinatário |
| 5 | Documentação | `agente-documentacao` | `documentacao-especificacao` | `05-especificacao-<projeto>.docx` | Documento no modelo ADS, sem seção inventada, pendências visíveis |
| 6 | Backlog (opcional) | — | `estruturacao-backlog` (instalada no ambiente) | `06-backlog.md` | Todo requisito coberto |
| 7 | Pré-estimativa (opcional) | — | `preparacao-estimativa` (instalada no ambiente) | `07-pre-estimativa.md` | Itens no DoR ou bloqueio declarado |

O `01-contexto-projeto.md` e o `01-persona.md` são arquivos únicos e incrementais, sem versão:
cada etapa atualiza no lugar o que foi afetado e registra a alteração no próprio arquivo (ver
convenções). Os demais artefatos `.md` seguem versionados.

Etapas 6 e 7 usam skills instaladas à parte no ambiente. Chame-as como subagente genérico pedindo
para carregar a skill pelo nome; se não estiverem instaladas, avise e encerre o fluxo na etapa 5.

## Abertura de um projeto

1. Pergunte (ferramenta de perguntas da plataforma), só o que não estiver claro no pedido:
   - nome curto do projeto (vira pasta e prefixo de arquivos);
   - área solicitante e ponto focal de negócio;
   - tipo de projeto: sistema novo, evolução, substituição de legado, integração, automação,
     com fornecedor;
   - onde salvar: pasta do workspace aberto, outra pasta do computador ou área de trabalho da
     sessão.
2. Confirme que a TAP (ou RAP), o MD de Persona e os demais documentos foram anexados. Sem
   TAP, pare e peça — não rode a etapa 1 sobre material hipotético. Sem MD de Persona, avise
   em uma linha, indique o modelo `skills/entendimento-tap/assets/modelo-persona.md` e siga se
   o usuário não anexar: a etapa 1 registra a ausência como lacuna crítica.
3. Crie a pasta `fluxo/<projeto>/` e o arquivo de estado `fluxo/<projeto>/estado.md`
   (modelo em `references/estado.md`). Passe a pasta à etapa 1: o `agente-entendimento-tap`
   cria `fontes/` com as cópias da TAP, do MD de Persona e dos anexos e grava ali os artefatos
   `01-*`. Das etapas seguintes em diante, documentos brutos são lidos de
   `fluxo/<projeto>/fontes/`.

## Ciclo de cada etapa

1. **Monte o pacote de entrada** conforme `references/pacotes-entrada.md`. Passe ao subagente
   caminhos de arquivo, não o conteúdo colado, exceto respostas do usuário.
2. **Chame o subagente** com a ferramenta de subagentes da plataforma, usando o agente da
   tabela (sem suporte a subagentes, veja "Ferramentas da plataforma"). O prompt sempre
   contém: "Modo subagente", o nome do projeto, a lista de arquivos de entrada, o caminho de
   saída esperado, a versão a gerar (no contexto e nas personas: criar ou atualizar no
   lugar) e — em reemissão — as respostas recebidas, uma por Q-ID.
3. **Leia o bloco de status** devolvido.
   - `aguardando-respostas` → vá para a rodada de perguntas.
   - `bloqueado` → mostre o motivo ao usuário e pare.
   - `concluido` / `concluido-com-ressalvas` → verifique o gate.
4. **Verifique o gate** lendo o artefato contra o critério da tabela (checklists em
   `references/gates.md`). Quem produziu não se auto-aprova: a verificação é sua.
5. **Apresente ao usuário**: o que foi gerado (uma linha), o resultado do gate, as pendências
   críticas e a pergunta de avanço. Indique o caminho dos arquivos gerados (ou anexe-os, se a
   plataforma permitir).
6. **Avance só com confirmação explícita.** Atualize `estado.md` (versão — no contexto e nas
   personas, o Status —, gate, data).

## Envio ao Figma (etapa 3)

Depois que o `agente-prototipo` devolver o protótipo com build e capturas OK, e se o mapa de
telas trouxer "Envio ao Figma: pendente", faça o envio na sessão principal (onde o conector do
Figma está disponível): carregue a skill `prototipo-navegavel`, siga
`references/envio-figma.md` e registre o link do arquivo no `03-mapa-telas.md` e no
`estado.md`. Use o link de arquivo Figma do projeto se o usuário já tiver informado; senão crie
um novo. Sem o conector, avise o usuário em uma linha e siga — não bloqueia o gate.

## Rodada de perguntas

- Junte as perguntas do artefato, mantenha no máximo 7 por rodada, ordenadas por criticidade,
  agrupadas por tema, com destinatário.
- Pergunta cujo destinatário não é o usuário (negócio, TI, fornecedor) não vai para a
  ferramenta de perguntas: liste-a e pergunte se o usuário quer seguir com suposição declarada ou
  aguardar a resposta.
- Na etapa 1, as perguntas **não** são respondidas agora: elas formam o roteiro da reunião.
  O gate da etapa 1 é ter as perguntas certas, não as respostas.
- Com as respostas, chame o mesmo agente de novo pedindo reemissão completa — no contexto e
  nas personas, atualização no lugar do que foi afetado.

## Retornos entre etapas

Descoberta em etapa posterior volta à etapa dona da informação. Tabela em
`references/retornos.md`. Ao voltar:

1. Registre em `estado.md` a descoberta, a etapa de origem e a etapa dona.
2. Marque como `desatualizada` toda etapa posterior que consumiu o que mudou.
3. Rode a etapa dona em reemissão, depois as desatualizadas, na ordem.

Exemplo frequente: na validação do protótipo, o negócio cita uma regra nova → volta ao
contexto (etapa 2, como atualização pós-reunião) → protótipo da tela afetada → requisitos.

## Ferramentas da plataforma

O fluxo roda em qualquer assistente que leia skills (`SKILL.md`): GitHub Copilot (VS Code e
CLI), Claude Code, Codex, Cursor, Gemini CLI e outros. As instruções descrevem a ação, não o
nome da ferramenta; use a equivalente disponível:

| Ação | Exemplos |
|------|----------|
| Perguntar ao usuário | `AskUserQuestion` (Claude), `ask_user` / perguntas do chat (Copilot); sem ferramenta, pergunte em texto e pare o turno |
| Chamar subagente | `Agent`/`Task` (Claude), `runSubagent` / `task` (Copilot) |
| Carregar skill | ferramenta `Skill`/`skill`; sem ela, leia o `SKILL.md` da pasta da skill |
| Busca e leitura web | `WebSearch`/`WebFetch` (Claude), `web_fetch` / ferramentas web (Copilot) |

**Sem suporte a subagentes** (ou se o agente da etapa não estiver disponível): execute a etapa
na própria sessão. Leia o arquivo do agente (`agents/<agente>.agent.md` do plugin) e siga-o,
carregue a skill da etapa e trabalhe em "modo subagente" — sem perguntar ao usuário durante a
etapa e terminando com o bloco de status. Depois, retome o papel de orquestrador a partir do
passo 3 do ciclo.

## Retomada

Se `estado.md` existir, leia-o, diga em uma linha onde o projeto está e o que falta para o
próximo gate, e pergunte se continua dali. Não reexecute etapa com gate atendido sem motivo.

## Regras

- Não responda perguntas no lugar do negócio ou da TI.
- Não pule etapa nem gate. Se o usuário mandar pular, obedeça e registre em `estado.md`
  como **Suposição adotada**, com o impacto se estiver errada.
- Não feche pendência para deixar o fluxo limpo.
- Não reescreva artefato de etapa; peça reemissão ao agente.
- Mantenha cada mensagem ao usuário curta: o detalhe está nos arquivos.

## Material de apoio

- `references/convencoes.md` — marcas, IDs, bloco de status, modo subagente.
- `references/estado.md` — modelo do arquivo de estado.
- `references/pacotes-entrada.md` — o que cada agente recebe.
- `references/gates.md` — checklist de cada gate.
- `references/retornos.md` — descoberta → etapa dona.
