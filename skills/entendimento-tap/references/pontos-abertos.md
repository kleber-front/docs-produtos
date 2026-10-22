# Pontos em aberto por área

Varra as áreas abaixo ao consolidar. Cada item é algo que costuma não estar escrito em lugar
nenhum e que ninguém percebe faltando até a etapa seguinte.

Ausência de menção não significa inaplicável. Verifique se a fonte diz algo; se não diz,
registre como ponto em aberto com destinatário — não conclua nem preencha.

## Sumário
- [Objetivo e escopo](#objetivo-e-escopo)
- [Atores e permissões](#atores-e-permissões)
- [Regras de negócio](#regras-de-negócio)
- [Fluxos](#fluxos)
- [Dados](#dados)
- [Integrações](#integrações)
- [Transição e convivência](#transição-e-convivência)
- [Decisão e governança](#decisão-e-governança)
- [Classificação de criticidade](#classificação-de-criticidade)

---

## Objetivo e escopo
Destinatário típico: produto, patrocinador.

- O que está explicitamente **fora** de escopo. Quase nunca é declarado.
- Como se sabe que o projeto deu certo — indicador, meta, forma de medir.
- Existe fase 2 prevista? O que foi adiado para ela?
- O projeto substitui, complementa ou convive com algo existente?
- Qual área é dona do produto depois da entrega?

---

## Atores e permissões
Destinatário típico: negócio, segurança.

- A lista de perfis está completa, incluindo administrador e perfis de exceção?
- Um usuário pode acumular perfis? Como as permissões se combinam?
- A permissão é por perfil ou por dado (unidade, centro de custo, região)?
- Quem administra perfis — tela do sistema ou processo externo?
- O que o usuário sem permissão vê: erro, item oculto ou bloqueado?
- Existe perfil apenas de consulta, para auditoria ou gestão?

---

## Regras de negócio
Destinatário típico: área de negócio.

- Toda condição tem o caso contrário definido?
- Toda exceção tem tratamento, ou só está nomeada?
- Cálculos têm unidade, arredondamento e exemplo numérico?
- Prazos são em dias úteis ou corridos? Qual calendário de feriados?
- Quais valores mudam com frequência e deveriam ser parametrizáveis?
- Quem autoriza mudança de regra depois da entrega?

---

## Fluxos
Destinatário típico: negócio, processos.

- Cada ponto de decisão tem a regra escrita?
- Todo fluxo termina em estado final identificado?
- O que acontece quando o responsável de uma etapa está ausente?
- É possível cancelar, reverter ou reabrir? Quem pode, e até quando?
- Existe prazo por etapa? O que acontece quando estoura?
- Há caminho de exceção tratado hoje manualmente que ninguém documentou?

A última pergunta rende mais que as outras cinco juntas em processos que já existem.

---

## Dados
Destinatário típico: negócio, dados.

- Volume atual e crescimento esperado.
- O que é dado obrigatório e o que é opcional.
- Existe dado sensível ou pessoal? Qual a base legal e o prazo de retenção?
- De onde vem cada dado exibido: digitado, importado, calculado, integrado?
- Existe dado preexistente a migrar? Com qual qualidade?
- Quem é o dono de cada base envolvida?

---

## Integrações
Destinatário típico: arquitetura, responsável pelo sistema externo.

- O que acontece quando o outro lado está indisponível.
- Síncrona ou assíncrona; o usuário espera a resposta?
- Existe ambiente de homologação com dado utilizável?
- Quem é o interlocutor do outro lado e qual o prazo de resposta dele?
- O contrato de dados está estável ou muda durante o projeto?
- Há limite de chamadas, janela ou custo por requisição?

---

## Transição e convivência
Destinatário típico: negócio, gestão do projeto.

- O que acontece com o trabalho em andamento na virada.
- Os dois sistemas convivem? Por quanto tempo, e qual é a fonte da verdade nesse período?
- Há necessidade de treinamento ou comunicação aos usuários?
- Existe plano de retorno se a virada falhar?
- Quem opera o sistema depois da entrega e quem atende o usuário?

Esta área é a mais esquecida em projetos que substituem processo existente, e a que mais
gera crise na semana da entrega.

---

## Decisão e governança
Destinatário típico: gestão do projeto.

- Quem decide sobre escopo quando surgir divergência?
- Quem aprova formalmente as entregas?
- Existe comitê ou rito de decisão? Com qual periodicidade?
- Há restrição de prazo com origem externa — regulatória, contratual, sazonal?
- Qual o orçamento ou limite que condiciona decisões técnicas?

Ponto em aberto sem destinatário identificável é, ele mesmo, um ponto em aberto de
governança. Registre assim.

---

## Classificação de criticidade

**Crítica** — bloqueia a etapa seguinte. O trabalho de extração de requisitos não avança
sem a resposta, ou avança produzindo algo que será refeito. Exemplos: escopo ambíguo,
perfil não definido, regra central incompleta.

**Relevante** — não bloqueia, mas gera retrabalho provável. Exemplos: volume desconhecido,
comportamento de exceção não definido em fluxo secundário.

**Menor** — pode ser tratada depois ou com suposição declarada. Exemplos: rótulo de campo,
formato de exibição, ordenação padrão.

Duas regras: criticidade se mede pelo impacto na próxima etapa, não pela importância do
tema no projeto. E ponto crítico que ninguém sabe responder é mais grave do que parece —
registre também a ausência de destinatário.
