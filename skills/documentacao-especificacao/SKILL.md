---
name: documentacao-especificacao
description: "Gera o Documento de especificação ADS (modelo padrão do Grupo Plaenge, .docx) de um projeto a partir dos artefatos do fluxo — Contexto do Projeto, ata da reunião, mapa de telas e capturas do protótipo, requisitos funcionais e técnicos e cenários de teste — preenchendo capa, controle de versões, objetivo, escopo, justificativa, cenário atual, restrições, premissas, dependências, requisitos de software por funcionalidade com protótipo, requisitos técnicos (dicionário de dados, integrações), testes e anexos, sem inventar conteúdo. Use quando o usuário pedir \"documenta o projeto\", \"gera a especificação\", \"monta o documento ADS\", \"preenche o modelo de especificação\", \"documento com os protótipos\", ou quando o orquestrador fluxo-produto chamar a etapa 5.\n"
metadata:
  version: "0.1.0"
---

# Documento de especificação ADS

Transforme os artefatos do fluxo no Documento de especificação do modelo ADS, preservando a
formatação do modelo (capa, logotipo, faixa, estilos, sumário, tabelas) e o vocabulário dos
artefatos.

Documentar é registrar, não decidir. Todo conteúdo vem de um artefato anterior. Seção sem fonte
fica **[pendente]** e entra nas pendências; nunca é preenchida com texto plausível.

Convenções comuns em `references/convencoes.md`. Leia antes de começar.

## Entradas

| Artefato | Uso no documento |
|----------|------------------|
| `01-contexto-projeto.md` v1.0 | Objetivo, Escopo, Justificativa, Cenário atual, Restrições, Premissas, Dependências |
| `02-ata-reuniao.md` | Decisões citadas; partes interessadas; anexos |
| `03-mapa-telas.md` + `03-capturas/` | Seções de funcionalidade e imagens de protótipo |
| `04-requisitos.md` | Regras e requisitos por funcionalidade, requisitos técnicos, testes |
| `design-system.md` | Só referência em Anexos, se pertinente |
| Modelo `assets/modelo-especificacao-ads.docx` | Base do documento — sempre |

Sem `04-requisitos.md`, pare: o documento não tem o que especificar.

## Fluxo

1. **Confirme as entradas e versões.** Registre a versão de cada artefato usado; ela vai para o
   resumo do Controle de Versões e para os Anexos.
2. **Confirme os dados da capa** (projeto, analista, departamento, solicitante, data) e a versão
   do documento. Dado ausente → pergunte; não use o texto do modelo.
3. **Proponha o índice** — lista de funcionalidades (uma subseção H2 por TL ou grupo de TLs) e
   integrações (uma H3 por INT). Com o usuário presente, pare para validar. Em modo subagente,
   siga e registre o índice no status.
4. **Mapeie conteúdo → seção** conforme `references/mapeamento-modelo.md`. Cada seção do modelo
   tem uma fonte definida; respeite a ordem do modelo.
5. **Monte o JSON de conteúdo** no formato de `references/formato-conteudo.md`.
6. **Gere o .docx** com o script:
   `python3 ${CLAUDE_PLUGIN_ROOT}/skills/documentacao-especificacao/scripts/gerar_especificacao.py conteudo.json`
   (sem a variável disponível, use o caminho da skill). O script mantém capa, estilos, cabeçalho,
   rodapé e sumário do modelo, preenche capa e Controle de Versões e substitui o corpo.
7. **Verifique**: converta para PDF (`soffice --headless --convert-to pdf`), gere imagens das
   páginas (`pdftoppm -r 60 -png`) e confira capa, sumário, uma seção de funcionalidade com
   protótipo, o dicionário de dados e os testes. Rode o checklist de
   `references/verificacao.md`.
8. **Entregue** o .docx (e o PDF, se pedido) e liste as pendências que ficaram no documento.

## Regras do modelo

- **Remova todo texto de instrução** do modelo (os trechos *[entre colchetes, em itálico
  cinza]*) e todo exemplo do modelo (reembolso, "Bruno Santos - LDB", API Listar Regionais de
  exemplo, URL devapi). O script já remove o corpo; não copie exemplos para o JSON.
- **Requisitos de Software**: uma subseção por funcionalidade com, nesta ordem: regras de
  negócio em frases "Sempre que…" (com RN-ID ao final), H3 "Protótipo" com a captura, H3
  "Requisitos funcionais e não funcionais" agrupados por bloco da tela (Cabeçalho, Barra de
  títulos, Filtros, Resultado, Grupos, Rodapé), cada item "**Elemento:** descrição (RF-ID)".
- **Dicionário de dados**: colunas do modelo — Campo, Tipo, Obrigatório, Descrição, Exemplo — uma
  tabela por entidade (ENT-ID no título).
- **Integrações**: uma H3 por INT, com a tabela URL/Método/Endpoint e as seções Parâmetros, Corpo
  da requisição, Corpo da resposta (Sucesso/Erro) e Regras. Inclua "Tratamento de falha" em
  Regras. URL ou endpoint desconhecido = [pendente].
- **Testes**: cenários por funcionalidade em DADO QUE / E / QUANDO / ENTÃO, com CT-ID no título.
- **Dependências de negócio e de TI**: tabelas do modelo, coluna Funcionalidade com o nome da
  subseção correspondente.
- **IDs preservados**: RF, RN, RNF, INT, ENT, CT e TL aparecem entre parênteses ao final do item.
  Nunca renumere.
- **Pendências e suposições**: o modelo não tem seção própria; registre-as em Anexos, subseção
  "Pendências em aberto", com ID, item afetado e destinatário. Não esconda em rodapé.

## Quando perguntar

- Dados da capa ou do Controle de Versões ausentes (autor, versão, departamento, solicitante).
- Funcionalidade com RF incompletos: incluir com [pendente] ou adiar a subseção?
- Integração sem contrato: documentar o que se sabe com [pendente] ou omitir até o contrato?
- Divergência entre `04-requisitos.md` e o mapa de telas — volta para a etapa dona, não se
  resolve aqui.

Máximo de 5 perguntas por rodada.

## Escopo

**Fora do escopo:** criar requisito, regra ou decisão; alterar tela; propor arquitetura nova;
estimar. Se para completar uma seção for preciso inventar, a seção não estava pronta — volte uma
etapa.

## Material de apoio

- `references/convencoes.md` — marcas, IDs, status, modo subagente.
- `references/mapeamento-modelo.md` — seção do modelo → artefato de origem.
- `references/formato-conteudo.md` — JSON de entrada do script, com exemplo por seção.
- `references/verificacao.md` — checklist antes de entregar.
- `references/estilo.md` — redação para quem não estava presente.
- `references/rastreabilidade.md` — IDs e versionamento.
- `scripts/gerar_especificacao.py` — gera o .docx a partir do modelo.
- `assets/modelo-especificacao-ads.docx` — modelo oficial.
