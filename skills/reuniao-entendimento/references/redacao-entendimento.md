# Redação do entendimento

## Sumário
- [Consolidado vs concatenado](#consolidado-vs-concatenado)
- [Hedge e incerteza](#hedge-e-incerteza)
- [Como escrever cada seção](#como-escrever-cada-seção)
- [Erros frequentes](#erros-frequentes)

---

## Consolidado vs concatenado

**Concatenado** (errado):

> O documento de requisitos descreve que o sistema permite abrir chamados. A ata de 12/03
> menciona que o gestor aprova chamados acima de determinado valor. O e-mail de 20/03
> informa que a aprovação é do gestor do centro de custo. O documento técnico cita que o
> chamado tem categoria.

Quatro frases, quatro fontes, nenhuma visão. O leitor precisa montar o quebra-cabeça.

**Consolidado** (certo):

> O solicitante abre um chamado informando categoria, descrição e centro de custo. Chamados
> acima de R$ 5.000 são direcionados para aprovação do gestor do centro de custo; abaixo
> disso, seguem direto para atendimento (doc. requisitos 3.1 e 5.4; ata 12/03; e-mail
> 20/03).

Uma visão, origens citadas ao final, sem costura visível.

---

## Hedge e incerteza

Escreva como quem documenta, não como quem opina.

- Ruim: "Pelo que entendi, parece que o sistema permitiria abrir chamados."
- Bom: "O sistema permite abrir chamados (doc. requisitos 3.1)."

O hedge espalhado pelo texto dilui a distinção entre fato e dúvida, que é exatamente o que
o leitor precisa enxergar. A incerteza tem lugar próprio: marcação explícita e seção de
pontos em aberto.

Três marcações, usadas com parcimônia:

| Marca | Quando | Exemplo |
|-------|--------|---------|
| **[inferido]** | Você deduziu de informação existente | "O chamado é encerrado pelo atendente **[inferido]** — nenhuma fonte diz quem encerra, mas o fluxo só fecha assim" |
| **[pendente]** | Não foi decidido | "Prazo de aprovação: **[pendente]**" |
| **[divergente]** | Fontes conflitam | "Alçada: R$ 5.000 (requisitos 5.4) ou R$ 10.000 (ata 12/03) **[divergente]**" |

Texto sem marca nenhuma é fato documentado com origem citada. Se não é fato e não tem
marca, não entra.

---

## Como escrever cada seção

**Resumo executivo** — 3 a 5 linhas, sem jargão, legível por quem nunca ouviu falar do
projeto. Se o resumo precisa de termo do glossário, reescreva.

**Objetivo e problema** — comece pelo problema, não pela solução. "Hoje as solicitações de
material circulam por e-mail, sem rastreabilidade de aprovação" diz mais que "o projeto
visa implementar um portal de chamados".

**Escopo e fora de escopo** — listas curtas, itens paralelos. Fora de escopo precisa ser tão
específico quanto o escopo: "não inclui integração com o ERP" é útil; "não inclui itens
futuros" não é.

**Atores e perfis** — tabela: perfil, quem é na organização, o que faz no sistema. Perfil
que aparece em outra seção e não está aqui é ponto em aberto.

**Regras de negócio** — numeradas, uma por linha, com origem. Regra com exceção não
definida leva **[pendente]** na própria linha, não só na tabela final.

**Fluxos** — passos curtos e numerados, sujeito explícito em cada. Ramificação como
subitem, não como parágrafo à parte.

**Integrações** — tabela: sistema, direção, tipo, criticidade. Uma linha de contexto por
integração, se necessário.

**Restrições** — separe por natureza (técnica, prazo, regulatória, orçamentária) e cite a
origem de cada uma. Restrição sem origem costuma ser preferência disfarçada.

**Decisões registradas** — decisão, responsável, data, documento. Sem responsável
identificável, a decisão vira ponto em aberto de governança.

**Pontos em aberto** — tabela com criticidade, destinatário e impacto. Impacto descreve o
que acontece se ninguém responder, não repete a pergunta.

---

## Erros frequentes

- **Resumir por documento.** O erro estrutural desta etapa. Consolide por tema.
- **Promover discussão a regra.** Ideia em ata sem decisão registrada vira ponto em aberto.
- **Alternar termos.** "Chamado", "requisição" e "solicitação" no mesmo texto fazem o leitor
  procurar uma diferença que não existe.
- **Escrever o fora de escopo como formalidade.** "Não estão previstas funcionalidades não
  descritas neste documento" é tautologia. Se não há exclusões declaradas nas fontes, isso é
  ponto em aberto crítico.
- **Esconder a divergência na tabela final.** Quem lê o tema precisa ver o conflito ali
  mesmo, senão usa o primeiro número que encontrar.
- **Incorporar detalhe técnico.** Decisão de implementação que apareceu numa reunião técnica
  pertence à etapa de arquitetura.
- **Marcar tudo como [inferido].** Marcação excessiva tem o mesmo efeito da ausência de
  marcação: o leitor para de distinguir. Se mais da metade do texto está marcado, o problema
  é falta de material, e isso deve estar dito na primeira linha.
