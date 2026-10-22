# Consolidação de fontes

## Sumário
- [Consolidar por tema, não por documento](#consolidar-por-tema-não-por-documento)
- [Decisão, discussão e intenção](#decisão-discussão-e-intenção)
- [Reconciliação de vocabulário](#reconciliação-de-vocabulário)
- [Quando as fontes divergem](#quando-as-fontes-divergem)
- [Hierarquia entre fontes](#hierarquia-entre-fontes)
- [O que fica de fora](#o-que-fica-de-fora)

---

## Consolidar por tema, não por documento

O erro que define uma consolidação malfeita: percorrer os documentos em ordem e resumir cada
um. O resultado repete informação, contradiz a si mesmo em parágrafos distantes e obriga o
leitor a fazer o cruzamento que era o trabalho.

Percorra os **temas** — objetivo, escopo, atores, regras, fluxos, integrações, restrições —
e para cada um reúna o que todas as fontes dizem. Um tema pode consumir informação de seis
documentos; um documento pode alimentar nove temas.

Teste: se o leitor consegue identificar qual parágrafo veio de qual documento, a
consolidação não aconteceu.

---

## Decisão, discussão e intenção

Três coisas diferentes que o material apresenta com a mesma aparência textual.

| Aparece como | É | Vai para |
|--------------|---|----------|
| "Ficou definido que os chamados acima de R$ 5.000 passam por aprovação" | Decisão | Regras de negócio |
| "Foi levantada a possibilidade de incluir aprovação por valor" | Discussão | Pontos em aberto |
| "Pretendemos incluir aprovação por valor na segunda fase" | Intenção | Fora de escopo, ou pontos em aberto |
| "O sistema atual já faz aprovação por valor" | Fato do as-is | Contexto, não regra do novo |

Sinais de decisão: verbo no passado com sujeito ("o comitê aprovou", "ficou definido"),
registro de responsável, data, ou presença em documento formal aprovado.

Sinais de discussão: condicional ("seria bom", "poderia"), voz passiva sem agente ("foi
sugerido"), ausência de encaminhamento.

Na dúvida, trate como discussão. Promover discussão a regra é o erro mais caro desta etapa,
porque o erro se propaga para os requisitos, o backlog e o código sem que ninguém revisite a
fonte.

---

## Reconciliação de vocabulário

Faça antes de escrever, não depois. Reescrever o texto inteiro para uniformizar termos
custa mais que decidir no início.

Processo:

1. Liste os conceitos que aparecem com mais de um nome nas fontes.
2. Escolha o termo oficial por este critério, em ordem: o que o negócio usa no dia a dia →
   o que aparece no documento mais formal → o mais específico.
3. Aplique em todo o texto, inclusive ao citar trechos — quando alterar o termo dentro de
   uma citação, indique.
4. Registre no glossário com os sinônimos: "Chamado (também: requisição, solicitação, RC)".
5. Se não houver como saber qual é o oficial, escolha um, registre a escolha como
   **[inferido]** e pergunte.

Caso especial: mesmo termo com significados diferentes. "Solicitação" como o registro
inteiro num documento e como a etapa inicial em outro. Aqui não basta escolher — é preciso
nomear os dois conceitos separadamente e sinalizar a ambiguidade como ponto em aberto,
porque o texto original vai continuar circulando.

---

## Quando as fontes divergem

Não escolha um lado por conta própria. Registre a divergência no corpo do entendimento, no
tema correspondente, e abra o ponto:

> A alçada de aprovação aparece como R$ 5.000 (documento de requisitos, item 5.4) e como
> R$ 10.000 (ata de 12/03). O valor está em aberto — ver seção 11.

Não faça isso em rodapé nem apenas na tabela de pontos em aberto. Quem lê o tema precisa ver
a divergência ali, senão vai usar o primeiro número que encontrar.

Divergência que se resolve sozinha pela leitura — uma fonte é claramente mais detalhada e
não contradiz a outra — não é divergência. Consolide no nível mais detalhado e siga.

---

## Hierarquia entre fontes

Quando precisar decidir a qual fonte dar peso na consolidação (não na resolução de conflito,
que exige pergunta), use como orientação:

1. Contrato ou documento assinado.
2. Documento formal aprovado, com versão e aprovador.
3. Documento formal em rascunho.
4. Ata com decisão registrada e responsável.
5. E-mail com decisão e data.
6. Ata sem encaminhamento, transcrição, anotação.

Duas ressalvas. Data importa dentro do mesmo nível, não entre níveis: e-mail recente não
supera contrato. E hierarquia não substitui pergunta quando a divergência muda escopo,
custo ou obrigação — ali a decisão é de quem responde pelo projeto.

---

## O que fica de fora

Não entra no entendimento, mesmo estando nas fontes:

- **Histórico de discussão** que não mudou a conclusão. Interessa o que ficou, não o
  caminho.
- **Opinião individual** sem decisão associada.
- **Detalhe de implementação** que apareceu numa reunião técnica. Vai para a etapa de
  arquitetura, não para o entendimento.
- **Conteúdo de outro projeto** que veio junto no documento reaproveitado. Se nada conecta o
  trecho a este projeto, marque e pergunte em vez de incorporar.
- **Números sem fonte** citados de memória em reunião ("acho que são uns 2 mil registros").
  Se forem relevantes, viram ponto em aberto, não fato.
