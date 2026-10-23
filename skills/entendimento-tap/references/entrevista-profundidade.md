# Entrevista em profundidade

As perguntas Q- confirmam e decidem. A entrevista em profundidade descobre o que a TAP não
diz: o processo real, as exceções e a necessidade por trás do pedido. Ela usa perguntas
abertas (E-ID) e alimenta as Q- — não as substitui.

O que a entrevista revela é **fato do as-is, lacuna ou necessidade a confirmar**. Nunca é
requisito, regra decidida nem solução escolhida. Requisitos nascem na etapa 4.

## Técnicas

| Técnica | Quando usar | O que revela |
|---------|-------------|--------------|
| Critical Incident Technique | Sempre que a TAP cita problema, retrabalho ou exceção | Casos reais e recentes, em vez de opinião genérica |
| 5 Whys | Depois de um incidente ou dor relevante | A causa por trás do sintoma relatado |
| Contextual Inquiry / Think Aloud | Quando o entrevistado pode compartilhar a tela ou demonstrar a atividade | O processo real (as-is), atalhos, planilhas paralelas e workarounds |
| Contraste e casos extremos | Quando a TAP sugere regras, aprovações ou variações por tipo/valor | Regras de negócio implícitas e exceções |
| Laddering | Quando o pedido chega como solução pronta ("quero um botão…") | A necessidade por trás da solução pedida |

### Critical Incident Technique

- **Gatilho:** problema, retrabalho, atraso, reclamação ou exceção citados em qualquer fonte.
- **Pergunta de abertura:** "Me conte a última vez que <problema citado na TAP> aconteceu."
- **Aprofundamento:** "O que você estava fazendo? Quem mais participou? Como resolveu? Quanto
  tempo levou? Com que frequência isso acontece?"
- **Cuidado:** peça um caso específico e recente. "Normalmente…" é opinião; traga de volta para
  "e da última vez?".

### 5 Whys

- **Gatilho:** incidente ou dor relevante — em geral, encadeado logo após uma pergunta de
  Critical Incident.
- **Pergunta de abertura:** "Por que isso aconteceu?" e repita sobre cada resposta até chegar a
  uma causa que o projeto possa ou não tratar (não precisa ser exatamente 5).
- **Cuidado:** pare quando a causa sair do alcance do projeto e registre o limite. Causa
  encontrada é hipótese para confirmar, não diagnóstico fechado.

### Contextual Inquiry / Think Aloud

- **Gatilho:** atividade operacional que o entrevistado executa em sistema, planilha ou e-mail.
- **Pergunta de abertura:** "Pode compartilhar a tela e fazer <atividade> como faz no dia a
  dia, falando em voz alta o que está pensando?"
- **Aprofundamento:** "Por que você abriu essa planilha? Esse passo está em algum
  procedimento? O que acontece se pular?"
- **Cuidado:** observe, não ensine nem corrija. Atalho e planilha paralela são achados, não
  erros do usuário. Precisa de quem executa o processo, não do gestor.

### Contraste e casos extremos

- **Gatilho:** regra, aprovação, alçada, prazo ou variação por tipo, valor, região ou perfil.
- **Pergunta de abertura:** "Qual foi o maior caso que já passou por isso? E o menor? E o mais
  fora do comum?"
- **Aprofundamento:** "O que muda entre um <tipo A> e um <tipo B>? Já houve caso que não se
  encaixou em nenhum? Quem decidiu o que fazer?"
- **Cuidado:** a resposta revela regra **implícita**. Registre como R-xx **[inferido]** com Q-
  de confirmação para quem decide — exemplo contado não define regra.

### Laddering

- **Gatilho:** pedido formulado como solução: tela, botão, relatório, campo, integração ou
  ferramenta específica.
- **Pergunta de abertura:** "O que esse <botão/relatório> permitiria você fazer que hoje não
  consegue?"
- **Aprofundamento:** "E por que isso é importante? O que acontece hoje sem isso?" — suba até a
  necessidade ou o resultado de negócio.
- **Cuidado:** a solução pedida não entra como funcionalidade decidida. Registre a necessidade
  revelada e mantenha a solução como uma opção **[sugerido]** pelo entrevistado.

## Estrutura da entrevista

Uma entrevista por persona do `01-persona.md` (do MD de Persona ou gerada a partir da TAP),
sempre nesta ordem. Os gatilhos que o MD de Persona oferece — dores com exemplo, etapas da jornada com
planilha ou contorno, decisões relatadas — estão em `persona.md`.

| # | Bloco | Técnica | Conteúdo |
|---|-------|---------|----------|
| 1 | Abertura | — | Objetivo da conversa, duração, consentimento para gravar |
| 2 | Contexto e rotina do entrevistado | — | Papel, rotina, onde a atividade entra no dia a dia |
| 3 | Demonstração da atividade | Contextual Inquiry / Think Aloud | Se der para compartilhar a tela |
| 4 | Incidentes críticos + aprofundamento | Critical Incident + 5 Whys | Último caso real e a causa |
| 5 | Contrastes e casos extremos | Contraste | Maior, menor e mais fora do comum |
| 6 | Laddering | Laddering | Da solução pedida à necessidade |
| 7 | Fechamento | — | Resumo do entendimento para o entrevistado confirmar e materiais a enviar |

Cada bloco de 2 a 6 traz perguntas-guia (E-), sondas de follow-up e qual dúvida aberta
(LAC-) ou hipótese (H-) cobre. Bloco sem gatilho no material fica como "Não se aplica", com o
motivo. Formato em `roteiro-reuniao.md`.

## Hipóteses

Hipótese (H-ID) é uma suspeita que o material sugere e ninguém confirmou: "a conferência é
refeita porque os dados chegam por planilha". Ela não entra no contexto como fato; entra no
roteiro com a origem da suspeita, as E-/Q- que a testam e o que muda se for confirmada ou
derrubada. Na etapa 2, toda H- sai como confirmada, derrubada ou não testada.

## Como montar o bloco

1. Escreva o resumo do que já se sabe e liste as hipóteses H- antes das perguntas — elas
   orientam o que a entrevista precisa testar.
2. Varra o contexto e as fontes atrás dos gatilhos de cada técnica. Use só as técnicas que têm
   gatilho no material; técnica sem gatilho não entra.
3. Para cada gatilho, escreva uma E- com: técnica, gatilho (FON-ID e seção), pergunta-guia
   personalizada com os termos do glossário, sondas de follow-up, e as LAC-, Q- e H- que ela
   cobre. Coloque a E- no bloco da sua técnica, na entrevista do perfil certo.
4. Encadeie: Critical Incident → 5 Whys é a sequência natural; Contraste costuma preceder a Q-
   que confirma a regra.
5. Limite: de 6 a 10 E- por entrevista de 60 minutos. Uma demonstração cobre de 1 a 2
   atividades.

## Guardrails

- Pergunta neutra: sem propor solução, sem opções, sem insinuar a resposta.
- Nada de requisito: a entrevista não registra nem redige RN, RF, RNF, RT, DT, INT, ENT ou CT.
- Lacuna não se preenche com suposição: vira E-, Q- ou H-.
- O roteiro não conduz a entrevista: é apoio para o analista, que adapta ordem e sondas.

## Quando separar em duas sessões

Proponha duas sessões quando:

- houver Contextual Inquiry (exige quem executa o processo, tela compartilhada e tempo);
- houver mais de 10 E- ou a soma de E- e Q- passar de 25;
- quem executa o processo e quem decide forem pessoas diferentes.

Ordem: **sessão 1 — entrevista em profundidade** com quem executa o processo (uma entrevista
em 7 blocos por perfil); **sessão 2 — decisão** com patrocinador e quem decide, já com os
achados da sessão 1. Se só houver uma sessão, a entrevista vem antes das Q-.

## Erros comuns

- **Pergunta indutiva.** "Seria bom ter aprovação automática?" leva à resposta. Pergunte pelo
  caso real.
- **Pergunta aberta sem foco.** "Fale sobre o processo" gera transcrição longa e nada útil.
  Toda E- parte de um gatilho concreto.
- **Transformar achado em requisito.** "O usuário precisa de um filtro por obra" é necessidade
  a confirmar, não RF.
- **Entrevistar só o gestor.** Gestor descreve o processo ideal; quem executa mostra o real.
