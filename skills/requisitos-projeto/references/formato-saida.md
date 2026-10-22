# Formato de saída — 04-requisitos.md

A organização espelha o Documento de especificação ADS: regras e requisitos agrupados por
funcionalidade (tela), e dentro da tela por bloco estrutural. Isso permite que a etapa 5
transporte cada funcionalidade como subseção sem reescrever.

## 2. Regras de negócio

| ID | Regra | Condição | Exceção | Origem | Funcionalidades (TL) | Status |
|----|-------|----------|---------|--------|----------------------|--------|
| RN-001 | Somente registros com status Aberto podem ser aprovados. | status = Aberto | Não definida | Contexto R-04; Ata DEC-003 | TL-002 | Incompleto |

Status: OK, Incompleto, Ambíguo, Contraditório, Cancelado.
Valor que muda com frequência (alçada, prazo) → anote "parametrizável" na Exceção.

## 3. Requisitos de software por funcionalidade

Uma subseção por TL, na ordem do mapa de telas.

```markdown
### 3.2 TL-002 — Cadastro de solicitação

**Regras de negócio aplicáveis:** RN-001, RN-004
Descrição de negócio (do contexto, em frases "Sempre que…"):
- Sempre que um colaborador precisar cadastrar uma solicitação, ele deve informar …

| ID | Bloco | Elemento | Requisito | Ator | Origem | Depende de | Status |
|----|-------|----------|-----------|------|--------|------------|--------|
| RF-010 | Cabeçalho | Botão Voltar | Ao selecionar Voltar com dados alterados e não salvos, o sistema deve alertar o usuário sobre a perda dos dados e, confirmado, abrir TL-001. | Todos | TL-002 mapa | — | OK |
| RF-011 | Informações gerais | Regional | O campo Regional é obrigatório, do tipo lista, alimentado por INT-001; em inclusão permite selecionar um registro; em edição exibe o valor salvo, sem alteração. | Solicitante | TL-002; Ata Q-007 | INT-001 | OK |
| RF-015 | Rodapé | Botão Aprovar | O botão Aprovar deve estar disponível apenas em modo edição, para perfil Gestor, com status Aberto; ao selecionar, o sistema altera o status para Aprovado e permanece na tela. | Gestor | TL-002; RN-001 | RF-011 | OK |
```

Regras do bloco:
- **Um campo ou ação por linha.** Campo com comportamento diferente em inclusão e edição
  continua sendo uma linha, descrevendo os dois modos (como no modelo ADS).
- Para campo, sempre: tipo, obrigatoriedade, comportamento por modo, origem do dado, formato.
- Para ação, sempre: quem pode, em que estado, o que valida, o que muda, para onde vai.
- Campo marcado [pendente] no protótipo gera RF *Incompleto*, não RF OK.

Fora de tela (processos automáticos, notificações, rotinas): subseção "Funcionalidades sem
interface", mesmo formato, Bloco = "Processo".

## 4. Requisitos não funcionais

| ID | Categoria | Requisito | Métrica / critério | Condição de medição | Origem | Status |

## 5. Restrições

| ID | Restrição | Tipo (técnica, prazo, regulatória, orçamentária, contratual) | Impacto | Origem |

## 6. Requisitos técnicos

Formato em `requisitos-tecnicos.md`.

## 7. Cenários de teste

Por funcionalidade, no formato do modelo ADS:

```markdown
### TL-002 — Cadastro de solicitação

- **CT-007 — Verificar se tem permissão para aprovar** (RF-015, RN-001)
  DADO QUE esteja com o registro aberto,
  E meu perfil de usuário não seja de Gestor,
  QUANDO clicar no botão 'Aprovar',
  ENTÃO a aplicação deve emitir uma mensagem informando que não tenho permissão para aprovar o registro.
```

Só para RF com status OK. Valor que nenhuma RN define → [sugerido] e pendência.

## 8. Rastreabilidade

| Origem | RN | RF | TL | INT / ENT | CT | Status de cobertura |

Célula vazia é informação: RF sem origem, RN sem RF, RF sem CT, tela sem RF. Cada padrão vira
pendência.

## 9. Pendências

| PEN-ID | ID afetado | Problema (ambíguo, incompleto, duplicado, contraditório, sem métrica, sem origem) | O que falta | Destinatário | Criticidade |

## 10. Perguntas

Numeradas (Q-), agrupadas por tema, com destinatário e ID que destrava.
