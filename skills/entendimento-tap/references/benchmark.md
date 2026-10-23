# Benchmark de soluções de mercado

Objetivo: responder, com evidência, **"existe algo pronto que resolva isto, total ou
parcialmente?"** — antes de o projeto investir em protótipo e especificação de algo que se
compra ou se configura.

O benchmark informa a decisão; não a toma. Comprar, configurar ou construir é decisão do
patrocinador e da TI.

## Sumário
- [Quando fazer](#quando-fazer)
- [Como pesquisar](#como-pesquisar)
- [Categorias de alternativa](#categorias-de-alternativa)
- [Critérios de comparação](#critérios-de-comparação)
- [Formato](#formato)
- [Erros comuns](#erros-comuns)

---

## Quando fazer

Sempre na etapa 1. Mesmo quando a TAP já diz "desenvolver sistema", o benchmark é o que
permite dizer à reunião que a alternativa foi considerada. Se a TAP proíbe expressamente
aquisição, registre a restrição e faça o benchmark reduzido (só para referência de
funcionalidades e boas práticas).

## Como pesquisar

1. **Descreva o problema em termos de capacidade**, não de tela: "gestão de solicitações de
   reembolso com aprovação por alçada", "controle de chamados de material de obra".
2. **Faça buscas em paralelo** (ferramenta de busca web), em português e inglês, variando:
   - categoria de software ("software de gestão de reembolso", "expense management software");
   - setor ("construção civil", "incorporadora", "construction ERP add-on");
   - plataforma corporativa já usada pela empresa, quando conhecida pelas fontes (ex.: módulos
     do ERP, ecossistema Microsoft 365 — Power Apps, SharePoint, Power Automate);
   - nomes de concorrentes que aparecerem nos primeiros resultados.
3. **Abra as páginas oficiais** dos candidatos (ferramenta de leitura de página web) para confirmar funcionalidades e
   modelo de preço. Resultado de busca não basta como evidência.
4. **Registre data de consulta e link** de cada informação. Preço e funcionalidade mudam.
5. **Pare em 3 a 6 alternativas relevantes.** Mais que isso dilui a análise. Se não encontrar 3,
   diga quantas encontrou e quais buscas fez.

Se a pesquisa web não estiver disponível na sessão, diga isso na primeira linha da seção e
registre o benchmark como **[pendente]** — não monte benchmark de memória.

## Categorias de alternativa

Cubra, quando fizer sentido, uma de cada:

| Categoria | Exemplo de pergunta |
|-----------|---------------------|
| SaaS / produto de mercado | Existe produto que já faz isso? |
| Módulo ou recurso do ERP / sistema atual | O sistema que a empresa já tem resolve com configuração? |
| Plataforma low-code corporativa | Dá para montar na plataforma que a empresa já licencia? |
| Desenvolvimento próprio | Referência de base — o que se ganha e o que se assume |

"Desenvolvimento próprio" entra como linha de comparação, sem pesquisa de mercado e sem custo
estimado.

## Critérios de comparação

Use os critérios que a TAP torna relevantes; estes são o ponto de partida:

- **Aderência ao escopo** — quais funcionalidades candidatas (seção 11) atende: total, parcial,
  não atende, não verificado.
- **Gaps** — o que o projeto precisa e a solução não tem.
- **Integrações** — conecta com os sistemas da seção 14? Tem API?
- **Autenticação corporativa** — SSO com o provedor da empresa, quando conhecido.
- **Dados e LGPD** — onde os dados ficam, existe DPA, hospedagem no Brasil.
- **Idioma e localização** — PT-BR, moeda, calendário, regionais.
- **Modelo comercial** — por usuário, por volume, licença; preço público ou "sob consulta". Cite
  o valor com data; nunca estime.
- **Suporte e presença no Brasil**.
- **Maturidade** — clientes de referência no setor, quando a página oficial informar.

## Formato

Arquivo próprio `fluxo/<projeto>/01-benchmark.md`, com o cabeçalho de versionamento das
convenções, sempre na mesma versão do contexto. A seção 15 do contexto traz só o resumo.

```markdown
## Benchmark de mercado

Data da pesquisa: dd/mm/aaaa | Buscas realizadas: <lista das consultas>
Problema pesquisado: <capacidade em uma linha>

### Visão comparativa
| BMK-ID | Solução | Categoria | Aderência ao escopo | Principais gaps | Integrações | Modelo comercial [externo] | Fonte |
|--------|---------|-----------|---------------------|-----------------|-------------|----------------------------|-------|

### Por solução
#### BMK-001 — <nome>
- O que é: <uma linha> [externo] (<link>, consultado em dd/mm/aaaa)
- Atende: <funcionalidades da seção 11>
- Não atende / não verificado: <...>
- Pontos a confirmar com fornecedor: <...>

### Leitura para a reunião
3 a 5 linhas, sem recomendar: o que o benchmark mostra (ex.: "nenhuma solução avaliada cobre a
aprovação por alçada integrada ao ERP; duas cobrem o fluxo de solicitação") e qual pergunta de
decisão ele levanta para o patrocinador (vira Q-).
```

## Erros comuns

- **Recomendar.** "A melhor opção é X" é decisão. Apresente critérios e gaps.
- **Afirmar funcionalidade sem fonte oficial.** Página de review ou comparador não basta para
  "atende"; use "não verificado".
- **Preço inventado ou estimado.** Só preço publicado, com data, ou "sob consulta".
- **Comparar por marketing.** "Solução líder", "plataforma completa" não são critérios.
- **Benchmark desconectado do escopo.** Toda linha de aderência aponta para funcionalidades
  candidatas da seção 11.
