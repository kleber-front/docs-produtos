# Modelo do arquivo de estado

Arquivo `fluxo/<projeto>/estado.md`. Só o orquestrador escreve nele.

```markdown
# Estado do fluxo — <Projeto>

Tipo de projeto: <sistema novo | evolução | ...>
Área solicitante: <área> | Ponto focal: <nome>
Local dos arquivos: <pasta>
Iniciado em: dd/mm/aaaa | Última atualização: dd/mm/aaaa

## Etapas

| # | Etapa | Arquivo principal | Versão | Status | Gate | Críticas abertas | Atualizado |
|---|-------|-------------------|--------|--------|------|------------------|------------|
| 1 | Entendimento da TAP | 01-contexto-projeto.md | Rascunho | concluído | atendido | 4 | dd/mm |
| 2 | Reunião de entendimento | 02-ata-reuniao.md | — | não iniciada | — | — | — |
| 3 | Protótipo | 03-mapa-telas.md | — | não iniciada | — | — | — |
| 4 | Requisitos | 04-requisitos.md | — | não iniciada | — | — | — |
| 5 | Documentação | 05-especificacao-<projeto>.docx | — | não iniciada | — | — | — |

Status possíveis: não iniciada, em andamento, aguardando-respostas, concluída, desatualizada,
bloqueada.

O contexto não tem versão: na coluna Versão da linha dele vai o Status do contexto (Rascunho,
Em revisão, Validado).

## Suposições adotadas

| # | Etapa | Suposição | Impacto se errada | Autorizada por | Data |

## Retornos registrados

| Data | Descoberta | Etapa de origem | Etapa dona | Etapas invalidadas | Situação |

## Perguntas fora do usuário (aguardando terceiros)

| Q-ID | Pergunta | Destinatário | Desde | Bloqueia |
```
