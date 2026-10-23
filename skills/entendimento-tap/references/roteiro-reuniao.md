# Roteiro da reunião de entendimento

O roteiro é o que leva o contexto de Rascunho a Validado. Reunião sem roteiro produz transcrição
longa e pouca decisão.

O roteiro tem duas partes: a **entrevista em profundidade** (E-, perguntas abertas e neutras,
em 7 blocos por perfil de entrevistado, que descobrem o processo real, as exceções e a
necessidade) e as **perguntas de confirmação e decisão** (Q-, fechadas). Técnicas, blocos e
montagem das E- em `entrevista-profundidade.md`.

## Princípios

- **Pergunta respondível.** Vale para as Q-; as E- são abertas por definição. Cada Q- se
  responde em uma frase ou escolhendo entre opções. "Como funciona a aprovação?" é ruim; "Quem
  aprova solicitações acima de R$ 5.000: gestor do centro de custo, diretor da regional ou
  outro?" é boa.
- **E- neutra.** A entrevista não propõe solução nem traz opções: pergunta pelo caso real, pela
  atividade e pela necessidade. Opções ficam só nas Q- de decisão.
- **Diga o que destrava.** Cada pergunta indica qual lacuna ou hipótese cobre e qual etapa
  depende dela.
- **Agrupe por tema e por destinatário.** O roteiro precisa permitir liberar quem já respondeu.
- **Criticidade primeiro.** Escopo, fora de escopo, perfis e regra central antes de detalhe de
  campo.
- **Inclua o benchmark** (de `01-benchmark.md`). Se houver solução de mercado com aderência
  relevante, a pergunta de decisão ("seguimos com desenvolvimento ou avaliamos X?") entra na
  abertura da sessão de decisão — nunca na entrevista.
- **Limite.** Uma reunião de 60 minutos comporta de 15 a 25 perguntas, somando E- e Q-. Mais que
  isso, proponha duas sessões (critérios em `entrevista-profundidade.md`) ou envie as menores
  por escrito antes.
- **Entrevista antes da decisão.** As E- vêm antes das Q- que confirmam o que elas revelaram.

## Guardrails

- **Não registra nem redige requisitos.** Nem E- nem Q- pedem para definir RN, RF, RNF, RT, DT,
  INT, ENT, CT, tela ou campo. O roteiro descobre e decide entendimento; requisitos são da
  etapa 4.
- **Não propõe solução.** As perguntas da entrevista são neutras.
- **Não completa lacunas com suposições.** O que falta na TAP vira pergunta ou hipótese H-
  explícita, nunca resposta presumida no resumo.
- **Não conduz a entrevista.** O roteiro é apoio para o analista; quem entrevista adapta a ordem
  e as sondas ao que ouvir.

## Formato

```markdown
# Roteiro — Reunião de entendimento — <Projeto>

Versão: 0.1 | Data: dd/mm/aaaa | Base: Contexto do Projeto atualizado em dd/mm/aaaa
Formato: sessão única | duas sessões (1 — entrevista em profundidade; 2 — decisão)
Duração sugerida: <min por sessão>
Participantes sugeridos:
| Sessão | Papel | Por que precisa estar | Perguntas que responde (E-/Q-) |

## O que já se sabe
Resumo de 5 a 10 linhas, consolidado da TAP, dos documentos e de entrevistas anteriores, com
FON-ID. Só fato documentado; o que não está documentado vai para hipóteses ou dúvidas.

## Hipóteses a confirmar ou derrubar
| H-ID | Hipótese | Origem (por que suspeitamos) | Como testar (E-/Q-) | Se confirmada | Se derrubada |
|------|----------|------------------------------|---------------------|---------------|--------------|
| H-001 | A conferência é refeita porque os dados chegam por planilha | FON-002, aba 3 [inferido] | E-004, E-005 | Reforça LAC-004 | Nova E- de incidente |

## Entrevista em profundidade — <persona>
<Repita esta seção para cada persona do `01-persona.md`: quem executa, gestor, área
parceira...>
Entrevistado: <papel> | Sessão: <1 ou única> | Duração: <min>

### 1. Abertura
Objetivo da conversa, duração e consentimento para gravar. Sem perguntas sobre o projeto.

### 2. Contexto e rotina do entrevistado
### 3. Demonstração da atividade (se der para compartilhar a tela)
### 4. Incidentes críticos + aprofundamento (5 Whys)
### 5. Contrastes e casos extremos
### 6. Laddering — da solução pedida à necessidade
<Em cada bloco de 2 a 6:>
| E-ID | Técnica | Pergunta-guia | Sondas de follow-up | Gatilho (origem) | Cobre (LAC-/Q-/H-) |
|------|---------|---------------|---------------------|------------------|--------------------|
| E-004 | Critical Incident | Me conte a última vez que uma conferência precisou ser refeita. | O que aconteceu? Quem participou? Quanto tempo levou? | FON-001, item 3 | LAC-004, H-001 |
| E-005 | 5 Whys | Por que precisou ser refeita? | Repetir sobre cada resposta até a causa | Encadeada na E-004 | LAC-004, H-001 |
Bloco sem gatilho no material: "Não se aplica — <motivo em uma linha>".

### 7. Fechamento
Resumo do entendimento para o entrevistado confirmar e materiais a enviar depois, com prazo.

## Perguntas de confirmação e decisão
| Q-ID | Tema | Pergunta | Opções (se houver) | Destinatário | Fecha | Criticidade | Bloqueia |
|------|------|----------|--------------------|--------------|-------|-------------|----------|
| Q-001 | Escopo | ... | a) ... b) ... | Patrocinador | LAC-003 | Crítica | Protótipo |

## Pauta da sessão de decisão
1. Abertura e objetivo (5 min) — confirmar objetivo e resultado esperado
2. Achados da entrevista e hipóteses (5 min) [se houve sessão 1]
3. Escopo e fora de escopo (10 min)
4. Benchmark — decisão de caminho (5 min) [se aplicável]
5. Atores, perfis e permissões
6. Fluxo e regras de negócio
7. Dados, integrações e dependências
8. Restrições, prazo e transição
9. Encaminhamentos — o que fica para depois, quem responde, até quando
Em sessão única, a entrevista vem antes do item 3.

## Ligação entre dúvidas e perguntas
| Dúvida (LAC-/H-) | Criticidade | Perguntas que respondem (E-/Q-) | Entrevistado/destinatário |
Toda LAC- crítica e toda H- aparecem aqui com ao menos uma pergunta.

## Perguntas para envio prévio (por escrito)
Perguntas Menores ou de levantamento (volumetria, lista de regionais, exemplos de planilha).

## Materiais a pedir
| Material | Quem tem | Quando (antes / durante) | Para que serve (LAC-/H-) |
Telas, planilhas, exemplos reais, documentos ausentes. Sem MD de Persona, ele entra aqui,
no modelo `assets/modelo-persona.md`, para antes da reunião.
```
