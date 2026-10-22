# Inconsistências entre fontes

Cruzar documentos é a parte do diagnóstico que mais retorno dá e a que mais se pula. Ler
cada fonte isoladamente produz um resumo; cruzá-las produz o diagnóstico.

## Sumário
- [Padrões de divergência](#padrões-de-divergência)
- [Como registrar](#como-registrar)
- [O que não é inconsistência](#o-que-não-é-inconsistência)
- [Sinais de documentação incompleta](#sinais-de-documentação-incompleta)

---

## Padrões de divergência

**Valor diferente para a mesma regra**
O caso mais simples e o mais perigoso, porque ambos os documentos parecem corretos
isoladamente. Alçada de R$ 5.000 no documento de requisitos e R$ 10.000 na ata. Registre os
dois valores com origem e data, e pergunte quem decide.

**Escopo que cresce entre versões sem registro**
A versão 2 tem uma funcionalidade que a versão 1 não tinha, e nenhum documento diz que ela
foi acrescentada. Pode ser decisão não registrada ou item colado por engano. Pergunte.

**Decisão revertida sem rastro**
A ata de março decide A; o documento de abril descreve B; nada explica a mudança. Registre
como decisão sem rastreabilidade — importa menos qual vale e mais que ninguém sabe por que
mudou.

**Termo com dois significados**
"Solicitação" significando o chamado inteiro em um documento e apenas a etapa inicial em
outro. Produz requisitos que parecem concordar e não concordam. Sempre registre, mesmo
quando o contexto deixa claro — o desenvolvimento não terá o contexto.

**Ator que aparece sem definição**
"O administrador aprova a exceção" num documento onde a lista de perfis tem apenas
solicitante e gestor. Ou falta um perfil, ou o requisito está errado. As duas hipóteses
viram pergunta.

**Fluxo que não fecha**
Existe transição para um estado, nenhuma transição saindo dele. Ou existe uma condição sem
o caso contrário. Registre como lacuna de fluxo, com o ponto exato onde ele interrompe.

**Integração citada em um lado apenas**
O documento do sistema A descreve o envio; nada no material do sistema B menciona o
recebimento. Pode ser documentação incompleta ou premissa não validada com o outro time.

**Prazo incompatível com escopo declarado**
Não é sua função estimar, mas quando o documento declara prazo e escopo e a combinação é
visivelmente tensa, registre como ponto a validar — sem dizer que é inviável, porque isso
seria estimativa.

---

## Como registrar

Uma linha por divergência, com os quatro elementos:

| # | Divergência | Documentos envolvidos | Impacto |
|---|-------------|----------------------|---------|
| 1 | Alçada de aprovação: R$ 5.000 (requisitos 5.4) vs R$ 10.000 (ata 12/03) | Doc. requisitos v2; Ata 12/03 | Muda a regra de roteamento e o volume que passa por aprovação |

Regras:

- **Cite ambos os lados com localização.** "Os documentos divergem sobre a alçada" não
  permite a ninguém verificar.
- **Descreva o impacto, não a divergência de novo.** Impacto é o que faz alguém priorizar a
  resolução.
- **Não escolha um lado.** Nem por data, nem por hierarquia do documento, nem por
  plausibilidade. Registre e pergunte.
- **Uma divergência que aparece em três documentos é uma linha**, com os três citados — não
  três linhas.

---

## O que não é inconsistência

Evite inflar a seção com achados que não são divergência real:

- **Nível de detalhe diferente.** Documento executivo diz "o sistema controla chamados"; o
  técnico detalha as regras. Complementaridade, não contradição.
- **Sinônimo declarado.** Se um documento estabelece que "chamado" e "requisição" são a
  mesma coisa, o uso alternado é ruído de redação, não inconsistência. Registre uma vez em
  lacunas de glossário.
- **Informação presente em um e ausente em outro.** Isso é lacuna, não inconsistência, e vai
  na outra seção.
- **Ordem diferente de apresentação.** Sem significado.

Seção de inconsistências inflada perde credibilidade e faz o leitor ignorar as duas ou três
que realmente importam.

---

## Sinais de documentação incompleta

Indícios de que existe material não enviado. Todos viram pergunta:

- Sumário citando seções que não estão no arquivo.
- Numeração de seções ou de requisitos com saltos (RF-001, RF-002, RF-007).
- "Versão parcial", "rascunho", "para discussão" no cabeçalho.
- Referência a anexo, apêndice, diagrama ou planilha não fornecidos.
- Comentário ou marcação de revisão pendente no corpo do texto.
- Data de última alteração muito anterior à do projeto em curso.
- Cabeçalho com campo de aprovação em branco.
- Menção a decisão tomada "em reunião" sem ata correspondente no material.

Registre cada um citando onde aparece. É a forma mais rápida de recuperar documentação que
existe e não foi enviada — o que resolve mais lacunas que qualquer outra pergunta.
