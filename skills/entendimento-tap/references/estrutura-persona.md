# Estrutura das Personas

O `01-persona.md` reúne as personas do projeto: quem executa, aprova ou acompanha o processo,
com a síntese do perfil em 10 itens e a jornada de trabalho de hoje. Nasce na etapa 1, é
atualizado na etapa 2 com o que a entrevista de cada persona revelou e é consulta do protótipo
e dos requisitos.

Como o Contexto do Projeto, é um **arquivo único e incremental, sem número de versão**: cada
etapa altera no lugar só as personas e os itens afetados, preserva o resto e acrescenta uma
linha no Registro de alterações. Regras em "Contexto do Projeto e Personas: arquivos
incrementais", nas convenções.

As personas ficam só aqui. O contexto lista os perfis (seção 10, com a coluna Persona apontando
para este arquivo) e consolida por tema o que as personas relatam — dores e jornada no cenário
atual (§5), local de trabalho e familiaridade nas premissas (§7), decisões nas regras (§12),
sistemas e dados nas integrações (§14).

## Origem das personas

- **Com MD de Persona:** uma persona por persona do MD (um `# Persona — <papel>` em cada
  arquivo), com origem `FON-00x, item n`.
- **Sem MD de Persona:** uma persona por perfil citado na TAP, só com o que a TAP diz dele, com
  origem. Item sem informação fica `[pendente] — ver LAC-00x`. A persona é identificada como
  "a partir da TAP" e a entrevista em profundidade é quem a completa.

Relato da persona é fato do as-is declarado, não regra, decisão nem requisito. A persona é
descrita pelo papel; o nome de quem preencheu o MD fica só no inventário de fontes do contexto.

## Formato

```markdown
# Personas — <Projeto>

Projeto: <nome> | Artefato: Personas
Status: Rascunho | Atualizado em: dd/mm/aaaa

> Diagnóstico: <n> personas (<n> do MD de Persona, <n> a partir da TAP) · <n> itens [pendente].

## Registro de alterações
| Data | Etapa | Personas | O que mudou |
|------|-------|----------|-------------|
| dd/mm/aaaa | 1 Entendimento da TAP | todas | Criação a partir do MD de Persona (FON-002) |
Uma linha por atualização, a mais recente por último; nunca "ajustes gerais".

## Visão geral
| Persona | Perfil (contexto §10) | Origem | Onde trabalha | Familiaridade (1 a 5) | Entrevista no roteiro |
|---------|-----------------------|--------|---------------|-----------------------|-----------------------|
Origem: MD de Persona (FON-00x) | a partir da TAP (FON-001).

## <Papel>
Origem: FON-00x (MD de Persona) | a partir da TAP (FON-001)

### Síntese do perfil
| Item | Síntese | Origem |
|------|---------|--------|
| 1. Função e setor | | FON-00x, item 1 |
| 2. Objetivo principal da função | | |
| 3. Atividades recorrentes e tempo | | |
| 4. Sistemas e ferramentas | | |
| 5. Informações e de onde vêm | | |
| 6. Decisões e aprovações | | |
| 7. Principais dores (exemplo recente) | | |
| 8. Áreas e papéis com que interage | | |
| 9. Onde trabalha | | |
| 10. Familiaridade com tecnologia (1 a 5) | | |

### Jornada atual (as-is)
| # | Etapa | O que faz | Sistema ou ferramenta | Informação | Tempo | Dor | Com quem | Origem |
|---|-------|-----------|-----------------------|------------|-------|-----|----------|--------|
Jornada desconhecida → [pendente] — ver LAC-00x.

### Pendências da persona
| Item | O que falta | LAC-/Q-/E- |
|------|-------------|------------|
Item ou célula em branco, "não sei" ou vago aparece aqui e como [pendente] na tabela.
```

## Atualização na etapa 2

- Aplique o que a entrevista confirmou, corrigiu ou completou no item e na etapa da jornada
  correspondentes, com origem "Reunião dd/mm, fala de <papel>". Item corrigido mostra o valor
  novo; a divergência com o relato anterior, se mudar algo, vai para o contexto (§16).
- Item que segue sem resposta permanece `[pendente]`, com a pendência atualizada.
- Persona nova revelada na reunião ganha seção própria e linha na Visão geral; persona
  descartada fica com a marca *Cancelada* e o motivo — não some.
- Achado de entrevista não vira regra nem decisão aqui: regra vai ao contexto como R-xx
  [inferido] com pergunta; decisão só com DEC- registrada.
- Status: Validado quando o gate 2 é atendido e o usuário confirma; senão, Rascunho.
