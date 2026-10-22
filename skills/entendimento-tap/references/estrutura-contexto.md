# Estrutura do Contexto do Projeto

O Contexto do Projeto é o artefato vivo do fluxo. Nasce na etapa 1 (v0.x), é validado na
reunião (v1.0) e é a entrada de protótipo, requisitos e documentação.

As seções 2 a 9 espelham a ordem do **Documento de especificação ADS** (Objetivo, Escopo,
Justificativa, Cenário atual, Restrições, Premissas, Dependências de negócio, Dependências de
TI), para que a etapa 5 transporte o conteúdo sem reorganizar.

Seção sem informação nas fontes **não fica vazia nem some**: recebe uma linha
"**[pendente]** — ver LAC-00x" e a lacuna correspondente na seção 16.

```markdown
# Contexto do Projeto — <Projeto>

Projeto: <nome> | Artefato: Contexto do Projeto | Versão: 0.1 | Data: dd/mm/aaaa
Status: Rascunho
| Versão | Data | Autor | Alteração |

> Diagnóstico: <n> lacunas críticas. <A TAP é / não é suficiente para a reunião de entendimento porque ...>

## 1. Resumo executivo
3 a 5 linhas, sem jargão: o que é, para quem, resultado esperado.

## 2. Objetivo
Principal entrega do projeto, conforme a TAP/RAP. Comece pelo problema, não pela solução.

## 3. Escopo
### 3.1 Itens incluídos
### 3.2 Itens excluídos
Tão específicos quanto os incluídos. Se nenhuma fonte declarar exclusões → [pendente] + lacuna crítica.

## 4. Justificativa
Motivos e benefícios declarados; indicadores de sucesso, se houver (com meta e forma de medir).

## 5. Cenário atual
Como o processo é feito hoje (as-is): ferramentas, planilhas, e-mails, volume, dores citadas.
Separe fato do as-is de expectativa do to-be.

## 6. Restrições
Imposições externas: prazo, orçamento, regulatório, política de TI. Cada uma com origem.

## 7. Premissas
O que é assumido como verdadeiro para o projeto acontecer (ex.: regionais atendidas, idioma,
conectividade em obra). Premissa sem origem = [inferido] e pergunta.

## 8. Dependências de negócio
| Área de negócio | Responsabilidade | Parte interessada | Funcionalidade relacionada |

## 9. Dependências de TI
| Área de TI | Responsabilidade | Responsável | Funcionalidade relacionada |

## 10. Atores e perfis
| Perfil | Quem é na organização | O que faz no processo | Origem |
Perfil citado em outra seção e ausente aqui = lacuna.

## 11. Funcionalidades candidatas
Lista do que o sistema precisa permitir, no nível de capacidade (ex.: "consultar solicitações",
"cadastrar solicitação", "aprovar solicitação", "dashboard de acompanhamento"), cada uma com
origem. Não é requisito ainda; é o insumo que o protótipo transforma em telas.

| # | Funcionalidade | Atores | Origem | Situação |
Situação: citada na TAP | [inferido] | [pendente].

## 12. Regras de negócio conhecidas
Numeradas provisoriamente (R-01, R-02…) — viram RN- na etapa 4. Uma por linha, com origem,
condição e exceção; exceção desconhecida = [pendente].

## 13. Fluxos
Principal e alternativos em passos curtos com sujeito explícito. Ponto de decisão sem regra =
lacuna. Fluxo sem estado final = lacuna.

## 14. Integrações e sistemas envolvidos
| Sistema | Direção | O que troca | Interlocutor | Origem |
Interlocutor não nomeado = lacuna.

## 15. Benchmark de mercado
Resumo e tabela comparativa (detalhe em `01-benchmark.md` quando separado).

## 16. Lacunas e gaps
| LAC-ID | Tipo (lacuna/gap) | Descrição | Área | Criticidade | Por que importa | Pergunta(s) |

## 17. Inconsistências entre fontes
| # | Divergência | Fontes (FON-ID + local) | Impacto |

## 18. Documentos ausentes
| Documento esperado | Para que serve | Quem costuma ter |

## 19. Decisões registradas
| DEC-ID | Decisão | Responsável | Data | Origem |
Na etapa 1, só o que a TAP traz como decidido e aprovado.

## 20. Glossário
| Termo | Definição | Sinônimos |

## 21. Fontes
| FON-ID | Documento | Tipo | Versão/Data | Autor | Conteúdo | Status |
```
