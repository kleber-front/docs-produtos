# Roteiro da reunião de entendimento

O roteiro é o que transforma o contexto v0.x em v1.0. Reunião sem roteiro produz transcrição
longa e pouca decisão.

## Princípios

- **Pergunta respondível.** Cada Q- se responde em uma frase ou escolhendo entre opções. "Como
  funciona a aprovação?" é ruim; "Quem aprova solicitações acima de R$ 5.000: gestor do centro
  de custo, diretor da regional ou outro?" é boa.
- **Diga o que destrava.** Cada pergunta indica qual lacuna fecha e qual etapa depende dela.
- **Agrupe por tema e por destinatário.** O roteiro precisa permitir liberar quem já respondeu.
- **Criticidade primeiro.** Escopo, fora de escopo, perfis e regra central antes de detalhe de
  campo.
- **Inclua o benchmark.** Se houver solução de mercado com aderência relevante, a pergunta de
  decisão ("seguimos com desenvolvimento ou avaliamos X?") entra no bloco de abertura.
- **Limite.** Uma reunião de 60 minutos comporta de 15 a 25 perguntas. Mais que isso, proponha
  duas reuniões ou envie as menores por escrito antes.

## Formato

```markdown
# Roteiro — Reunião de entendimento — <Projeto>

Versão: 0.1 | Data: dd/mm/aaaa | Base: Contexto do Projeto v0.x
Duração sugerida: <min>
Participantes sugeridos:
| Papel | Por que precisa estar | Perguntas que responde |

## Pauta
1. Abertura e objetivo (5 min) — confirmar objetivo e resultado esperado
2. Escopo e fora de escopo (10 min)
3. Benchmark — decisão de caminho (5 min) [se aplicável]
4. Atores, perfis e permissões
5. Fluxo e regras de negócio
6. Dados, integrações e dependências
7. Restrições, prazo e transição
8. Encaminhamentos — o que fica para depois, quem responde, até quando

## Perguntas
| Q-ID | Tema | Pergunta | Opções (se houver) | Destinatário | Fecha | Criticidade | Bloqueia |
|------|------|----------|--------------------|--------------|-------|-------------|----------|
| Q-001 | Escopo | ... | a) ... b) ... | Patrocinador | LAC-003 | Crítica | Protótipo |

## Perguntas para envio prévio (por escrito)
Perguntas Menores ou de levantamento (volumetria, lista de regionais, exemplos de planilha).

## Materiais a pedir
Documentos ausentes que alguém da reunião provavelmente tem (planilha atual, fluxo, contrato).
```
