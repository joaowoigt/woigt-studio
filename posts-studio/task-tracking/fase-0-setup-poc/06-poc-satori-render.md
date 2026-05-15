# Task 06: PoC Satori `/api/render`

**Fase:** Fase 0 — Setup & Proof of Concept
**Depende de:** Task 04, Task 05
**Estimativa:** 1h
**Status:** done

---

## Objetivo

Implementar a rota `/api/render` usando Satori + Resvg para converter um JSX simples (com fonte e cor do brand w²) em PNG retornado como response. É a prova-de-conceito que destrava todo o projeto.

## O Que Fazer

1. Instalar dependências:
   ```
   npm install satori @resvg/resvg-js
   ```
2. Criar `src/lib/render.ts` com função `renderToPng(jsx, options)` que:
   - Chama `satori(jsx, { width, height, fonts })` → retorna SVG string
   - Passa SVG para `Resvg(svg).render().asPng()` → retorna Buffer
3. Criar `src/app/api/render/route.ts` com handler GET que:
   - Define um JSX hardcoded de teste: div com fundo `#F5C100` (amarelo w²), texto "VOCÊ EXISTE." em Barlow Condensed Black, cor `#0D0D0D`, mais "²" em magenta `#E01A5A`
   - Carrega fontes via `loadW2Fonts()`
   - Chama `renderToPng()`
   - Retorna `new Response(buffer, { headers: { 'Content-Type': 'image/png' } })`
4. Testar localmente: abrir `http://localhost:3000/api/render` no browser

## Arquivos Envolvidos

- `d:/w2-posts-studio/package.json` — adicionar `satori`, `@resvg/resvg-js`
- `d:/w2-posts-studio/src/lib/render.ts` — criar
- `d:/w2-posts-studio/src/app/api/render/route.ts` — criar

## Detalhes Técnicos

**Estrutura de `src/lib/render.ts`:**

```ts
import satori from 'satori';
import { Resvg } from '@resvg/resvg-js';

export type RenderOptions = {
  width: number;
  height: number;
  fonts: Array<{
    name: string;
    data: Buffer | ArrayBuffer;
    weight: 400 | 700 | 900;
    style: 'normal' | 'italic';
  }>;
};

export async function renderToPng(
  jsx: React.ReactNode,
  options: RenderOptions
): Promise<Buffer> {
  const svg = await satori(jsx, {
    width: options.width,
    height: options.height,
    fonts: options.fonts,
  });
  const png = new Resvg(svg).render().asPng();
  return png;
}
```

**Importante / Limitações do Satori:**
- Suporta apenas flexbox (sem grid CSS)
- Sem `box-shadow` complexo, `filter`, ou animations
- `position: absolute` funciona
- Imagens via `<img src={dataUri | url}>` (data URIs preferíveis no PoC)
- `fontFamily` deve bater exatamente com `name` registrado em `fonts`

**Conteúdo de teste sugerido (route.ts):**

```tsx
const jsx = (
  <div style={{
    width: '100%',
    height: '100%',
    background: '#F5C100',
    display: 'flex',
    alignItems: 'center',
    justifyContent: 'center',
    fontFamily: 'Barlow Condensed',
  }}>
    <span style={{ fontSize: 120, color: '#0D0D0D', fontWeight: 900 }}>
      VOCÊ EXISTE.
    </span>
    <span style={{ fontSize: 60, color: '#E01A5A', fontWeight: 900, fontStyle: 'italic' }}>
      ²
    </span>
  </div>
);
```

Render em 1080×1080.

## Verificação

- [x] `satori` e `@resvg/resvg-js` instalados
- [x] Abrir `http://localhost:3001/api/render` retorna imagem PNG no browser
- [x] PNG tem fundo amarelo `#F5C100` (visualmente confirmado)
- [x] Texto "VOCÊ EXISTE." aparece em Barlow Condensed Black, cor preta
- [x] "w² AGÊNCIA" aparece em magenta `#E01A5A`, italic (adaptado do mock original)
- [x] Tamanho da imagem é 1080×1080 px (confirmado via cabeçalho PNG)

> **Decisão arquitetural:** `@resvg/resvg-js` tem binding nativo e precisa de
> `serverExternalPackages: ['@resvg/resvg-js']` no `next.config.ts` para evitar
> erro de bundling. `loadW2Fonts()` usa fetch em runtime (padrão Vercel OG) em vez
> de `fs.readFile`, evitando TTFs no repo e simplificando o deploy.

---

## Como Testar (manual)

```bash
cd D:/w2-posts-studio
npm run dev -- --port 3001
```

1. Abrir http://localhost:3001/api/render no browser
2. Deve abrir uma imagem 1080×1080 com fundo amarelo
3. Texto "VOCÊ EXISTE." em preto bold, "w² AGÊNCIA" em magenta italic
4. Salvar a imagem e verificar propriedades: deve ser 1080×1080 PNG

**Verificação de dimensões via curl:**
```bash
curl -s -o test.png -w "%{http_code} %{size_download}bytes" http://localhost:3001/api/render
# esperado: 200 ~19000bytes
```
