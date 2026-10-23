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
| 1 | Entendimento da TAP | `agente-entendimento-tap` | `entendimento-tap` | `fontes/` + `01-contexto-projeto.md` (v0.x) + `01-benchmark.md` + `01-roteiro-reuniao.md` | Contexto completo, benchmark feito, perguntas Q- com destinatário |
| 2 | Reunião de entendimento | `agente-reuniao-entendimento` | `reuniao-entendimento` | `01-contexto-projeto.md` (v1.0) + `02-ata-reuniao.md` | Escopo e fora de escopo confirmados; checklist de prontidão para protótipo OK |
| 3 | Protótipo | `agente-prototipo` | `prototipo-navegavel` | `prototipo/` + `03-mapa-telas.md` + `design-system.md` | Toda tela ligada ao contexto; validação com negócio registrada |
| 4 | Requisitos | `agente-requisitos` | `requisitos-projeto` | `04-requisitos.md` | Todo RF OK com CT; todo RF não OK em pendência com destinatário |
| 5 | Documentação | `agente-documentacao` | `documentacao-especificacao` | `05-especificacao-<projeto>.docx` | Documento no modelo ADS, sem seção inventada, pendências visíveis |
| 6 | Backlog (opcional) | — | `estruturacao-backlog` (instalada na conta) | `06-backlog.md` | Todo requisito coberto |
| 7 | Pré-estimativa (opcional) | — | `preparacao-estimativa` (instalada na conta) | `07-pre-estimativa.md` | Itens no DoR ou bloqueio declarado |

Etapas 6 e 7 usam as skills já existentes na conta. Chame-as como subagente genérico pedindo
para carregar a skill pelo nome; se não estiverem instaladas, avise e encerre o fluxo na etapa 5.

## Abertura de um projeto

1. Pergunte (AskUserQuestion), só o que não estiver claro no pedido:
   - nome curto do projeto (vira pasta e prefixo de arquivos);
   - área solicitante e ponto focal de negócio;
   - tipo de projeto: sistema novo, evolução, substituição de legado, integração, automação,
     com fornecedor;
   - onde salvar: pasta conectada do computador, projeto do Claude, ou workspace da sessão.
2. Confirme que a TAP (ou RAP) e os demais documentos foram anexados. Sem documento, pare e
   peça — não rode a etapa 1 sobre material hipotético.
3. Crie a pasta `fluxo/<projeto>/` e o arquivo de estado `fluxo/<projeto>/estado.md`
   (modelo em `references/estado.md`). Passe a pasta à etapa 1: o `agente-entendimento-tap`
   cria `fontes/` com as cópias da TAP e dos anexos e grava ali os artefatos `01-*`. Das
   etapas seguintes em diante, documentos brutos são lidos de `fluxo/<projeto>/fontes/`.

## Ciclo de cada etapa

1. **Monte o pacote de entrada** conforme `references/pacotes-entrada.md`. Passe ao subagente
   caminhos de arquivo, não o conteúdo colado, exceto respostas do usuário.
2. **Chame o subagente** com a ferramenta Agent, usando o agente da tabela. O prompt sempre
   contém: "Modo subagente", o nome do projeto, a lista de arquivos de entrada, o caminho de
   saída esperado, a versão a gerar e — em reemissão — as respostas recebidas, uma por Q-ID.
3. **Leia o bloco de status** devolvido.
   - `aguardando-respostas` → vá para a rodada de perguntas.
   - `bloqueado` → mostre o motivo ao usuário e pare.
   - `concluido` / `concluido-com-ressalvas` → verifique o gate.
4. **Verifique o gate** lendo o artefato contra o critério da tabela (checklists em
   `references/gates.md`). Quem produziu não se auto-aprova: a verificação é sua.
5. **Apresente ao usuário**, com SendUserMessage: o que foi gerado (uma linha), o resultado do
   gate, as pendências críticas e a pergunta de avanço. Envie os arquivos com SendUserFile.
6. **Avance só com confirmação explícita.** Atualize `estado.md` (versão, gate, data).

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
- Pergunta cujo destinatário não é o usuário (negócio, TI, fornecedor) não vai para
  AskUserQuestion: liste-a e pergunte se o usuário quer seguir com suposição declarada ou
  aguardar a resposta.
- Na etapa 1, as perguntas **não** são respondidas agora: elas formam o roteiro da reunião.
  O gate da etapa 1 é ter as perguntas certas, não as respostas.
- Com as respostas, chame o mesmo agente de novo pedindo reemissão completa.

## Retornos entre etapas

Descoberta em etapa posterior volta à etapa dona da informação. Tabela em
`references/retornos.md`. Ao voltar:

1. Registre em `estado.md` a descoberta, a etapa de origem e a etapa dona.
2. Marque como `desatualizada` toda etapa posterior que consumiu o que mudou.
3. Rode a etapa dona em reemissão, depois as desatualizadas, na ordem.

Exemplo frequente: na validação do protótipo, o negócio cita uma regra nova → volta ao
contexto (etapa 2, como atualização pós-reunião) → protótipo da tela afetada → requisitos.

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
