# Task 02: Template feed-tip (3 variantes)

**Fase:** Fase 2 — Restante dos Templates
**Depende de:** Fase 2 Task 01 (não estritamente, mas ordem natural)
**Estimativa:** 2h
**Status:** pending

---

## Objetivo

Implementar template `feed-tip` (dica/lista numerada de 3 itens) com 3 variantes, no formato 4:5 (1080×1350) — formato Instagram preferido para feed.

## O Que Fazer

1. Criar `src/brands/w2-agencia/templates/feed-tip/` com `schema.ts`, `meta.ts`, `variants.tsx`, `index.ts`
2. Schema: título (max 60), 3 itens de lista (max 50 cada), CTA (max 40), variant A/B/C, colorVariant
3. Meta: aspect ratio 4:5, dimensões 1080×1350
4. 3 variantes JSX:
   - **A** — Título topo + lista numerada vertical + CTA rodapé
   - **B** — Título lateral esquerdo (rotation 0 ou vertical-ish) + lista direita
   - **C** — Título centro + lista em 2 colunas (mas só 3 itens — 2+1 ou layout adaptativo)
5. Numeração visual destacada (números grandes em magenta ou amarelo dependendo da paleta)
6. Adicionar ao `template-registry.ts`
7. Testar via página existente `/studio/w2-agencia/feed-tip`

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-tip/schema.ts`
- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-tip/meta.ts`
- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-tip/variants.tsx`
- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-tip/index.ts`
- `d:/w2-posts-studio/src/lib/template-registry.ts` — adicionar entry feed-tip

## Detalhes Técnicos

**Schema:**

```ts
export const feedTipSchema = z.object({
  title: z.string().min(1).max(60),
  items: z.tuple([
    z.string().min(1).max(50),
    z.string().min(1).max(50),
    z.string().min(1).max(50),
  ]),
  cta: z.string().max(40).optional(),
  variant: z.enum(['A', 'B', 'C']),
  colorVariant: z.enum(['yellow', 'magenta', 'black']),
});
```

**Fields para o studio-form:**
```ts
fields: [
  { name: 'title', label: 'Título', maxLength: 60 },
  { name: 'items.0', label: 'Item 1', maxLength: 50 },
  { name: 'items.1', label: 'Item 2', maxLength: 50 },
  { name: 'items.2', label: 'Item 3', maxLength: 50 },
  { name: 'cta', label: 'CTA (opcional)', maxLength: 40, optional: true },
]
```

**Nota:** `studio-form` precisa suportar paths aninhados (`items.0`). Se ainda não suporta, ampliar na implementação desta task (caso simples — React Hook Form lida nativamente).

**Tipografia:**
- Título: Barlow Condensed Black, 64-72px, letterSpacing -1
- Itens: Barlow Condensed Bold ou Regular, 36-44px
- Números: Barlow Condensed Black, 80px+, cor accent
- CTA: Barlow Condensed Black, 28px

## Verificação

- [ ] Acessar `/studio/w2-agencia/feed-tip` carrega o template
- [ ] Os 4 campos de texto (título + 3 itens) aparecem no form com char counters
- [ ] CTA é opcional (não bloqueia export se vazio)
- [ ] Mudar variante muda layout corretamente
- [ ] Exportar PNG nas 3 variantes × 3 cores = 9 combinações funcionam visualmente
- [ ] Numeração 1, 2, 3 aparece destacada e legível
- [ ] PNG em 1080×1350 (proporção 4:5)
