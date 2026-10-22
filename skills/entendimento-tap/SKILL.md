---
name: entendimento-tap
description: "Lê a TAP (Termo de Abertura do Projeto, também chamada RAP) e os documentos anexos de um projeto do Grupo Plaenge e gera o Contexto do Projeto — objetivo, escopo e fora de escopo, cenário atual, atores, regras, fluxos, integrações, restrições, premissas e dependências — mais um benchmark de soluções prontas no mercado, as lacunas e gaps classificados e o roteiro de perguntas para a reunião de entendimento. Use quando o usuário anexar uma TAP/RAP ou documentos de abertura e pedir \"entendimento da TAP\", \"analisa essa TAP\", \"prepara a reunião de entendimento\", \"monta o contexto do projeto\", \"existe solução pronta para isso\", \"faz o benchmark\", ou quando o orquestrador fluxo-produto chamar a etapa 1.\n"
metadata:
  version: "0.1.0"
---

# Entendimento da TAP

Transforme a TAP e seus anexos em três entregas: o **Contexto do Projeto** (a visão única que
alimenta todas as etapas seguintes), o **benchmark** de soluções de mercado e o **roteiro da
reunião de entendimento**.

Esta é a primeira etapa. Nada foi validado com o negócio ainda. O trabalho é entender o que a
documentação estabelece, expor o que ela não diz e chegar à reunião com as perguntas certas —
não com respostas presumidas.

Convenções comuns (marcas, IDs, bloco de status, modo subagente) em
`references/convencoes.md`. Leia antes de começar.

## Fluxo

1. **Confirme o material.** Sem TAP ou documento de abertura, peça e pare. Não monte contexto
   sobre material hipotético.
2. **Inventarie as fontes** com FON-ID: nome, tipo, versão/data, autor, uma linha do que cobre,
   status (OK, Incompleto, Ilegível, Vazio, Versão conflitante). Leia cada tipo de fonte
   conforme `references/leitura-fontes.md`.
3. **Leia tudo antes de escrever.** Consolide por **tema**, não por documento — regras em
   `references/consolidacao.md`.
4. **Reconcilie o vocabulário** e monte o glossário antes de redigir o contexto.
5. **Escreva o Contexto do Projeto** na estrutura de `references/estrutura-contexto.md`. Ela
   segue as seções do Documento de especificação ADS para que nada precise ser reorganizado na
   etapa 5.
6. **Cruze as fontes** em busca de divergências — padrões em `references/inconsistencias.md`.
   Divergência aparece no tema correspondente com **[divergente]**, não só na tabela final.
7. **Faça o benchmark** conforme `references/benchmark.md`. Pesquise na web; sem pesquisa real,
   não há benchmark.
8. **Identifique lacunas e gaps** (LAC-ID) varrendo as áreas de `references/pontos-abertos.md`
   e os documentos esperados de `references/documentos-esperados.md`. Classifique por
   criticidade.
9. **Formule as perguntas** (Q-ID), uma ou mais por lacuna crítica, com destinatário, e monte o
   roteiro da reunião conforme `references/roteiro-reuniao.md`.
10. **Entregue** e pare. As perguntas desta etapa são respondidas na reunião, não no chat —
    exceto as que bloqueiam a própria análise (objetivo do projeto ilegível, TAP de outro
    projeto, versão conflitante sem indicação de qual vale).

## Saídas

| Arquivo | Conteúdo |
|---------|----------|
| `01-contexto-projeto.md` | Contexto do Projeto v0.1 — estrutura completa, com marcas |
| `01-benchmark.md` | Benchmark — pode ir dentro do contexto (seção 15) se for curto; separe quando passar de 5 soluções |
| `01-roteiro-reuniao.md` | Pauta, participantes sugeridos, perguntas agrupadas por tema e por destinatário |

Abra o contexto com uma linha de diagnóstico: quantas lacunas críticas existem e se a TAP é
suficiente para a reunião. Se não for, diga na primeira linha.

## Lacuna vs gap

- **Lacuna** — informação que deveria existir e não está no material (ex.: ninguém disse quem
  aprova).
- **Gap** — distância entre o que o projeto pretende e o que o cenário atual ou a solução
  disponível entrega (ex.: o processo atual não tem controle de alçada que a TAP pressupõe; a
  solução de mercado X não integra com o ERP).

Registre ambos na tabela de lacunas com a coluna Tipo. Gap costuma virar pergunta de escopo;
lacuna, pergunta de detalhe.

## Quando perguntar ao usuário (antes da reunião)

Só quando a ambiguidade impedir a própria análise:

- a TAP não deixa claro o objetivo ou parece ser de outro projeto;
- há mais de uma versão da TAP sem indicação de qual vale;
- um anexo citado como essencial não veio;
- não há como saber o tipo de projeto (sistema novo, evolução, substituição, integração,
  automação, fornecedor) e isso muda o catálogo de documentos esperados.

Máximo de 5 perguntas, respondíveis em uma linha. Todo o resto vai para o roteiro da reunião.

## Escopo

**Fora do escopo:** extrair requisitos estruturados (RF, RNF), desenhar telas, propor
arquitetura, estimar esforço ou prazo, recomendar comprar ou construir. O benchmark apresenta
opções e critérios; a decisão é do patrocinador.

## Tom e estilo

- Escreva como quem documenta: "O processo de reembolso é feito por e-mail (FON-001, item 2)",
  não "parece que o processo seria".
- Cite a origem sempre: FON-ID e seção/página.
- Sem adjetivo de valor, sem elogio ao material, sem preâmbulo.
- Tabela para conteúdo com três dimensões ou mais.
- Pergunta boa é respondível em uma frase ou com opções, e diz o que destrava.

## Quando usar conhecimento próprio

Use para **detectar ausência** e **pesquisar mercado**, nunca para preencher o contexto.

- Certo: "A TAP prevê aprovação por valor, mas não diz o que acontece quando o aprovador está
  ausente. Processos assim costumam ter delegação — está previsto?" → vira Q-.
- Certo: apontar que sistema com alçada normalmente exige trilha de auditoria.
- Errado: escrever no contexto que existe delegação porque é o padrão de mercado.
- Errado: concluir que uma área não se aplica porque nenhuma fonte fala dela.

## Material de apoio

- `references/convencoes.md` — marcas, IDs, status, modo subagente.
- `references/estrutura-contexto.md` — seções do Contexto do Projeto.
- `references/benchmark.md` — como pesquisar e apresentar soluções de mercado.
- `references/roteiro-reuniao.md` — como montar a pauta e as perguntas.
- `references/leitura-fontes.md` — o que cada tipo de documento costuma omitir.
- `references/consolidacao.md` — fundir fontes, separar decisão de discussão, vocabulário.
- `references/inconsistencias.md` — padrões de divergência entre fontes.
- `references/pontos-abertos.md` — áreas a varrer e destinatário típico.
- `references/documentos-esperados.md` — documentos por tipo de projeto.
