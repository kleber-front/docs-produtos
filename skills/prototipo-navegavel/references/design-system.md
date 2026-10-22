# Fundação do Design System

Não existe Design System na organização ainda. O primeiro projeto do fluxo cria a fundação; os
seguintes reutilizam e evoluem. O registro fica em `design-system.md` (na pasta do fluxo,
compartilhado entre projetos quando possível).

## Ordem

1. **Tokens** em `src/design-system/tokens.css`, como variáveis CSS do shadcn:
   `--background`, `--foreground`, `--primary`, `--primary-foreground`, `--secondary`,
   `--muted`, `--accent`, `--destructive`, `--border`, `--input`, `--ring`, `--radius`, mais
   tokens de status (`--status-aberto`, `--status-aprovado`, `--status-andamento`,
   `--status-cancelado`, `--status-concluido`) e escala de espaçamento.
   Cor da marca: use a identidade do Grupo Plaenge se fornecida; senão, neutro com primária
   provisória marcada [pendente] em `design-system.md`.
2. **Tema claro e escuro** desde o início, com contraste AA verificado.
3. **Componentes base** — os do shadcn, sem alteração de API.
4. **Composições do DS** — componentes de padrão de tela que se repetem entre projetos:
   `CabecalhoApp`, `BarraTitulo`, `FiltroBar`, `CartaoRegistro`, `StatusTrilha`,
   `GrupoFormulario`, `CampoFormulario`, `RodapeAcoes`, `EstadoVazio`, `EstadoErro`.
5. **Padrões** — regras de uso: quando cartão vs tabela, quando modal vs página, mensagens
   padrão (salvo com sucesso, campo obrigatório, sem permissão), formato de data e moeda.

## Regras

- Nenhuma cor, espaço ou raio hardcoded em tela; só tokens e classes Tailwind ligadas a eles.
- Componente novo só entra no DS se for usado em mais de uma tela ou tiver chance clara de
  reaproveitamento; senão fica em `dominios/<dominio>/componentes`.
- Toda alteração no DS gera linha no histórico de `design-system.md`.

## Formato de `design-system.md`

```markdown
# Design System — Grupo Plaenge (fundação)
Versão: 0.x | Atualizado em: dd/mm/aaaa | Projetos que usam: <lista>

## Tokens
| Token | Claro | Escuro | Uso |
## Componentes base (shadcn)
| Componente | Variantes usadas | Observação |
## Composições
| Componente | Props principais | Estados | Onde é usado (TL) |
## Padrões
| Padrão | Regra | Exemplo |
## Pendências
## Histórico
| Versão | Data | Projeto | Alteração |
```
