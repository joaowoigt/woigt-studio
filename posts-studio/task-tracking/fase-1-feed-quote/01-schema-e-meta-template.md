# Task 01: Schema Zod + meta do template feed-quote

**Fase:** Fase 1 — Primeiro Template feed-quote
**Depende de:** Fase 0 completa
**Estimativa:** 30min
**Status:** done

---

## Objetivo

Definir o "contrato" do template `feed-quote`: quais campos o usuário preenche, com que limites e validações, mais metadados (aspect ratio, descrição, variantes disponíveis).

## O Que Fazer

1. Criar pasta `src/brands/w2-agencia/templates/feed-quote/`
2. Criar `schema.ts` com Zod schema dos inputs do template
3. Criar `meta.ts` com metadados (nome, descrição, aspect ratio, dimensões, lista de variantes, lista de paletas de cor)
4. Criar `index.ts` que re-exporta tudo da pasta

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-quote/schema.ts` — criar
- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-quote/meta.ts` — criar
- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-quote/index.ts` — criar

## Detalhes Técnicos

**`schema.ts`:**

```ts
import { z } from 'zod';

export const feedQuoteSchema = z.object({
  quote: z.string().min(1, 'Obrigatório').max(120, 'Máximo 120 caracteres'),
  signature: z.string().max(30, 'Máximo 30 caracteres').optional(),
  variant: z.enum(['A', 'B', 'C']),
  colorVariant: z.enum(['yellow', 'magenta', 'black']),
});

export type FeedQuoteInput = z.infer<typeof feedQuoteSchema>;
```

**`meta.ts`:**

```ts
export const feedQuoteMeta = {
  id: 'feed-quote',
  name: 'Quote / Insight',
  description: 'Frase de posicionamento ou insight de marca',
  aspectRatio: '1:1' as const,
  width: 1080,
  height: 1080,
  variants: [
    { id: 'A', label: 'Centro + fundo cor + logo rodapé' },
    { id: 'B', label: 'Topo + faixa accent + assinatura' },
    { id: 'C', label: 'Centro + textura + logo discreto' },
  ],
  colorVariants: [
    { id: 'yellow', label: 'Amarelo', preview: '#F5C100' },
    { id: 'magenta', label: 'Magenta', preview: '#E01A5A' },
    { id: 'black', label: 'Preto', preview: '#0D0D0D' },
  ],
} as const;
```

**`index.ts`:**

```ts
export * from './schema';
export * from './meta';
export * from './variants'; // será criado na Task 02
```

## Verificação

- [ ] `schema.ts` exporta `feedQuoteSchema` e tipo `FeedQuoteInput`
- [ ] `meta.ts` exporta `feedQuoteMeta` com aspect ratio, dimensões, 3 variantes e 3 paletas
- [ ] Importar `feedQuoteSchema` em outro arquivo e fazer `.parse({...})` valida corretamente
- [ ] Tentar quote >120 chars retorna erro de validação
- [ ] TypeScript: `FeedQuoteInput` é inferido corretamente
