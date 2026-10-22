# Estilo de redação

## Sumário
- [Regras com exemplo](#regras-com-exemplo)
- [Glossário](#glossário)
- [Adaptação ao leitor](#adaptação-ao-leitor)
- [Erros frequentes](#erros-frequentes)

---

## Regras com exemplo

**Escreva para quem não estava presente**
- Ruim: "Conforme alinhado na reunião, o fluxo de aprovação será mantido."
- Problema: quem lê daqui a seis meses não tem acesso à reunião nem sabe o que foi
  alinhado.
- Bom: "O fluxo de aprovação permanece em duas etapas: gestor da área e controladoria
  (decisão registrada na ata de 12/03)."

**Voz ativa, sujeito explícito**
- Ruim: "O CPF será validado antes da gravação."
- Problema: futuro descreve intenção, não comportamento; e some quem valida.
- Bom: "O sistema valida o CPF antes de gravar o cadastro."

**Sem adjetivo de valor**
- Ruim: "A solução oferece uma interface moderna e uma arquitetura robusta."
- Problema: nada disso é verificável e envelhece em um ano.
- Bom: corte a frase. Se houver conteúdo real por trás, ele já está nos RNFs.

**Um assunto por parágrafo**
- Ruim: parágrafo de dez linhas cobrindo cadastro, aprovação e notificação.
- Problema: documentação é consultada por trecho. Parágrafo denso não é encontrável.
- Bom: um parágrafo por assunto, com subtítulo quando houver mais de três.

**Tabela em vez de prosa enumerativa**
- Ruim: "O perfil Solicitante pode abrir e consultar chamados, enquanto o Gestor pode
  abrir, consultar, aprovar e cancelar, e o Administrador pode tudo isso além de..."
- Bom: matriz perfil × ação. Três dimensões ou mais, sempre tabela.

**Condição sempre com o caso contrário**
- Ruim: "Chamados acima de R$ 5.000 vão para aprovação."
- Bom: "Chamados acima de R$ 5.000 vão para aprovação do gestor. Abaixo desse valor,
  seguem direto para atendimento."

**Número com unidade e contexto**
- Ruim: "O prazo é de 2 dias."
- Bom: "2 dias úteis, contados do envio para aprovação, pelo calendário da unidade do
  solicitante."

---

## Glossário

Vai na seção 2, antes do conteúdo. Glossário no fim do documento só é encontrado por quem
já não precisava dele.

Inclua:
- Termo de domínio que não é evidente fora da área ("alçada", "centro de custo", "RC").
- Sigla, na primeira ocorrência e no glossário.
- Termo que a organização usa com significado próprio, diferente do uso comum.
- Sinônimos, apontando para o termo oficial: "Requisição → ver Chamado".

Não inclua termo genérico de TI que o leitor do documento domina. Glossário inflado é
ignorado inteiro, inclusive nas entradas que importavam.

Formato:

| Termo | Definição | Sinônimos |
|-------|-----------|-----------|
| Alçada | Valor máximo que um perfil pode aprovar sem escalonamento | Limite de aprovação |

Se a mesma coisa aparece com dois nomes nas fontes e não há como saber qual é o oficial,
escolha um, registre o outro como sinônimo e pergunte na rodada de dúvidas. Não alterne.

---

## Adaptação ao leitor

O mesmo fato muda de forma conforme o documento:

| Leitor | Profundidade | O que incluir | O que cortar |
|--------|--------------|---------------|--------------|
| Negócio / patrocinador | Alta abstração | Impacto, escopo, prazo, risco | Estrutura de dados, protocolo, ID técnico |
| Desenvolvimento | Máxima precisão | Requisito, regra, contrato de dados, exceção | Justificativa de negócio extensa |
| QA | Verificabilidade | Critério de aceite, caminho negativo, estado esperado | Racional de decisão |
| Infraestrutura | Operação | Ambiente, janela, volume, dependência | Regra de negócio |
| Suporte | Sintoma e ação | Mensagem, causa, procedimento, escalonamento | Requisito e rastreabilidade |
| Usuário final | Tarefa | Passo a passo, o que esperar, o que fazer no erro | Qualquer termo de sistema |
| Auditoria | Rastreabilidade | Origem, decisão, responsável, data, versão | Detalhe de implementação |

Quando um mesmo conteúdo precisa ir para dois leitores muito diferentes, são dois
documentos — não um documento com seções "para negócio" e "para técnicos". O leitor
descarta o documento inteiro quando a primeira seção não é dele.

---

## Erros frequentes

- **Seção preenchida para não ficar vazia.** Conteúdo plausível inserido para completar o
  índice atravessa a revisão sem ninguém questionar e vira compromisso por acidente. Seção
  sem fonte sai do índice ou fica `[pendente]`.
- **Documento que descreve a tela em vez do comportamento.** "A tela tem um botão Salvar
  no canto inferior direito" quebra na primeira mudança de layout. Documente o que o
  sistema faz, não onde o botão está — exceto no manual do usuário.
- **Referência circular.** Documento A remete ao B para a regra; B remete ao A. A regra não
  está em lugar nenhum. Defina um dono para cada conteúdo.
- **Histórico de alterações genérico.** "Ajustes gerais" não permite saber o que mudou
  entre versões, que é a única função da coluna.
- **Data ausente.** Documento sem data é impossível de ordenar contra as outras versões que
  circulam por e-mail.
- **Termo alternado.** "Chamado" em um parágrafo, "requisição" no seguinte, "solicitação"
  no terceiro. O leitor passa a procurar a diferença entre eles, e não existe.
