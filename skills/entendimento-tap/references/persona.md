# MD de Persona

O MD de Persona é o relato de quem executa, aprova ou acompanha o processo: a síntese do perfil
em 10 itens e o fluxo de trabalho (mapa de jornada) de hoje. Ele chega junto com a TAP, no
modelo `assets/modelo-persona.md`. A TAP diz o que o projeto pretende; a persona diz como o
trabalho acontece. O cruzamento das duas é o que torna a entrevista objetiva.

## Sumário
- [Natureza da fonte](#natureza-da-fonte)
- [Item → seção do contexto](#item--seção-do-contexto)
- [Cruzamento com a TAP](#cruzamento-com-a-tap)
- [Completude](#completude)
- [Gatilhos para a entrevista](#gatilhos-para-a-entrevista)
- [Sem MD de Persona](#sem-md-de-persona)

---

## Natureza da fonte

- **É relato, não decisão.** O que a persona escreve é fato do as-is declarado por ela: entra
  no contexto com FON-ID e item ("FON-002, item 4"), nunca como regra decidida, decisão ou
  requisito.
- **Peso na consolidação:** mesmo nível de anotação ou entrevista (nível 6 da hierarquia em
  `consolidacao.md`). Diante de documento formal, a persona não prevalece — a divergência é
  registrada e perguntada.
- **Papel, não pessoa.** O contexto descreve a persona pelo papel ("Engenheiro de obra"). O
  nome de quem preencheu fica só no inventário de fontes.
- **Um ou vários arquivos.** Aceite um arquivo por persona ou várias no mesmo arquivo (um
  `# Persona — <papel>` para cada). Cada arquivo é uma FON; cada persona, uma subseção em
  10.2.
- **Fora do modelo.** MD de Persona em outro formato é lido do mesmo jeito: localize cada um
  dos 10 itens e a jornada; o que não for encontrado é tratado como item em branco.

---

## Item → seção do contexto

Consolide por tema: o item alimenta a seção indicada junto com o que as outras fontes dizem.
A síntese completa de cada persona fica em 10.2, com origem por item.

| Item do MD | Vai para | Como |
|------------|----------|------|
| 1. Função e setor | §10.1, §10.2 | Perfil que a persona representa; papel sem perfil na TAP = lacuna |
| 2. Objetivo principal da função | §10.2 | Contrastar com o objetivo do projeto (§2) |
| 3. Atividades recorrentes e tempo | §5 | Rotina, frequência e tempo como fato do as-is; volume citado sem fonte vira pergunta |
| 4. Sistemas e ferramentas | §5, §14 | Planilha, e-mail e sistema em uso; sistema sem interlocutor = lacuna |
| 5. Informações e de onde vêm | §14 | Origem de cada dado: digitado, planilha, outro sistema, outra área |
| 6. Decisões e aprovações | §12, §10.1 | Regra relatada = R-xx **[inferido]** + Q- para quem decide; aprovador sem perfil = lacuna |
| 7. Principais dores e exemplo | §5 | Dor citada, com o exemplo; gatilho de entrevista |
| 8. Áreas e papéis com que interage | §8, §10.1 | Área parceira = dependência de negócio a confirmar; papel citado sem perfil = lacuna |
| 9. Onde trabalha | §7 | O que o projeto pressupõe (uso em obra, no celular, sem rede) = premissa **[inferido]** + pergunta |
| 10. Familiaridade com tecnologia | §7, §10.2 | Premissa de uso e de treinamento **[inferido]** + pergunta |
| Fluxo de trabalho / jornada | §10.2, §5 | Tabela da jornada em 10.2; resumo do as-is em §5. Não é o fluxo do projeto (§13) |

---

## Cruzamento com a TAP

O que a persona relata e a TAP não cobre é achado — registre em §16 (gap ou lacuna) ou §17
(divergência), com os dois lados citados:

| Achado | Tipo | Exemplo |
|--------|------|---------|
| Sistema usado pela persona e ausente da TAP | Lacuna | Persona controla medições em planilha paralela; a TAP só cita o ERP |
| Dor relatada que o objetivo da TAP não trata | Gap | A dor central é retrabalho na conferência; a TAP trata só da aprovação |
| Aprovação ou decisão relatada que a TAP não prevê | Lacuna | Persona aprova exceções por e-mail; a TAP não tem alçada |
| Persona e TAP descrevem o mesmo passo de formas diferentes | Divergência | TAP: "o gestor lança"; persona: "eu lanço e o gestor confere" |
| Papel do item 8 sem perfil em §10.1 | Lacuna | "Passo para o suprimentos" sem perfil de suprimentos |
| Perfil da TAP sem persona | Lacuna | Relevante; Crítica quando for quem executa o fluxo principal |

Não escolha lado: o relato não corrige a TAP nem a TAP desmente o relato. As duas versões ficam
visíveis até a reunião.

---

## Completude

| Situação no MD | Registro |
|----------------|----------|
| Item em branco ou "não sei" | `[pendente]` em 10.2 + LAC |
| Resposta genérica ("vários sistemas", "normalmente", "depende") | LAC + E- que pede o caso concreto |
| Dor sem exemplo recente | E- de Critical Incident na entrevista da persona |
| Etapa da jornada sem tempo, sistema ou responsável | `[pendente]` na célula + LAC, se a etapa entra no escopo |
| Jornada sem início ou fim claros | LAC de fluxo, com o ponto onde interrompe |

Criticidade pelo impacto na próxima etapa, conforme as convenções: item que define quem usa o
sistema ou o que ele substitui tende a Crítica; detalhe de rotina, a Relevante ou Menor.

---

## Gatilhos para a entrevista

Cada persona vira uma entrevista em 7 blocos (`entrevista-profundidade.md`), com o papel da
persona como entrevistado.

| No MD | Gatilho de | E- |
|-------|-----------|----|
| Item 7 — dor com exemplo | Critical Incident + 5 Whys | "Me conte de novo o caso de <exemplo do item 7>…" e a causa |
| Etapa da jornada com planilha, e-mail ou contorno manual | Contextual Inquiry | Demonstração da etapa, com tela compartilhada |
| Item 6 — decisão ou aprovação | Contraste e casos extremos | Maior, menor e mais fora do comum caso decidido |
| Pedido de solução escrito no MD | Laddering | Da solução pedida à necessidade; solução fica **[sugerido]** |

No bloco 2 (contexto e rotina), o analista lê a síntese para a persona confirmar e aprofunda só
o que ficou vago ou em branco. Não repita na entrevista o que o MD já respondeu.

---

## Sem MD de Persona

A etapa segue; a ausência é registrada assim:

- **LAC crítica** "Persona e jornada de trabalho ausentes" — área Atores; destinatário: ponto
  focal da área solicitante. Por que importa: sem ela, perfis, cenário atual e entrevista
  partem só da TAP.
- **Q-** respondível ligada à LAC: "Quem executa o processo hoje e quem preenche o modelo de
  Persona até <data da reunião>?" — destinatário: ponto focal.
- **§10.2** com `[pendente] — ver LAC-00x`.
- **§18 Documentos ausentes:** "MD de Persona (síntese do perfil e jornada) — mostra rotina,
  ferramentas e dores de quem executa o processo — área solicitante".
- **Materiais a pedir** do roteiro: MD de Persona no modelo `assets/modelo-persona.md`, antes da
  reunião.
- **Roteiro:** uma entrevista por perfil da TAP. O bloco 2 cobre os 10 itens como E- neutras e
  o bloco 3 levanta a jornada, com demonstração quando der.
