# Checklists de gate

Verifique lendo o artefato. Cada item é sim/não. Um "não" em item crítico = gate não atendido.

## Gate 1 — Entendimento da TAP

- [ ] Todas as fontes inventariadas com FON-ID e status (crítico)
- [ ] Contexto tem todas as seções da estrutura, com seções sem informação marcadas como lacuna (crítico)
- [ ] Fora de escopo declarado, ou registrado como lacuna crítica (crítico)
- [ ] Benchmark feito com ao menos 3 alternativas ou justificativa de por que há menos, cada uma com link e data de consulta (crítico)
- [ ] Benchmark não recomenda decisão; apresenta opções e critérios
- [ ] Toda lacuna crítica tem ao menos uma pergunta Q- associada (crítico)
- [ ] Toda pergunta tem destinatário
- [ ] Roteiro da reunião gerado, com participantes sugeridos e ordem por tema

## Gate 2 — Reunião de entendimento

- [ ] Toda Q- do roteiro tem situação: respondida, parcial, não respondida, adiada (crítico)
- [ ] Decisões novas registradas como DEC- com responsável (crítico)
- [ ] Contexto reemitido inteiro como v1.0 (não adendo), com histórico (crítico)
- [ ] Escopo e fora de escopo confirmados pelo usuário (crítico)
- [ ] Checklist de prontidão para protótipo: atores/perfis, fluxo principal, funcionalidades candidatas a tela, dados principais por tela (crítico)
- [ ] Pontos ainda abertos têm destinatário e prazo, se citado

## Gate 3 — Protótipo

- [ ] Toda tela tem TL-ID e aponta para funcionalidade/regra do contexto (crítico)
- [ ] Nenhuma tela ou campo nasceu sem origem; o que foi deduzido está marcado [inferido]
- [ ] Estados vazio, carregando, erro e sem permissão tratados ou marcados como pendência
- [ ] Protótipo roda (build sem erro) e as capturas de tela foram geradas (crítico)
- [ ] Telas enviadas ao Figma com link registrado no mapa de telas e no `estado.md` (ou pendência declarada se o conector estiver indisponível)
- [ ] Validação com negócio registrada: quem, quando, o que mudou (crítico)
- [ ] Mudanças de regra vindas da validação foram devolvidas ao contexto

## Gate 4 — Requisitos

- [ ] Todo RF tem ator, origem e TL de referência quando houver interface (crítico)
- [ ] Todo RF com status OK tem cenário de teste CT- (crítico)
- [ ] Todo RF não OK está em pendência com destinatário (crítico)
- [ ] Toda RN tem exceção definida ou status Incompleto
- [ ] RNF com métrica, ou em pendência
- [ ] Requisitos técnicos cobrem: arquitetura/stack, integrações, modelo de dados, infra e segurança — cada área com conteúdo ou pendência (crítico)
- [ ] Decisões técnicas propostas (DT-) marcadas [sugerido] até aprovação da TI

## Gate 5 — Documentação

- [ ] Documento gerado a partir do modelo ADS, preservando formatação e ordem das seções (crítico)
- [ ] Controle de versões preenchido com autor, versão, data e resumo real (crítico)
- [ ] Uma subseção por funcionalidade em "Requisitos de Software", com protótipo e requisitos por estrutura de tela
- [ ] Nenhum texto de instrução do modelo ([entre colchetes, em itálico]) esquecido no documento (crítico)
- [ ] Nenhuma seção preenchida sem fonte; seções sem fonte marcadas [pendente]
- [ ] IDs preservados (RF, RN, TL, INT, CT) e consistentes com 04-requisitos
