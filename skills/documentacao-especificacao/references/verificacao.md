# Verificação antes de entregar

Converta para PDF e confira as páginas renderizadas. Cada item é sim/não.

## Forma
- [ ] Capa com projeto, analista, data, departamento e solicitante reais — nenhum texto do modelo
- [ ] Controle de Versões com linha real; sem "Bruno Santos - LDB" nem linhas vazias sobrando
- [ ] Sumário lista os títulos gerados (o Word recalcula as páginas ao abrir)
- [ ] Nenhum texto de instrução do modelo `[Descrever…]` no documento
- [ ] Nenhum exemplo do modelo (reembolso, devapi.epgnet, ObterRegionais de exemplo) que não seja do projeto
- [ ] Imagens de protótipo legíveis, sem tela branca, com legenda TL-ID
- [ ] Tabelas com cabeçalho cinza e texto dentro das células

## Conteúdo
- [ ] Ordem das seções igual à do modelo
- [ ] Toda funcionalidade do mapa de telas tem subseção, ou está nas pendências com motivo
- [ ] Todo RF de `04-requisitos.md` aparece em alguma funcionalidade (contagem igual)
- [ ] Todo CT aparece em Testes
- [ ] Todo INT tem subseção com tratamento de falha (ou [pendente])
- [ ] Termos iguais aos do glossário do contexto
- [ ] Mesmo valor para a mesma regra em todo o documento
- [ ] Pendências em aberto listadas em Anexos, iguais às de `04-requisitos.md` ou com motivo para diferir
- [ ] Versões dos artefatos de origem citadas em Anexos

Item reprovado em Conteúdo que exija informação nova → retorno à etapa dona (ver
`fluxo-produto`), não correção local.
