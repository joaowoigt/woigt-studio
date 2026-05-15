# Task 02: Refactor para tokens via prop/context

**Fase:** Fase 4 — Multi-Brand Prep
**Depende de:** Fase 4 Task 01
**Estimativa:** 1h30
**Status:** pending

---

## Objetivo

Aplicar os refactors identificados na auditoria para que adicionar um novo brand exija APENAS criar `src/brands/[novo-brand]/` + entrada no registry, sem tocar em código compartilhado.

## O Que Fazer

1. Refatorar `loadW2Fonts()` → `loadBrandFonts(brandId)` que despacha para o loader correto
2. Refatorar `template-registry.ts` para incluir referência ao font loader do brand
3. Em `api/render/route.ts`, chamar `loadBrandFonts(body.brand)` ao invés de hardcoded
4. Mover qualquer config `--w2-*` específica do `globals.css` para componente scoped (`<BrandProvider>` que injeta CSS variables só no escopo da página)
5. Garantir que templates JSX consomem tokens via prop (`tokens`) ou via lookup no registry — não via import direto fixo
6. Atualizar tipos TS para refletir o novo formato

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/lib/load-brand-fonts.ts` — criar
- `d:/w2-posts-studio/src/lib/template-registry.ts` — adicionar `fontLoader` por brand
- `d:/w2-posts-studio/src/app/api/render/route.ts` — usar loader dinâmico
- `d:/w2-posts-studio/src/components/brand-provider.tsx` — criar (opcional)
- Templates de cada brand — confirmar que consomem tokens via `tokens` prop ou import scoped

## Detalhes Técnicos

**Loader dinâmico:**

```ts
import { loadW2Fonts } from '@/brands/w2-agencia/fonts';
import { loadSplitpostFonts } from '@/brands/splitpost/fonts';

const fontLoaders = {
  'w2-agencia': loadW2Fonts,
  'splitpost': loadSplitpostFonts,
} as const;

export async function loadBrandFonts(brandId: string) {
  const loader = fontLoaders[brandId as keyof typeof fontLoaders];
  if (!loader) throw new Error(`Font loader não encontrado para brand: ${brandId}`);
  return loader();
}
```

**Atualizar registry:**

```ts
export const templateRegistry = {
  'w2-agencia': {
    brand: w2AgenciaBrand,    // { tokens, fonts, assets }
    templates: { 'feed-quote': {...}, ... },
  },
  // splitpost será adicionado na Task 03
} as const;
```

## Verificação

- [ ] Todos os refactors da auditoria aplicados
- [ ] Adicionar um brand stub (`src/brands/test-brand/`) com tokens dummy não requer modificar nada fora dessa pasta + 2 entradas (`fontLoaders` + `templateRegistry`)
- [ ] Posts existentes de w² continuam funcionando idênticos
- [ ] `npm run build` passa sem erros
