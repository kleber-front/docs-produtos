# Redação de requisitos — exemplos

Consulte na hora de escrever ou revisar o texto de um item. Cada seção mostra o padrão
errado, o motivo e a correção.

## Sumário
- [Requisito funcional](#requisito-funcional)
- [Requisito não funcional](#requisito-não-funcional)
- [Regra de negócio](#regra-de-negócio)
- [Restrição](#restrição)
- [Erros que atravessam a revisão](#erros-que-atravessam-a-revisão)

---

## Requisito funcional

**Ator implícito**
- Ruim: "Deve ser possível aprovar o chamado."
- Problema: sem sujeito, some a permissão. Quem aprova? Todos? Só o gestor?
- Bom: "O gestor da área deve poder aprovar chamados atribuídos ao seu centro de custo."

**Duas obrigações num item**
- Ruim: "O sistema deve permitir cadastrar e aprovar solicitações."
- Problema: impossível marcar como parcialmente atendido; estimativa e teste ficam ambíguos.
- Bom: dois itens, RF-00X (cadastrar) e RF-00Y (aprovar), com RF-00Y dependendo de RF-00X.

**Solução embutida**
- Ruim: "O sistema deve usar WebSocket para atualizar a lista em tempo real."
- Problema: fixa a tecnologia antes da decisão de arquitetura.
- Bom: "A lista de chamados deve refletir alterações feitas por outros usuários sem
  recarga manual da página." A escolha do WebSocket vira decisão técnica, não requisito.
- Exceção: se o WebSocket for imposição de infraestrutura ou contrato, vira RT, não RF.

**Comportamento sem gatilho**
- Ruim: "O sistema deve notificar o solicitante."
- Problema: notificar quando, por qual canal, com qual conteúdo?
- Bom: "Ao mudar o status de um chamado, o sistema deve notificar o solicitante por
  e-mail informando status anterior, novo status e responsável pela mudança."

**Negativa vaga**
- Ruim: "O sistema não deve permitir dados inválidos."
- Problema: "inválido" não é definido em lugar nenhum; não dá para testar.
- Bom: um RF por validação, ou uma RN que define o conjunto de validações e um RF que
  obriga o sistema a aplicá-la antes da gravação.

---

## Requisito não funcional

**Sem métrica**
- Ruim: "O sistema deve ser rápido."
- Bom: "A busca de chamados deve retornar em até 2s no percentil 95, com 50 mil registros
  e 30 usuários simultâneos."
- Regra: métrica, condição de medição e carga. Os três, ou vai para pendência.

**Métrica sem condição de carga**
- Ruim: "Tempo de resposta ≤ 1s."
- Problema: 1s com um usuário e base vazia é trivial; com 500 simultâneos é outro sistema.
- Bom: "≤ 1s (p95) com até 200 usuários simultâneos e base de 1 milhão de registros."

**Qualidade subjetiva**
- Ruim: "A interface deve ser intuitiva."
- Bom: escolha o que realmente se mede — "Um usuário sem treinamento deve concluir a
  abertura de chamado em até 3 minutos em teste de usabilidade com 5 participantes" —
  ou converta em RFs concretos (rótulos, validação inline, estados de erro visíveis).

**Acessibilidade genérica**
- Ruim: "O sistema deve ser acessível."
- Bom: "As telas devem atender WCAG 2.1 nível AA, verificado por auditoria automatizada
  sem violações de nível A e AA e por navegação completa via teclado."

---

## Regra de negócio

**Condição sem exceção**
- Ruim: "Chamado acima de R$ 5.000 exige aprovação do gestor."
- Problema: e se o gestor estiver de férias? E se o solicitante for o próprio gestor?
- Bom: a regra, mais o tratamento — delegação, escalonamento ou bloqueio. Se o tratamento
  não existe na fonte, mantenha o item com status *Incompleto* e pergunte. Não invente.

**Cálculo sem arredondamento nem unidade**
- Ruim: "O valor total é a soma dos itens com desconto aplicado."
- Bom: "Total = Σ(quantidade × valor unitário) − desconto, arredondado para 2 casas
  decimais pelo critério de arredondamento comercial, em BRL."

**Estado sem transição**
- Ruim: "O chamado pode estar aberto, em análise, aprovado ou cancelado."
- Problema: lista estados sem dizer quem muda o quê, a partir de onde.
- Bom: tabela de transições — estado origem, evento, estado destino, ator autorizado.

**Prazo sem calendário**
- Ruim: "O gestor tem 2 dias para aprovar."
- Bom: "2 dias úteis, contados a partir do envio para aprovação, considerando o
  calendário de feriados da unidade do solicitante."

---

## Restrição

Restrição é imposição externa que o projeto não escolhe. Se a equipe pode decidir
diferente, não é RT — é decisão de arquitetura e está fora do escopo desta extração.

- Válido: "A autenticação deve usar o Azure AD corporativo (política de TI)."
- Válido: "O sistema deve operar em navegadores Chrome e Edge, versões N e N-1 (parque
  padronizado)."
- Válido: "Dados pessoais devem permanecer em datacenter no Brasil (jurídico, LGPD)."
- Inválido como RT: "Usar React." — a menos que exista política formal ou contrato que
  obrigue. Nesse caso, cite a política no campo Origem.

---

## Erros que atravessam a revisão

Padrões que parecem corretos e passam despercebidos:

- **Número plausível sem fonte.** "≤ 3s" gravado sem marcação vira compromisso por
  acidente. Todo valor não confirmado leva **[sugerido]**.
- **Duplicidade entre documentos.** O mesmo comportamento, descrito com verbos diferentes
  em duas fontes, gera dois RFs. Reconcilie antes de fechar a tabela.
- **Desejo promovido a requisito.** Menção em ata sem decisão registrada é pendência.
- **Requisito herdado de outro projeto.** Documento reaproveitado carrega itens que não
  se aplicam. Se nada na fonte conecta o item a este sistema, marque e pergunte.
- **Ator inventado.** "Administrador" aparece no requisito mas não existe na lista de
  perfis. Ou o perfil falta, ou o requisito está errado — as duas hipóteses viram pergunta.
