# Mapeamento: seção do modelo ADS → origem

| Seção do modelo | Nível | Origem | Observação |
|-----------------|-------|--------|------------|
| Capa — Data de publicação | — | Data de emissão | "outubro de 2026" |
| Capa — Analista | — | Usuário / estado do fluxo | |
| Capa — Título do projeto | — | Contexto, nome do projeto | |
| Capa — Time de TI | — | Padrão "Arquitetura e desenvolvimento de software" salvo indicação | |
| Capa — Departamento / Solicitante | — | Contexto seção 8 / TAP | |
| Controle de Versões | tabela | Histórico do documento | Uma linha por versão emitida; resumo real ("Inclusão das funcionalidades X e Y") |
| Objetivo | H1 | Contexto §2 | Começar por "O objetivo deste projeto é…" |
| Escopo | H1 | Contexto §3 | "Itens incluídos:" / "Itens excluídos:" em negrito + marcadores |
| Justificativa | H1 | Contexto §4 | "O projeto se justifica porque…" |
| Cenário atual | H1 | Contexto §5 | Prosa curta |
| Restrições | H1 | Contexto §6 + RT- de 04-requisitos | Marcadores; cite RT-ID |
| Premissas | H1 | Contexto §7 | Marcadores |
| Dependências de negócio | H1 | Contexto §8 | Frase introdutória do modelo + tabela de 4 colunas |
| Dependências de TI | H1 | Contexto §9 + DT-/INT- | Frase introdutória + tabela de 4 colunas |
| Requisitos de Software | H1 | — | Só título |
| <Funcionalidade> | H2 | 04-requisitos §3 (por TL) | Nome no padrão "Consulta de…", "Cadastro de…", "Dashboard de…" |
| — regras de negócio | marcadores | RN- aplicáveis | Frases "Sempre que…"; RN-ID ao final |
| Protótipo | H3 | 03-capturas/TL-xxx-*.png | Uma ou mais imagens; legenda com TL-ID e estado |
| Requisitos funcionais e não funcionais | H3 | 04-requisitos §3 (RF da TL) + RNF ligados | Rótulo em negrito por bloco; item "**Elemento:** descrição (RF-ID)"; subitens nível 1 |
| Requisitos Técnicos | H1 | 04-requisitos §6 | Incluir antes do dicionário um H2 "Arquitetura e stack" e um H2 "Infraestrutura e segurança" quando houver conteúdo |
| Dicionário de dados | H2 | 04-requisitos §6.3 | Uma tabela por ENT: Campo, Tipo, Obrigatório, Descrição, Exemplo |
| Integrações | H2 | 04-requisitos §6.2 | Uma H3 por INT |
| <API> | H3 | INT- | Tabela chave-valor URL/Método/Endpoint; Parâmetros; Corpo da requisição; Corpo da resposta; Regras |
| Testes | H1 | — | Só título |
| Cenários de teste | H2 | 04-requisitos §7 | |
| <Funcionalidade> | H3 | CT- da TL | Cenário: título em negrito com marcador + linhas DADO QUE / E / QUANDO / ENTÃO |
| Anexos | H1 | Fontes (FON-), artefatos do fluxo, pendências | Links, versões dos artefatos usados, "Pendências em aberto" |

## Ordem obrigatória

Objetivo → Escopo → Justificativa → Cenário atual → Restrições → Premissas → Dependências de
negócio → Dependências de TI → Requisitos de Software → Requisitos Técnicos → Testes → Anexos.

Seção do modelo sem conteúdo de origem: mantenha o título e uma linha "[pendente] — <o que
falta> (PEN-ID)". Não remova seção do modelo.
