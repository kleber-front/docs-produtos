# Documentos esperados

Use para montar a seção **Documentos ausentes**. Ausência de um documento não é
necessariamente problema — projetos pequenos vivem bem sem metade desta lista. O que
importa é que a ausência seja consciente, não descoberta tarde.

Ao listar um documento ausente, diga para que ele serve e quem costuma tê-lo. "Falta o
documento X" sem isso não ajuda ninguém a buscá-lo.

## Sumário
- [Sistema novo](#sistema-novo)
- [Evolução de sistema existente](#evolução-de-sistema-existente)
- [Substituição de sistema legado](#substituição-de-sistema-legado)
- [Integração entre sistemas](#integração-entre-sistemas)
- [Automação de processo](#automação-de-processo)
- [Projeto com fornecedor](#projeto-com-fornecedor)

---

## Sistema novo

| Documento | Para que serve | Quem costuma ter |
|-----------|----------------|------------------|
| Documento de visão ou business case | Objetivo, problema, resultado esperado | Patrocinador, produto |
| Requisitos ou PRD | O que o sistema deve fazer | Produto, análise de negócio |
| Regras de negócio | Cálculos, alçadas, validações | Área de negócio |
| Desenho de processo (to-be) | Como o trabalho passa a ser feito | Negócio, processos |
| Matriz de perfis e permissões | Quem faz o quê | Negócio, segurança |
| Requisitos não funcionais | Desempenho, segurança, disponibilidade | Arquitetura, infraestrutura |
| Protótipo ou wireframe | Como a interface se comporta | Design, produto |
| Restrições técnicas e políticas de TI | O que não pode ser escolhido livremente | Arquitetura, TI |

Ausência mais frequente e mais cara: matriz de perfis. Quase nunca vem, quase sempre muda
o escopo quando aparece.

---

## Evolução de sistema existente

Tudo do quadro anterior, mais:

| Documento | Para que serve | Quem costuma ter |
|-----------|----------------|------------------|
| Documentação atual do sistema | Comportamento que precisa ser preservado | Sustentação, TI |
| Modelo de dados atual | O que existe e o que pode quebrar | DBA, desenvolvimento |
| Lista de integrações ativas | O que consome o sistema hoje | Arquitetura, sustentação |
| Backlog de pendências conhecidas | Defeitos e dívidas que talvez entrem no escopo | Sustentação, produto |
| Histórico de incidentes | Onde o sistema falha na prática | Suporte |

Sem documentação atual, o escopo real só aparece durante o desenvolvimento. Registre como
lacuna crítica quando a evolução tocar comportamento existente.

---

## Substituição de sistema legado

| Documento | Para que serve | Quem costuma ter |
|-----------|----------------|------------------|
| Mapeamento de funcionalidades do legado | O que precisa existir no novo | Sustentação, usuários-chave |
| Plano ou regras de migração de dados | O que migra, o que fica, o que se perde | Negócio, dados |
| Dicionário de dados do legado | Como interpretar o que está armazenado | DBA, fornecedor original |
| Definição de convivência ou virada | Os dois sistemas coexistem? Por quanto tempo? | Produto, TI |
| Lista de relatórios e extrações em uso | O que ninguém lembra que existe até faltar | Usuários, sustentação |

A última linha é a que mais gera retrabalho tardio: relatórios operacionais raramente estão
documentados e sempre são exigidos na virada.

---

## Integração entre sistemas

| Documento | Para que serve | Quem costuma ter |
|-----------|----------------|------------------|
| Contrato de API ou especificação técnica | Campos, tipos, obrigatoriedade | Time do sistema externo |
| Política de autenticação da integração | Como se autentica, quem gerencia credencial | Segurança, arquitetura |
| Definição de volume e janela | Quantas chamadas, quando | Arquitetura, negócio |
| Acordo de nível de serviço do externo | O que esperar quando falha | Fornecedor, contrato |
| Ambiente de homologação e dados de teste | Se dá para testar antes de produção | TI do sistema externo |

Registre sempre o interlocutor do outro lado como lacuna quando ele não estiver nomeado.
Integração sem interlocutor trava independentemente da qualidade da documentação.

---

## Automação de processo

| Documento | Para que serve | Quem costuma ter |
|-----------|----------------|------------------|
| Processo atual (as-is) | O que é automatizado | Negócio, processos |
| Volumetria atual | Quantas vezes o processo roda, com que pico | Negócio |
| Regras de exceção | O que hoje é resolvido por decisão humana | Quem executa o processo |
| Definição de tratamento de falha | O que acontece quando a automação erra | Negócio, TI |
| Responsável pela operação após a entrega | Quem monitora | Gestão |

A terceira linha é a mais subestimada: processos manuais vivem de exceções não escritas, e
elas só aparecem quando a automação falha.

---

## Projeto com fornecedor

| Documento | Para que serve | Quem costuma ter |
|-----------|----------------|------------------|
| Contrato ou proposta comercial | Escopo contratado, entregas, marcos | Jurídico, compras |
| Termo de abertura ou escopo assinado | Fronteira do que foi acordado | Gestão de projeto |
| Matriz de responsabilidades | Quem faz o quê entre as partes | Gestão de projeto |
| Critérios de aceite contratuais | Como se aceita a entrega | Contrato, produto |
| Plano de comunicação e pontos focais | Quem decide de cada lado | Gestão de projeto |

Quando houver contrato, ele prevalece sobre documento interno em caso de divergência de
escopo — mas isso é constatação a registrar e confirmar, não decisão sua.
