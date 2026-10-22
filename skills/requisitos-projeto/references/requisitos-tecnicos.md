# Requisitos técnicos

Quatro áreas, sempre presentes. Área sem informação nas fontes não some: recebe pendência com
destinatário (normalmente Arquitetura/TI).

## Distinção que importa

| Tipo | O que é | Marca | Quem aprova |
|------|---------|-------|-------------|
| RT — Restrição | Imposição que o projeto não escolhe (política de TI, contrato, lei) | sem marca, com origem | — |
| DT — Decisão técnica proposta | Escolha de arquitetura/stack que o fluxo propõe | **[sugerido]** até aprovação | Arquitetura / coordenação de TI |
| DT aprovada | DT confirmada por quem responde | sem marca, com DEC- | — |

Nunca grave uma DT como fato. Uma escolha plausível sem marca atravessa a revisão e vira
compromisso por acidente.

---

## 6.1 Arquitetura e stack

| ID | Camada / tema | Proposta ou imposição | Motivo (o que no contexto/requisito leva a isso) | Alternativas consideradas | Origem | Status |
|----|---------------|-----------------------|-------------------------------------------------|---------------------------|--------|--------|
| DT-001 | Frontend | SPA React + TypeScript + Tailwind + shadcn/ui, reaproveitando a estrutura do protótipo | Decisão do fluxo de protótipo navegável; DS em construção | — | fluxo/00 | [sugerido] |

Temas a cobrir: frontend, backend/API, banco de dados, autenticação e autorização, hospedagem,
filas/rotinas, armazenamento de arquivos, observabilidade, ambientes (dev, homologação,
produção), CI/CD.

Perguntas típicas para a TI: existe padrão corporativo de stack? Onde a aplicação é hospedada?
Qual provedor de identidade (ex.: Azure AD / Entra ID)? Há gateway de APIs corporativo? Existe
padrão de logs?

## 6.2 Integrações

Panorama:

| ID | Sistema | Direção | Finalidade | Gatilho | Síncrona? | Interlocutor | Criticidade | Status |

Por integração, o mesmo formato do modelo ADS:

```markdown
#### INT-001 — API Listar Regionais
Finalidade: alimentar o campo Regional (RF-011, TL-002)
| URL | <ambiente> |
| Método | POST |
| Endpoint | /api/... |
Autenticação: <como; quem gerencia credencial> [pendente se ausente]
Parâmetros: <lista ou "Nenhum">
Corpo da requisição: <campos, tipo, obrigatório, case-sensitive?> + exemplo
Corpo da resposta: Sucesso (status code, exemplo) · Erro (status code, exemplo)
Regras: validações, filtros, paginação
Tratamento de falha: timeout, retentativa, mensagem ao usuário, o que fica bloqueado  ← obrigatório
Volume e janela: <chamadas, pico>
```

Contrato não fornecido → descreva o que o sistema precisa receber/enviar (campos derivados das
telas) marcado [sugerido] e registre pendência "contrato real da API" para o time do sistema
externo. Não invente URL nem endpoint.

## 6.3 Modelo e dicionário de dados

Entidades:

| ID | Entidade | Descrição | Origem (telas, integrações) | Relacionamentos |

Dicionário por entidade, no formato do modelo ADS:

| Campo | Tipo | Obrigatório | Descrição | Exemplo | Origem (RF/INT) |
|-------|------|-------------|-----------|---------|-----------------|
| ID | Inteiro | Sim | Código sequencial do registro | 405 | RF-010 |
| Status | Enumerado | Sim | 1 – Aberto; 2 – Aprovado; 3 – Em andamento; 4 – Cancelado; 5 – Concluído | 1 | RN-001 |

Regras:
- Todo campo do dicionário aparece em alguma tela, integração ou regra. Campo órfão = pendência.
- Todo campo de tela persistido aparece no dicionário.
- Tipo e tamanho (ex.: Varchar2(100)) só com origem; senão [sugerido].
- Enumerados listam código e rótulo.
- Dado pessoal ou sensível é sinalizado na descrição e cruzado com 6.4 (LGPD).

## 6.4 Infraestrutura e segurança

| ID | Tema | Requisito | Métrica / critério | Origem | Status |

Temas: autenticação (SSO corporativo, MFA), autorização por perfil e por dado (regional, centro
de custo), expiração de sessão, trilha de auditoria (quem, o quê, quando, valor anterior e
novo), criptografia em trânsito e repouso, gestão de segredos, LGPD (base legal, retenção,
exclusão), backup e retenção, disponibilidade (RTO/RPO), ambientes e janela de deploy, logs e
alertas.

Itens mensuráveis podem ficar como RNF (seção 4) e ser referenciados aqui; não duplique o texto.
