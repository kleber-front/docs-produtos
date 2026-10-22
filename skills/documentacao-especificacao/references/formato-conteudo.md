# JSON de conteúdo do script

O script `gerar_especificacao.py` lê um JSON com três chaves: `capa`, `versoes` e `blocos`.
Caminhos relativos (imagens, saída) são resolvidos a partir da pasta do JSON.

Texto aceita `**negrito**` inline. As marcas `[pendente]`, `[inferido]`, `[divergente]`,
`[sugerido]` e `[externo]` saem em negrito itálico automaticamente.

## Exemplo resumido

```json
{
  "saida": "05-especificacao-portal-x.docx",
  "capa": {
    "projeto": "Portal X",
    "time_ti": "Arquitetura e desenvolvimento de software",
    "analista": "Kleber Menezes",
    "data_publicacao": "outubro de 2026",
    "data_iso": "2026-10-19",
    "departamento": "Suprimentos",
    "solicitante": "Nome do solicitante"
  },
  "versoes": [
    {"autor": "Kleber Menezes", "versao": "0.1", "data": "19/10/2026",
     "resumo": "Versão inicial a partir do Contexto v1.0, Requisitos v1.0 e protótipo v1.0."}
  ],
  "blocos": [
    {"t": "h1", "texto": "Objetivo"},
    {"t": "p",  "texto": "O objetivo deste projeto é ..."},

    {"t": "h1", "texto": "Escopo"},
    {"t": "rotulo", "texto": "Itens incluídos:"},
    {"t": "li", "texto": "Consulta de solicitações"},
    {"t": "rotulo", "texto": "Itens excluídos:"},
    {"t": "li", "texto": "Integração com o ERP para baixa de estoque (DEC-004)"},

    {"t": "h1", "texto": "Dependências de negócio"},
    {"t": "p",  "texto": "Para a solução proposta, considerando os processos e requisitos de negócio, foi identificado que além do departamento ..., os seguintes departamentos também têm responsabilidades no processo:"},
    {"t": "tabela", "cabecalho": ["Área de negócio", "Responsabilidade", "Parte interessada", "Funcionalidade"],
     "linhas": [["Controladoria", "Auditar as solicitações concluídas", "Nome - Área", "Consulta de solicitações"]]},

    {"t": "h1", "texto": "Requisitos de Software"},
    {"t": "h2", "texto": "Consulta de solicitações"},
    {"t": "li", "texto": "Sempre que um colaborador precisar consultar a situação de sua solicitação, ... (RN-002)"},
    {"t": "h3", "texto": "Protótipo"},
    {"t": "img", "caminho": "03-capturas/TL-001-com-dados.png", "largura_cm": 15, "legenda": "TL-001 — Consulta de solicitações"},
    {"t": "h3", "texto": "Requisitos funcionais e não funcionais"},
    {"t": "rotulo", "texto": "Cabeçalho"},
    {"t": "li", "texto": "**Logotipo da empresa:** Mostrar o logotipo do Grupo Plaenge. (RF-001)"},
    {"t": "rotulo", "texto": "Resultado"},
    {"t": "p",  "texto": "O resultado da consulta deve ser apresentado em lista de cartões com rolagem vertical. (RF-008)"},
    {"t": "li", "texto": "**Cartão do registro:** Mostrar cada registro em um cartão contendo:"},
    {"t": "li", "texto": "**ID:** Código do registro.", "nivel": 1},

    {"t": "h1", "texto": "Requisitos Técnicos"},
    {"t": "h2", "texto": "Dicionário de dados"},
    {"t": "rotulo", "texto": "ENT-001 — Solicitação"},
    {"t": "tabela", "cabecalho": ["Campo", "Tipo", "Obrigatório", "Descrição", "Exemplo"],
     "linhas": [["ID", "Inteiro", "Sim", "Código sequencial do registro", "405"],
                ["Status", "Enumerado", "Sim", "Status atual:\n1 – Aberto\n2 – Aprovado", "1"]]},
    {"t": "h2", "texto": "Integrações"},
    {"t": "h3", "texto": "API Listar Regionais (INT-001)"},
    {"t": "chave_valor", "linhas": [["URL", "[pendente]"], ["Método", "POST"], ["Endpoint", "[pendente]"]]},
    {"t": "rotulo", "texto": "Corpo da requisição:"},
    {"t": "codigo", "texto": "{\n  \"Name\": \"ObterRegionais\"\n}"},
    {"t": "rotulo", "texto": "Regras:"},
    {"t": "li", "texto": "**Tratamento de falha:** [pendente] (PEN-007)"},

    {"t": "h1", "texto": "Testes"},
    {"t": "h2", "texto": "Cenários de teste"},
    {"t": "h3", "texto": "Cadastro de solicitação"},
    {"t": "cenario", "titulo": "CT-007 — Verificar se tem permissão para aprovar",
     "passos": ["DADO QUE esteja com o registro aberto,", "E meu perfil de usuário não seja de Gestor,",
                "QUANDO clicar no botão 'Aprovar',", "ENTÃO a aplicação deve emitir uma mensagem informando que não tenho permissão para aprovar o registro."]},

    {"t": "h1", "texto": "Anexos"},
    {"t": "li", "texto": "TAP do projeto (FON-001), versão 1.0 de 10/10/2026: <link>"},
    {"t": "rotulo", "texto": "Pendências em aberto"},
    {"t": "tabela", "cabecalho": ["ID", "Item afetado", "Pendência", "Destinatário"],
     "linhas": [["PEN-007", "INT-001", "Tratamento de falha da API", "TI – Integrações"]]}
  ]
}
```

Outros blocos: `h4`, `quebra` (quebra de página).
