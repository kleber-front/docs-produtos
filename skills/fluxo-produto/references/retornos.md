# Retornos entre etapas

| Descoberta | Costuma aparecer em | Etapa dona | Etapas invalidadas |
|------------|---------------------|------------|--------------------|
| Documento novo, versão nova da TAP | 2, 3, 4 | 1 (reemissão) | 2 em diante, se mudar escopo |
| Mudança de escopo, ator, perfil ou fluxo | 3, 4 | 2 (atualização pós-reunião do contexto) | 3, 4, 5 |
| Regra de negócio nova ou alterada | 3 (validação), 4, 5 | 2 (contexto) → 4 (RN) | 3 (telas afetadas), 4, 5 |
| Campo, estado ou ação de tela não definidos | 4, 5 | 3 (protótipo) | 4 (RFs da tela), 5 |
| Requisito técnico imposto pela TI (ex.: Azure AD, hospedagem) | 4, 5 | 4 | 5 |
| Inconsistência de ID ou valor entre artefatos | 5 | 4 | 5 |
| Solução de mercado considerada viável depois do benchmark | 2, 3 | 1 (benchmark) + decisão do patrocinador | todas, se o projeto mudar de "construir" para "adquirir" |

Retorno não é falha do fluxo: é o fluxo funcionando. O que não pode acontecer é a etapa
posterior "corrigir" a informação localmente — aí os artefatos passam a se contradizer.
