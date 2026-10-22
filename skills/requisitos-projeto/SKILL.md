---
name: requisitos-projeto
description: "Extrai os requisitos de um projeto do Grupo Plaenge a partir do Contexto do Projeto validado e do protótipo — regras de negócio (RN), requisitos funcionais (RF) organizados por tela e por bloco da tela, não funcionais (RNF), restrições (RT) e requisitos técnicos (arquitetura e stack, integrações e contratos de API, modelo de dados / dicionário de dados, infraestrutura e segurança), com IDs estáveis, origem, cenários de teste DADO QUE/QUANDO/ENTÃO e pendências. Use quando o usuário pedir \"extrai os requisitos\", \"levanta RF e RNF\", \"requisitos técnicos\", \"dicionário de dados\", \"contrato da API\", \"cenários de teste\", ou quando o orquestrador fluxo-produto chamar a etapa 4.\n"
metadata:
  version: "0.1.0"
---

# Requisitos do projeto (funcionais e técnicos)

Converta o contexto validado e o protótipo em requisitos que a equipe consiga implementar e
testar sem voltar à reunião — e que a etapa 5 transporte direto para o Documento de
especificação ADS.

Cada requisito é lido isoladamente, testado com sim ou não e tem origem localizável. Por isso a
saída é sempre em tabela, com IDs estáveis.

Convenções comuns em `references/convencoes.md`. Leia antes de começar.

## Entradas

- `01-contexto-projeto.md` v1.0 — obrigatório.
- `02-ata-reuniao.md` — obrigatório quando existir.
- `03-mapa-telas.md` e protótipo — obrigatórios para RF de interface; sem eles, RF de tela fica
  com status *Incompleto* e a ausência é pendência crítica.
- Documentos brutos (TAP, anexos) — consulta, para citar origem primária.
- Modelo ADS — consulta, para seguir a organização por funcionalidade.

## Fluxo

1. **Leia todas as entradas antes do primeiro requisito.** Extrair fonte por fonte gera
   duplicidade silenciosa.
2. **Converta as regras** (R-xx do contexto) em **RN-** com condição, exceção e origem. RN sem
   exceção declarada = *Incompleto*.
3. **Extraia os RF por funcionalidade/tela**, seguindo os blocos do mapa de telas (Cabeçalho,
   Barra de títulos, Filtros, Resultado, Grupos, Rodapé). Um RF por obrigação: campo com
   comportamento próprio, ação, validação, transição de status. Formato em
   `references/formato-saida.md`.
4. **Extraia os RNF** varrendo `references/catalogo-rnf.md`. Categoria aplicável sem menção =
   pendência, não seção vazia.
5. **Registre as restrições (RT)** — só imposições externas (política de TI, contrato, lei).
6. **Levante os requisitos técnicos** conforme `references/requisitos-tecnicos.md`:
   arquitetura e stack (DT-), integrações (INT-), modelo de dados (ENT-), infraestrutura e
   segurança. O que a TI impõe é RT; o que é proposta é DT **[sugerido]**.
7. **Escreva os cenários de teste (CT-)** dos RF com status OK, em DADO QUE / E / QUANDO /
   ENTÃO, cobrindo caminho principal, rejeição, permissão e estado resultante — regras em
   `references/criterios-aceite.md`.
8. **Monte a rastreabilidade** RN → RF → TL → CT e marque órfãos.
9. **Marque pendências** com criticidade e destinatário; formule as perguntas.
10. **Entregue** e pergunte antes de tratar pendências críticas como resolvidas. Reemita
    completo quando as respostas chegarem.

Redação: `references/redacao.md` — uma obrigação por requisito, voz ativa, sujeito explícito,
verificável, sem solução embutida no RF.

## Saída

`04-requisitos.md` com as seções (detalhe em `references/formato-saida.md`):

1. Resumo — contagem por tipo e status; lacunas críticas na primeira linha.
2. Regras de negócio (RN)
3. Requisitos de software por funcionalidade — para cada TL: regras aplicáveis, RF por bloco
4. Requisitos não funcionais (RNF)
5. Restrições (RT)
6. Requisitos técnicos — 6.1 Arquitetura e stack · 6.2 Integrações · 6.3 Modelo e dicionário de
   dados · 6.4 Infraestrutura e segurança
7. Cenários de teste (CT) por funcionalidade
8. Rastreabilidade
9. Pendências
10. Perguntas

## Quando perguntar

- RN com condição sem exceção, ou exceção sem tratamento.
- RNF sem métrica que não pode ser inferida com segurança.
- Campo do protótipo sem obrigatoriedade, tipo ou origem definidos.
- Integração sem contrato, sem interlocutor ou sem tratamento de falha.
- Decisão técnica que depende de política da TI não fornecida (hospedagem, autenticação,
  banco, padrão de API).
- Categoria de RNF obrigatória ausente: autenticação, autorização, auditoria, LGPD.

Máximo de 5 a 7 perguntas por rodada, agrupadas por tema, indicando qual ID destrava.

## Quando usar conhecimento próprio

Para **detectar ausência e propor como sugestão**, nunca para fechar requisito.

- Certo: "Não há RNF de auditoria. Com aprovação por status, o usual é registrar quem, quando,
  status anterior e novo. Aplica-se?" → pendência.
- Certo: propor DT-001 "SPA React + API REST + Azure AD" **[sugerido]**, citando o que no
  contexto motivou a proposta e que depende de aprovação da TI.
- Errado: gravar "≤ 3s" como RNF fechado porque é praxe.
- Errado: inventar campo no dicionário de dados que nenhuma tela ou integração usa.

## Escopo

**Fora do escopo:** backlog, user stories, estimativa, priorização, código, alteração de tela.
Lacuna de tela volta para o protótipo (etapa 3); lacuna de regra, para o contexto (etapa 2).

## Material de apoio

- `references/convencoes.md` — marcas, IDs, status, modo subagente.
- `references/formato-saida.md` — tabelas e organização por tela.
- `references/requisitos-tecnicos.md` — arquitetura, integrações, dados, infra e segurança.
- `references/redacao.md` — redação boa e ruim por tipo.
- `references/catalogo-rnf.md` — varredura de RNF com métricas típicas.
- `references/criterios-aceite.md` — critério verificável, caminho negativo, cobertura mínima.
