# Stack e estrutura do protótipo

## Stack

Vite + React + TypeScript · Tailwind CSS · shadcn/ui · React Router · lucide-react (ícones) ·
dados mock em memória. Sem backend, sem chamadas externas.

## Setup

```bash
npm create vite@latest prototipo -- --template react-ts
cd prototipo
npm install
npm install react-router-dom lucide-react
npm install -D tailwindcss @tailwindcss/vite
npx shadcn@latest init          # base color: neutral; CSS variables: sim
npx shadcn@latest add button input label select card table badge dialog alert-dialog \
  dropdown-menu tabs breadcrumb collapsible calendar popover sonner skeleton separator
```

Verifique as versões instaladas; se um comando mudou de sintaxe, consulte a documentação
oficial do shadcn e do Tailwind antes de improvisar.

## Estrutura por domínio

Organize por domínio de negócio, não por tipo de arquivo. A estrutura é pensada para ser
reaproveitada pelo frontend real.

```
src/
  app/
    router.tsx            # rotas; uma por TL
    layout/AppShell.tsx   # cabeçalho padrão, área de conteúdo
    perfil/PerfilContext.tsx  # perfil simulado ativo
  design-system/
    tokens.css            # variáveis (cores, raio, espaço, tipografia)
    componentes/          # composições reutilizáveis (CabecalhoApp, BarraTitulo, FiltroBar,
                          # CartaoRegistro, StatusTrilha, GrupoFormulario, RodapeAcoes, EstadoVazio...)
  dominios/
    <dominio>/
      telas/              # TL-001-ConsultaX.tsx, TL-002-CadastroX.tsx
      componentes/
      mocks/              # dados.ts, servico.ts (simula latência e erro)
      tipos.ts
  lib/
    formatadores.ts       # data DD/MM/AAAA, moeda BRL
```

## Mocks

- Tipos em `tipos.ts` com os campos do contexto; nomes de campo no vocabulário do glossário.
- `servico.ts` expõe funções assíncronas (`listar`, `obter`, `salvar`, `aprovar`...) com
  latência de 300–800 ms e um parâmetro para forçar erro — permite mostrar carregando e erro.
- Integrações citadas no contexto (ex.: lista de regionais) viram funções mock com o nome da
  integração (`apiListarRegionais`), para a documentação ligar tela ↔ integração.
- 8 a 20 registros por lista, cobrindo todos os status.

## Perfis simulados

Seletor de perfil no cabeçalho (só no protótipo, sinalizado como "Simulação"). Cada perfil do
contexto (seção 10) é uma opção. Visibilidade de botões e campos responde ao perfil ativo, para
validar a matriz de permissões com o negócio.

## Identificação das telas

Cada tela tem o TL-ID num atributo `data-tl="TL-002"` no contêiner principal e, em modo
desenvolvimento, um selo discreto no canto com o TL-ID. Facilita a validação ("na TL-002, o
campo Data…") e a captura.

## Entrega

```bash
npm run build                       # precisa passar sem erro
cd .. && zip -r prototipo.zip prototipo -x "prototipo/node_modules/*" "prototipo/dist/*"
```

Para visualização sem instalar nada, publique o build também como página (Artifact) quando a
sessão permitir, deixando claro que é protótipo com dados fictícios.
