# Envio do protótipo ao Figma

Depois do build e das capturas, as telas do protótipo React são enviadas para um arquivo Figma
(code-to-design), para que design e negócio comentem e refinem no Figma. O protótipo React
continua sendo a fonte da verdade: o Figma é espelho para revisão, não origem de regra.

## Pré-requisitos

- Conector do Figma ativo na sessão (ferramentas do servidor MCP `figma`). Se não estiver
  disponível, registre "Envio ao Figma: pendente — conector indisponível" no mapa de telas e
  siga; não bloqueia o gate.
- Carregue as skills do plugin Figma quando estiverem listadas: `figma:figma-generate-design`
  (obrigatória para montar telas) e `figma:figma-use` (obrigatória antes de qualquer
  `use_figma`). Sem o plugin, use as skills servidas pelo próprio conector
  (`get_figma_skill` / recursos `skill://figma/...`).

## Destino

- Se o usuário ou o `estado.md` informar um link de arquivo Figma do projeto, use-o.
- Caso contrário, crie um arquivo novo (`figma:figma-create-new-file` antes de
  `create_new_file`) com o nome `<Projeto> — Protótipo vX.Y`. Pergunte o time/projeto do Figma
  só se a ferramenta exigir.
- Registre o link no `03-mapa-telas.md` (cabeçalho) e no `estado.md`.

## Como

1. **Procure o Design System** com `search_design_system` antes de criar qualquer coisa:
   reutilize componentes, variáveis e estilos existentes da biblioteca Plaenge. Nunca recrie
   componente que já existe na biblioteca.
2. **Uma página do Figma por grupo funcional**, um frame por tela e estado principal, nomeado
   `TL-xxx — <nome da tela> — <estado>` (mesmo nome das capturas). Viewport 1440 × 900.
3. **Para cada tela**, com o preview rodando (`npx vite preview --port 4173`):
   - capture a referência visual da rota (generate_figma_design, quando disponível);
   - monte a tela com `use_figma` a partir dos componentes do Design System, seção por seção,
     seguindo os blocos do modelo ADS (Cabeçalho, Barra de títulos, Filtros, Resultado,
     Rodapé);
   - compare com a referência, ajuste e apague o frame de referência.
4. **Marque pendências** no próprio frame: campo ou estado `[pendente]` recebe uma anotação
   visível com o ID (PEN-/Q-) — igual ao protótipo React.
5. **Confira** com `get_screenshot` de 2 ou 3 frames que a tela montou corretamente.

## Regras

- Não crie no Figma tela, campo ou estado que não exista no protótipo React.
- Ajuste feito no Figma durante a revisão volta para o React (e, se mudar regra, para o
  contexto — etapa 2). O mapa de telas registra a divergência até ser resolvida.
- Mock com dados fictícios, os mesmos do protótipo; nunca dados reais de pessoas.
- Textos em português do Brasil, datas DD/MM/AAAA, moeda BRL.

## Saída

No `03-mapa-telas.md`, cabeçalho:

```markdown
Figma: <link do arquivo> · enviado em DD/MM/AAAA · versão do protótipo vX.Y
```

E, em cada tela, a linha `Figma: <link do frame>` junto das capturas.
