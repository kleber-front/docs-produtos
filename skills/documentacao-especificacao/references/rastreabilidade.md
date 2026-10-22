# Rastreabilidade e versionamento

## IDs

Preserve os identificadores dos artefatos anteriores em todos os documentos. Renumerar ao
documentar quebra a ligação com backlog, casos de teste, contrato e histórico de
alterações — e o rompimento só aparece meses depois, quando alguém procura o RF-014 do
contrato e encontra outro requisito no documento.

Convenção, se ainda não houver uma:

| Prefixo | Tipo |
|---------|------|
| RF | Requisito funcional |
| RNF | Requisito não funcional |
| RN | Regra de negócio |
| RT | Restrição |
| CA | Critério de aceite |
| INT | Integração |

Sequencial por tipo, três dígitos, sem reaproveitamento. Item removido recebe status
*Cancelado* e permanece na tabela — o número não volta a ser usado.

Agrupar por módulo no documento não autoriza renumerar. Use uma coluna "Módulo" em vez de
prefixos por área; prefixo por área só sobrevive se a estrutura de áreas nunca mudar, o
que não acontece.

## Matriz de rastreabilidade

Formato:

| Origem | RN | RF | CA | Caso de teste | Status |
|--------|----|----|----|---------------|--------|
| Doc. requisitos 5.4 | RN-001 | RF-007 | CA-007.1, CA-007.2 | CT-012 | Implementado |
| Ata 12/03 | — | RF-009 | CA-009.1 | — | Especificado |
| — | RN-004 | — | — | — | Órfã |

Célula vazia é informação, não lacuna de preenchimento. Cada padrão significa algo:

- **RF sem origem** — requisito que ninguém pediu. Ou falta a fonte, ou o requisito não
  deveria existir. Vira pergunta.
- **RN sem RF** — regra que nenhum requisito aplica. Ou falta requisito, ou a regra é de
  outro contexto.
- **RF sem CA** — requisito que não se sabe como validar. Bloqueia a homologação.
- **CA sem caso de teste** — esperado antes da fase de testes; vira pendência depois dela.
- **Origem sem RF** — item do documento de origem que não virou requisito. Pode ser
  escopo esquecido ou exclusão deliberada não registrada. Sempre vira pergunta.

Gere a matriz a partir dos artefatos, nunca preenchendo por dedução. Se você não consegue
citar onde a ligação está escrita, a célula fica vazia.

## Versionamento

**Numeração**: inteiro para versão aprovada (1, 2, 3); decimal para revisão em rascunho
(1.1, 1.2). Versão 1 é a primeira aprovada, não o primeiro rascunho — rascunhos anteriores
são 0.1, 0.2.

**Status**: Rascunho → Em revisão → Aprovado. Documento Aprovado alterado volta para
Rascunho na versão seguinte; não existe alteração silenciosa em documento aprovado.

**Histórico de alterações**: uma linha por versão emitida, com o que mudou em termos
úteis. "Ajustes gerais" não informa nada. "Incluídos RF-021 a RF-024 (módulo de anexos);
RN-003 corrigida quanto ao arredondamento" informa.

| Versão | Data | Autor | Alteração |
|--------|------|-------|-----------|
| 0.1 | 03/02/2026 | Kleber | Versão inicial |
| 1 | 11/02/2026 | Kleber | Aprovada em comitê; sem alteração de conteúdo |
| 1.1 | 20/03/2026 | Kleber | Incluídos RF-021 a RF-024 (anexos) |

**Reemissão completa**: ao receber correções, gere o documento inteiro atualizado. Adendo
solto e errata divergem da versão principal em duas rodadas, e a partir daí ninguém sabe
qual vale.

## Consistência entre documentos

Antes de fechar um conjunto, verifique:

1. O mesmo termo é usado para o mesmo conceito em todos os documentos.
2. O mesmo ID aponta para o mesmo item em todos os documentos.
3. Nenhuma regra aparece com valores diferentes em dois lugares.
4. O escopo declarado na Visão não contradiz os requisitos da Especificação.
5. As pendências listadas são as mesmas, ou têm razão declarada para diferir.
6. As datas e versões citadas na seção Referências existem e conferem.

Divergência encontrada aqui não se resolve escolhendo a versão mais recente: registre nos
dois documentos, marque o conflito e pergunte quem decide.
