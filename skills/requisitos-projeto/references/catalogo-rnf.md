# Catálogo de RNF

Use como varredura: percorra as categorias, marque as que se aplicam ao tipo de sistema
e registre como pendência toda categoria aplicável sem nenhuma menção nas fontes.

As métricas listadas são **faixas típicas para sugestão**, nunca valores a gravar como
fechados. Toda sugestão entra marcada `[sugerido]` e permanece em pendência.

## Sumário
- [Desempenho](#desempenho)
- [Escalabilidade e capacidade](#escalabilidade-e-capacidade)
- [Disponibilidade e continuidade](#disponibilidade-e-continuidade)
- [Segurança](#segurança)
- [Privacidade e conformidade](#privacidade-e-conformidade)
- [Usabilidade](#usabilidade)
- [Acessibilidade](#acessibilidade)
- [Compatibilidade](#compatibilidade)
- [Observabilidade e auditoria](#observabilidade-e-auditoria)
- [Manutenibilidade](#manutenibilidade)
- [Integração](#integração)
- [Localização](#localização)

---

## Desempenho
Perguntas: qual operação é a mais sensível? Sob qual volume? Medido onde — servidor ou
percepção do usuário?
Métricas: tempo de resposta por operação (p95 ou p99), tempo de carga inicial,
throughput em requisições por segundo, tempo de processamento em lote.
Faixas comuns: carga inicial de app web interno 2–3s; ação síncrona 200ms–1s;
relatório pesado assíncrono com notificação ao concluir.

## Escalabilidade e capacidade
Perguntas: quantos usuários simultâneos no pico? Qual o crescimento esperado da base em
12 meses? Há sazonalidade — fechamento de mês, campanha?
Métricas: usuários simultâneos suportados, volume de registros, taxa de crescimento,
tamanho máximo de arquivo e de lote.

## Disponibilidade e continuidade
Perguntas: qual janela de indisponibilidade é tolerável? Existe janela de manutenção
acordada? Qual a perda de dados aceitável?
Métricas: disponibilidade (99,5% / 99,9%), RTO, RPO, frequência de backup, retenção.
Observação: 99,9% permite ~8h de indisponibilidade ao ano; 99,5% permite ~44h. A
diferença muda a arquitetura inteira — confirme antes de assumir.

## Segurança
Perguntas: como o usuário se autentica? Há SSO corporativo? Como são tratados perfis e
permissões? Sessão expira em quanto tempo? Dados sensíveis em repouso são cifrados?
Métricas e itens: método de autenticação, MFA, expiração de sessão, política de senha,
criptografia em trânsito e em repouso, controle de acesso por perfil, proteção contra
as vulnerabilidades do OWASP Top 10, gestão de segredos.

## Privacidade e conformidade
Perguntas: o sistema trata dado pessoal? Qual a base legal? Existe prazo de retenção?
Há necessidade de anonimização, exportação ou exclusão a pedido do titular?
Itens: LGPD, retenção e descarte, consentimento, registro de tratamento, dados de
menores, transferência internacional, requisitos setoriais.

## Usabilidade
Perguntas: qual o nível de familiaridade do usuário? Há treinamento previsto? Qual
tarefa precisa ser concluída sem ajuda?
Métricas: tempo de conclusão de tarefa-chave, taxa de erro em formulário, número de
passos até a ação principal, resultado de teste de usabilidade com N participantes.

## Acessibilidade
Perguntas: há exigência formal — contrato, política interna, setor público?
Métricas: WCAG 2.1 nível A ou AA, navegação completa por teclado, contraste mínimo,
compatibilidade com leitor de tela, alvos de toque em mobile.

## Compatibilidade
Perguntas: quais navegadores e versões? Desktop, mobile ou ambos? Resolução mínima?
Há parque padronizado?
Itens: matriz de navegadores, sistemas operacionais, tamanho mínimo de tela,
comportamento offline, impressão.

## Observabilidade e auditoria
Perguntas: quem precisa saber que algo falhou, e como? Existe exigência de trilha de
auditoria? Por quanto tempo o log fica disponível?
Itens: log de aplicação e nível, trilha de auditoria (quem, o quê, quando, valor
anterior e novo), alertas, métricas de saúde, rastreamento de requisição.
Observação: auditoria é o RNF mais esquecido em sistema de aprovação. Se há alçada,
quase sempre há exigência de trilha — pergunte.

## Manutenibilidade
Perguntas: quem mantém depois da entrega? Há padrão de código na organização? Nível
de cobertura de teste esperado?
Itens: padrão de codificação, cobertura de teste, documentação técnica mínima,
versionamento, processo de deploy, ambiente de homologação.

## Integração
Perguntas: quais sistemas conversam com este? Síncrono ou assíncrono? O que acontece
quando o outro lado está fora do ar?
Itens: protocolo, formato, autenticação da integração, tempo limite, política de
retentativa, tratamento de falha, volume e frequência, contrato de dados.
Observação: "o que acontece quando a integração falha" é pergunta obrigatória — a
resposta vira RF, não só RNF.

## Localização
Perguntas: mais de um idioma? Mais de um fuso? Moedas diferentes? Unidades de negócio
com calendário próprio?
Itens: idiomas, formato de data e número, moeda e conversão, fuso horário de
armazenamento e exibição, calendário de feriados.
