# Task 05: Landing `/studio/` lista brands

**Fase:** Fase 3 — UX & Polish
**Depende de:** Fase 2 Task 06
**Estimativa:** 30min
**Status:** pending

---

## Objetivo

Criar página raiz `/studio/` que lista os brands disponíveis. No MVP só w² está disponível, mas a estrutura já fica pronta para Splitpost (Fase 4) e clientes futuros.

## O Que Fazer

1. Criar `src/app/studio/page.tsx`
2. Buscar lista de brands do `templateRegistry`
3. Layout: cards com logo do brand + nome + descrição + número de templates
4. Clicar navega para `/studio/[brand]/`
5. Header: "Posts Studio — w² Agência" (com logo símbolo)
6. Footer discreto: "Ferramenta interna w² Agência · build [git sha curto]"

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/app/studio/page.tsx` — criar
- `d:/w2-posts-studio/src/app/page.tsx` — redirecionar `/` para `/studio/` (ou tornar essa a homepage)
- `d:/w2-posts-studio/src/lib/brands-registry.ts` — criar com metadados dos brands (nome, descrição, logo)

## Detalhes Técnicos

**brands-registry:**

```ts
export const brandsRegistry = {
  'w2-agencia': {
    id: 'w2-agencia',
    name: 'w² Agência',
    description: 'Agência de presença digital para pequenos negócios brasileiros',
    logo: '/brands/w2-agencia/logo-symbol-color.svg', // expor SVG via public/
  },
} as const;
```

**Mover SVGs para `public/brands/[brand]/`** para acesso via URL, em vez de import (mais simples para o card).

## Verificação

- [ ] `/studio/` lista 1 card: w² Agência
- [ ] Clicar leva para `/studio/w2-agencia/`
- [ ] Logo do brand renderiza corretamente no card
- [ ] Layout pronto para crescer (grid expansível)
- [ ] `/` redireciona para `/studio/` (ou é a homepage)
