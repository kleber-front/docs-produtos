# Leitura por tipo de fonte

Cada tipo de documento mente de um jeito diferente. Não por má-fé — por natureza do
formato. Ata registra o que foi dito, não o que foi decidido; contrato registra o que foi
acordado, não o que é viável; protótipo mostra a tela, não a regra.

Saber o que cada formato omite por construção é o que separa uma leitura de uma análise.

## Sumário
- [Documento de requisitos / PRD](#documento-de-requisitos--prd)
- [Ata de reunião](#ata-de-reunião)
- [E-mail e mensagem](#e-mail-e-mensagem)
- [Contrato e proposta comercial](#contrato-e-proposta-comercial)
- [Planilha](#planilha)
- [Transcrição de reunião](#transcrição-de-reunião)
- [Protótipo, wireframe, print de tela](#protótipo-wireframe-print-de-tela)
- [Documentação de sistema existente](#documentação-de-sistema-existente)
- [Diagrama de processo](#diagrama-de-processo)
- [MD de Persona](#md-de-persona)

---

## Documento de requisitos / PRD
**Costuma trazer**: escopo, funcionalidades, atores, algumas regras.
**Costuma omitir**: fora de escopo, requisitos não funcionais, exceções das regras, o que
acontece com o processo atual.
**Verifique**: se há seção de fora de escopo (a ausência é lacuna, não descuido); se as
regras têm exceção; se há numeração com saltos; se a versão está identificada.

---

## Ata de reunião
**Costuma trazer**: o que foi discutido, posições, encaminhamentos.
**Costuma omitir**: quem decidiu, se a decisão foi formalizada, o que ficou sem conclusão.
**Verifique**: separe discussão de decisão. "Foi levantada a possibilidade de X" não é X
decidido. Itens assim entram no diagnóstico como pendência, nunca como fato documentado.
Anote também os participantes — é a melhor fonte para descobrir quem responde as perguntas.

---

## E-mail e mensagem
**Costuma trazer**: decisões pontuais, ajustes, aprovações informais.
**Costuma omitir**: contexto, o que veio antes, se a decisão foi revertida depois.
**Verifique**: a data é essencial — e-mail sem data no material é praticamente inútil para
resolver divergência. Cuidado com thread encaminhada: a decisão pode estar no trecho
inferior, contradita no superior.

---

## Contrato e proposta comercial
**Costuma trazer**: escopo contratado, entregas, marcos, critérios de aceite formais.
**Costuma omitir**: detalhe funcional suficiente para construir.
**Verifique**: o escopo contratual costuma ser mais restrito que o escopo discutido nas
reuniões. Divergência entre contrato e documento interno é achado importante e deve ser
registrada com destaque — mas a decisão sobre qual prevalece não é sua.

---

## Planilha
**Costuma trazer**: listas de requisitos, matrizes de permissão, volumetria, mapeamento de
campos.
**Costuma omitir**: contexto das colunas, significado de códigos e status, quem preencheu.
**Verifique**: abas escondidas, colunas fora da área visível, filtros aplicados que
escondem linhas, células com comentário. Planilha filtrada lida como completa é uma das
formas mais comuns de perder escopo. Verifique também se há aba de legenda — sem ela,
códigos viram lacuna.

---

## Transcrição de reunião
**Costuma trazer**: muito volume, contexto rico, discussões completas.
**Costuma omitir**: qualquer separação entre opinião, hipótese e decisão.
**Verifique**: trate tudo como discussão até que a própria transcrição registre uma
decisão explícita. Transcrição é a fonte que mais tenta o analista a promover comentário a
requisito. Quando um ponto parecer decidido, registre com a marca **[inferido]** e
pergunte.

---

## Protótipo, wireframe, print de tela
**Costuma trazer**: campos, fluxo de navegação, estados visíveis.
**Costuma omitir**: regras por trás dos campos, validações, permissões, estados de erro e
vazio, origem dos dados.
**Verifique**: cada campo do protótipo é uma pergunta em potencial — obrigatório?
validado como? preenchido de onde? Um protótipo detalhado dá falsa sensação de
documentação completa; ele documenta a interface, não o sistema. Verifique também se é
navegável ou estático, e se está versionado.

---

## Documentação de sistema existente
**Costuma trazer**: comportamento atual, modelo de dados, integrações.
**Costuma omitir**: o quanto está desatualizada.
**Verifique**: a data da última atualização contra a data da última mudança no sistema, se
essa informação existir. Documentação de sustentação frequentemente descreve uma versão
que já não roda. Quando houver dúvida, registre como "documentação de data incerta" em vez
de tratá-la como retrato do sistema atual.

---

## Diagrama de processo
**Costuma trazer**: sequência de atividades, responsáveis por raia, pontos de decisão.
**Costuma omitir**: as regras dos pontos de decisão, o que acontece nos caminhos de
exceção, volumetria.
**Verifique**: todo losango de decisão sem regra escrita é lacuna. Todo fluxo que termina
sem estado final é lacuna. Raia sem ator nomeado é lacuna. E confirme se o diagrama é
as-is ou to-be — diagramas raramente dizem, e a diferença muda tudo.

---

## MD de Persona
**Costuma trazer**: rotina, ferramentas, planilhas paralelas, dores e a jornada de quem executa
o processo, na voz dele.
**Costuma omitir**: exceções, volume real, o que outros papéis fazem, e por que as coisas são
feitas assim.
**Verifique**: se cada dor tem exemplo recente; se a jornada tem início, fim e tempo por etapa;
se os sistemas citados batem com os da TAP; se é relato de quem executa ou de quem gerencia.
Relato não é decisão: regra descrita pela persona vira R-xx **[inferido]** e pergunta. Leitura
e consolidação em `persona.md`.
