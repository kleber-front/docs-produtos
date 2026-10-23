---
name: prototipo-navegavel
description: "Cria o protótipo navegável em React (Vite + TypeScript + Tailwind + shadcn/ui + React Router + dados mock) de um projeto do Grupo Plaenge a partir do Contexto do Projeto validado — uma tela por funcionalidade, com perfis simuláveis, estados de vazio/erro/sem permissão, mapa de telas rastreável (TL-ID) e capturas de cada tela para o documento de especificação — e cria ou evolui a fundação do Design System. Use quando o usuário pedir \"cria o protótipo\", \"monta as telas\", \"prototipa a partir do contexto\", \"protótipo navegável\", \"atualiza a tela X depois da validação\", ou quando o orquestrador fluxo-produto chamar a etapa 3.\n"
metadata:
  version: "0.1.0"
---

# Protótipo navegável

Transforme o Contexto do Projeto em telas que o negócio consiga clicar e validar — e que a
etapa de requisitos e a documentação consigam descrever campo a campo.

O protótipo não é enfeite da especificação: é onde as lacunas de regra aparecem. Cada campo
desenhado faz uma pergunta (obrigatório? de onde vem? quem pode editar?). Quando a resposta não
está no contexto, a tela mostra **[pendente]** e a pergunta volta para o contexto — nunca é
respondida pelo prototipador.

Convenções comuns em `references/convencoes.md`. Leia antes de começar.

## Entradas

- `01-contexto-projeto.md` com Status Validado — obrigatório. Com Status Rascunho (sem
  reunião), avise que o protótipo será exploratório e marque o mapa de telas como tal.
- `01-persona.md` — consulta: onde cada persona trabalha, a familiaridade com tecnologia e a
  jornada orientam dispositivo, densidade e ordem de navegação. Não cria tela nem campo: o que
  vira tela vem do contexto.
- `02-ata-reuniao.md` e `02-prontidao-prototipo.md` — obrigatórios quando existirem.
- `design-system.md` — se já existir de projeto anterior, reutilize e evolua; não recrie.
- Modelo ADS (`documentacao-especificacao/assets`) — consulta: os blocos de tela do modelo
  (Cabeçalho, Barra de títulos, Filtros, Resultado, Rodapé) orientam a estrutura das telas.

## Fluxo

1. **Liste as telas** a partir das funcionalidades candidatas confirmadas (seção 11 do
   contexto / lista de prontidão). Uma funcionalidade pode gerar mais de uma tela; uma tela não
   existe sem funcionalidade de origem. Atribua TL-ID.
2. **Escolha o padrão de cada tela** em `references/padroes-tela.md` (consulta, cadastro,
   aprovação, dashboard, detalhe). O padrão dá a estrutura; o contexto dá o conteúdo.
3. **Apresente o mapa de telas e a navegação** (tela → ações → destino) e, se estiver com o
   usuário, pare para validação antes de codificar. Em modo subagente, siga e registre o mapa.
4. **Monte o projeto** conforme `references/stack-e-estrutura.md`: estrutura por domínio, mocks
   tipados, rotas, seletor de perfil.
5. **Aplique o Design System** conforme `references/design-system.md`: tokens primeiro,
   componentes shadcn depois, nada de valor visual hardcoded.
6. **Construa cada tela** com os estados obrigatórios: com dados, vazio, carregando, erro, sem
   permissão. Estado sem regra no contexto = pendência visível na tela e no mapa.
7. **Rode o build** (`npm run build`) e corrija até passar sem erro.
8. **Gere as capturas** de cada tela e estado principal com Playwright, conforme
   `references/captura-telas.md`. Elas vão para o documento da etapa 5.
   Em seguida, **envie as telas ao Figma** conforme `references/envio-figma.md` (um frame por
   tela e estado, com o Design System da biblioteca). Em modo subagente sem acesso ao conector
   do Figma, não tente: registre "Envio ao Figma: pendente" no mapa — o orquestrador faz o envio.
9. **Escreva o mapa de telas** (`03-mapa-telas.md`) com a estrutura de cada tela no mesmo
   formato de blocos do modelo ADS — é o insumo direto dos requisitos.
10. **Entregue** e peça a sessão de validação com negócio. Registre o resultado em
    `03-validacao-prototipo.md` (quem, quando, o que foi aprovado, rejeitado, pedido). Regra
    nova ou alterada na validação volta ao contexto (etapa 2) — não é ajustada só na tela.

## Saídas

| Arquivo | Conteúdo |
|---------|----------|
| `prototipo/` | Projeto React navegável |
| `prototipo.zip` | Projeto compactado para entrega (sem node_modules) |
| `03-mapa-telas.md` | TL-ID, rota, funcionalidade de origem, perfis, estrutura por blocos, navegação, pendências |
| `03-capturas/TL-xxx-<estado>.png` | Capturas para o documento |
| Arquivo Figma | Telas do protótipo espelhadas no Figma; link no `03-mapa-telas.md` e no `estado.md` |
| `design-system.md` | Tokens, componentes base, padrões — criado ou evoluído |
| `03-validacao-prototipo.md` | Registro da validação com negócio |

## Formato do mapa de telas

```markdown
## TL-002 — Cadastro de solicitação
Rota: /solicitacoes/nova · /solicitacoes/:id
Funcionalidade de origem: #3 do contexto (Cadastrar solicitação) · Regras: R-02, R-05
Perfis: Solicitante (inclusão, edição própria) · Gestor (edição, aprovar) · Consulta (leitura)
Modos: inclusão, edição

**Cabeçalho** — Logotipo Plaenge · Home (portal CSC) · Voltar (alerta de dados não salvos → TL-001)
**Barra de títulos** — Título · Identificador (ID, Título, Responsável) em edição
**Acompanhamento do status** — migalha: Aberto → Aprovado → Em andamento → Concluído | Cancelado
**Grupo Informações gerais** (expansível)
| Campo | Tipo | Obrigatório | Inclusão | Edição | Origem do dado | Regra | Situação |
| Regional | Lista | Sim | Seleciona | Somente leitura | API Regionais [pendente] | R-02 | OK |
**Rodapé** — Salvar · Aprovar (Gestor, status Aberto) · Cancelar · Concluir

Estados: vazio — n/a · erro ao salvar — mensagem [pendente] · sem permissão — botão oculto [inferido]
Navegação: Salvar → TL-001 · Voltar → TL-001
Pendências: PEN-004 (mensagem de erro), Q-021 (quem pode cancelar)
Capturas: 03-capturas/TL-002-inclusao.png, TL-002-edicao.png
Figma: <link do frame TL-002>
```

## Regras

- **Tela sem funcionalidade de origem não existe.** Se parecer necessária (ex.: login,
  configurações), registre como [sugerido] e pergunte.
- **Campo sem origem fica marcado.** Rótulo pode ser deduzido; obrigatoriedade, validação e
  permissão, não.
- **Dados mock realistas e neutros.** Nomes fictícios, regionais e valores plausíveis; nunca
  dados reais de pessoas.
- **Nada de backend.** Mocks em memória; integrações simuladas com atraso e erro configuráveis
  para mostrar estados.
- **Português do Brasil** em toda a interface; datas DD/MM/AAAA; moeda BRL.
- **Acessibilidade desde o início**: rótulos em todo campo, foco visível, contraste AA,
  navegação por teclado. Use `design:accessibility-review` quando disponível antes da
  validação.
- **Não decida arquitetura de produção.** A estrutura do protótipo é reaproveitável, mas
  escolha de backend, autenticação e hospedagem é da etapa 4 (DT-) com aprovação da TI.

## Quando perguntar

- Funcionalidade confirmada sem dados definidos (não dá para desenhar a tela).
- Dois padrões de tela razoáveis que mudam o fluxo (ex.: cadastro em página vs. em modal).
- Perfil com permissão ambígua sobre uma ação principal.
- Existe identidade visual ou portal de referência (ex.: portal CSC) não fornecido.

Máximo de 5 perguntas por rodada.

## Material de apoio

- `references/convencoes.md` — marcas, IDs, status, modo subagente.
- `references/stack-e-estrutura.md` — setup, estrutura de pastas, mocks, perfis.
- `references/padroes-tela.md` — estrutura padrão de consulta, cadastro, aprovação, dashboard.
- `references/design-system.md` — fundação do DS e como evoluí-la.
- `references/captura-telas.md` — capturas com Playwright.
- `references/envio-figma.md` — envio das telas ao Figma pelo conector.
