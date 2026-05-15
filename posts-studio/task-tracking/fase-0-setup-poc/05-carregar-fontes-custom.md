# Task 05: Carregar fontes custom (Barlow Condensed)

**Fase:** Fase 0 — Setup & Proof of Concept
**Depende de:** Task 04
**Estimativa:** 30min
**Status:** done

---

## Objetivo

Baixar e configurar as fontes do brand w² (Barlow Condensed Black, Italic) tanto para o browser (live preview) quanto para o Satori server-side (render PNG).

## O Que Fazer

1. Baixar arquivos `.ttf` de Barlow Condensed do Google Fonts:
   - `BarlowCondensed-Black.ttf`
   - `BarlowCondensed-BlackItalic.ttf`
   - `BarlowCondensed-Regular.ttf` (fallback)
2. Salvar em `src/brands/w2-agencia/fonts/`
3. Criar `src/brands/w2-agencia/fonts.ts` que:
   - Para o browser: usa `next/font/local` ou `next/font/google` para Barlow Condensed
   - Para o Satori: exporta função `loadW2Fonts()` que retorna `ArrayBuffer[]` lendo os arquivos via `fs.readFile`
4. Aplicar a fonte via classe Tailwind / className no `layout.tsx`
5. Se houver fonte de corpo definida no brandbook (Inter ou similar), adicionar também

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/brands/w2-agencia/fonts/BarlowCondensed-*.ttf` — baixar
- `d:/w2-posts-studio/src/brands/w2-agencia/fonts.ts` — criar com loaders
- `d:/w2-posts-studio/src/app/layout.tsx` — aplicar fonte
- `d:/w2-posts-studio/src/app/globals.css` — variável `--font-display`

## Detalhes Técnicos

**Padrão para Satori (loadW2Fonts):**

```ts
import { readFile } from 'fs/promises';
import path from 'path';

export async function loadW2Fonts() {
  const fontsDir = path.join(process.cwd(), 'src/brands/w2-agencia/fonts');
  const [black, blackItalic] = await Promise.all([
    readFile(path.join(fontsDir, 'BarlowCondensed-Black.ttf')),
    readFile(path.join(fontsDir, 'BarlowCondensed-BlackItalic.ttf')),
  ]);
  return [
    { name: 'Barlow Condensed', data: black, weight: 900, style: 'normal' as const },
    { name: 'Barlow Condensed', data: blackItalic, weight: 900, style: 'italic' as const },
  ];
}
```

**Padrão para browser (next/font):**

```ts
import { Barlow_Condensed } from 'next/font/google';

export const barlowCondensed = Barlow_Condensed({
  subsets: ['latin'],
  weight: ['400', '900'],
  style: ['normal', 'italic'],
  variable: '--font-w2-display',
});
```

**Importante:** o nome usado no JSX (`fontFamily: 'Barlow Condensed'`) deve bater EXATAMENTE com o `name` registrado no Satori, senão a fonte não aplica.

## Verificação

- [ ] Arquivos `.ttf` existem em `src/brands/w2-agencia/fonts/`
- [ ] `fonts.ts` exporta tanto a fonte do browser quanto o `loadW2Fonts()` para Satori
- [ ] Aplicar a fonte numa div de teste em `page.tsx` — texto renderiza em Barlow Condensed
- [ ] `loadW2Fonts()` executa sem erro em ambiente Node (testar com pequeno script ou no route handler)
- [ ] Build production completa sem erros
