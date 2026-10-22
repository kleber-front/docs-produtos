# Captura de telas

As capturas entram na seção "Protótipo" de cada funcionalidade no documento ADS. Gere depois do
build passar.

## Como

1. `npm run build && npx vite preview --port 4173 &`
2. Script Playwright (Chromium já instalado no ambiente; não rode `playwright install`):

```js
// scripts/capturar.mjs
import { chromium } from 'playwright';
const telas = [
  { id: 'TL-001', estado: 'com-dados', rota: '/solicitacoes' },
  { id: 'TL-001', estado: 'vazio',     rota: '/solicitacoes?mock=vazio' },
  { id: 'TL-002', estado: 'inclusao',  rota: '/solicitacoes/nova' },
  { id: 'TL-002', estado: 'edicao',    rota: '/solicitacoes/12?perfil=gestor' },
];
const browser = await chromium.launch();
const page = await browser.newPage({ viewport: { width: 1440, height: 900 }, deviceScaleFactor: 2 });
for (const t of telas) {
  await page.goto(`http://localhost:4173${t.rota}`);
  await page.waitForLoadState('networkidle');
  await page.waitForTimeout(900); // latência dos mocks
  await page.screenshot({ path: `../03-capturas/${t.id}-${t.estado}.png`, fullPage: true });
}
await browser.close();
```

3. Para estados (vazio, erro, perfil), aceite parâmetros de URL só no protótipo (`?mock=vazio`,
   `?mock=erro`, `?perfil=gestor`) — documente-os no README do protótipo.
4. Capture ao menos: cada tela no estado principal; cadastro em inclusão e edição; uma captura
   por perfil quando a tela muda por perfil.
5. Abra 2 ou 3 capturas com Read para conferir que renderizaram (sem tela branca, sem erro).

Use `BrowserRouter` com fallback de rota no preview; se o preview não servir rotas profundas,
use `HashRouter` só para a captura.
