# Task 04: Estruturar `src/brands/` e tokens w² Agência

**Fase:** Fase 0 — Setup & Proof of Concept
**Depende de:** Task 02
**Estimativa:** 30min
**Status:** done

---

## Objetivo

Criar a estrutura `src/brands/w2-agencia/` com tokens (cores, fontes, espaçamentos) e assets (logos SVG) importados do brandbook oficial.

## O Que Fazer

1. Criar estrutura:
   ```
   src/brands/w2-agencia/
   ├── tokens.ts
   ├── fonts.ts        # placeholder, será preenchido na Task 05
   ├── assets.ts
   └── logos/          # copiar SVGs
   ```
2. Copiar SVGs de `d:/woigt-studio/brand/assets/logo/` para `src/brands/w2-agencia/logos/`
3. Em `tokens.ts`, exportar objeto com as cores, tipografia e espaçamentos do brand
4. Em `assets.ts`, exportar paths/imports dos SVGs como strings base64 ou imports
5. Atualizar `src/app/globals.css` para incluir os tokens como CSS variables (`--w2-yellow`, etc.)

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/brands/w2-agencia/tokens.ts` — criar
- `d:/w2-posts-studio/src/brands/w2-agencia/fonts.ts` — criar (placeholder)
- `d:/w2-posts-studio/src/brands/w2-agencia/assets.ts` — criar
- `d:/w2-posts-studio/src/brands/w2-agencia/logos/*.svg` — copiar de woigt-studio
- `d:/w2-posts-studio/src/app/globals.css` — adicionar variables

## Detalhes Técnicos

**Conteúdo de `tokens.ts`:**

```ts
export const w2Tokens = {
  colors: {
    yellow: '#F5C100',      // Amarelo Elétrico — primary background
    magenta: '#E01A5A',     // Magenta — accent, ², CTAs
    black: '#0D0D0D',       // Preto Total — text, borders
    graphite: '#1A1A1A',    // Grafite — dark surfaces
    white: '#FFFFFF',       // Branco — light backgrounds
  },
  fonts: {
    display: 'Barlow Condensed',  // Black, Italic — headlines
    body: 'Inter',                 // a confirmar no brandbook — corpo
  },
  spacing: {
    sm: 16,
    md: 24,
    lg: 48,
    xl: 96,
  },
  radii: {
    sm: 8,
    md: 16,
    lg: 32,
  },
} as const;

export type W2Tokens = typeof w2Tokens;
```

**Conteúdo de `assets.ts`:** importar SVGs como string raw (para uso em JSX inline ou data URI no Satori).

Confirmar fonte de corpo lendo `d:/woigt-studio/design-handoff-claude.md` antes de cravar `body`. Se não houver fonte de corpo definida, manter Inter como fallback (declarar como decisão no commit).

## Verificação

- [ ] `src/brands/w2-agencia/tokens.ts` exporta `w2Tokens` com tipagem
- [ ] `src/brands/w2-agencia/logos/` contém todos os 10 SVGs do brand
- [ ] `src/brands/w2-agencia/assets.ts` exporta pelo menos `logoPrimaryDark`, `logoPrimaryLight`, `logoSymbolColor`
- [ ] `globals.css` define `--w2-yellow`, `--w2-magenta`, `--w2-black`, `--w2-graphite`, `--w2-white`
- [ ] `npm run build` completa sem erros de import
