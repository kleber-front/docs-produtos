# Critérios de aceite

Critério de aceite responde uma pergunta: **como saber que este requisito foi atendido?**
Não é roteiro de teste — não descreve cliques, dados de massa nem ambiente. Descreve a
condição observável que precisa ser verdadeira.

## Formato

Duas formas, escolha por item:

**Lista de condições** — para requisito com várias verificações independentes:

```
RF-001 — Abertura de chamado
- Chamado é criado com status "Aberto" e número sequencial único.
- Categoria, descrição e centro de custo são obrigatórios; envio é bloqueado sem eles.
- Anexo aceita PDF, PNG e JPG até 10 MB; formato ou tamanho fora disso é rejeitado com
  mensagem indicando o motivo.
- O solicitante recebe confirmação com o número do chamado.
```

**Dado / Quando / Então** — para comportamento condicional, especialmente quando há
regra de negócio envolvida:

```
RF-007 — Aprovação por alçada
- Dado um chamado de R$ 6.000, quando o solicitante envia para aprovação, então o
  chamado é direcionado ao gestor do centro de custo e fica com status "Aguardando
  aprovação".
- Dado um chamado de R$ 4.000, quando o solicitante envia, então o chamado segue
  direto para "Em atendimento", sem etapa de aprovação.
```

Não misture os dois formatos dentro do mesmo RF.

## Regras

- **Um critério, uma verificação.** Se precisa de "e" para ligar duas condições
  independentes, são dois critérios.
- **Observável de fora.** "O registro é gravado na tabela X" não é critério de aceite —
  é detalhe de implementação. "O chamado aparece na listagem do solicitante" é.
- **Inclua o caminho negativo.** Critério que só cobre o fluxo feliz deixa passar
  metade dos defeitos. Para cada validação, um critério de rejeição.
- **Sem dado de massa.** "Usar o usuário teste01" pertence ao plano de teste, não aqui.
- **Derivado da regra, não inventado.** Se o critério exige um valor que nenhuma RN
  define — limite, prazo, formato —, esse valor é pendência. Marque `[sugerido]` e
  pergunte; não escreva o critério como se o número estivesse decidido.

## Quando não escrever

Não produza critérios de aceite para:

- **RF com status diferente de OK.** Requisito ambíguo ou incompleto gera critério
  igualmente ambíguo, com a agravante de parecer fechado.
- **RNF.** A métrica já é o critério. Repetir em outra seção duplica a manutenção.
- **RN isolada.** Regra é verificada através dos RFs que a aplicam. Se uma RN não é
  exercida por nenhum RF, isso é pendência: ou falta o RF, ou a regra não se aplica.

## Cobertura mínima por RF

Antes de fechar, confira se os critérios cobrem:

1. Fluxo principal com dados válidos.
2. Cada validação, no caminho de rejeição.
3. Permissão — o que acontece quando o ator errado tenta a ação.
4. Estado resultante, quando o requisito altera status.
5. Efeito colateral esperado — notificação, registro em auditoria, atualização de saldo.

Item de 1 a 5 sem cobertura e sem informação na fonte vira pendência, não critério
inventado.
