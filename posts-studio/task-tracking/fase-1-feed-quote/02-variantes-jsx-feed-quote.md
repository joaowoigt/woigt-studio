# Task 02: 3 variantes JSX de feed-quote

**Fase:** Fase 1 — Primeiro Template feed-quote
**Depende de:** Fase 1 Task 01
**Estimativa:** 2h
**Status:** done

---

## Objetivo

Implementar as 3 variantes visuais do template `feed-quote` como componentes JSX puros (sem hooks/state) que aceitam `FeedQuoteInput` e renderizam o post.

## O Que Fazer

1. Criar `variants.tsx` na pasta `src/brands/w2-agencia/templates/feed-quote/`
2. Implementar 3 componentes:
   - `FeedQuoteVariantA` — texto centro, fundo cor sólida, logo rodapé
   - `FeedQuoteVariantB` — texto topo, faixa accent, assinatura "— w² Agência" rodapé
   - `FeedQuoteVariantC` — texto centralizado, textura/pattern fundo, logo discreto canto
3. Criar componente router `FeedQuoteRender` que recebe `input: FeedQuoteInput` e despacha para a variante correta
4. Aplicar paletas de cor baseadas em `input.colorVariant`:
   - `yellow`: fundo amarelo, texto preto, ² magenta
   - `magenta`: fundo magenta, texto branco, ² preto
   - `black`: fundo preto, texto branco, ² magenta
5. Garantir que TODOS os estilos são compatíveis com Satori (flexbox only, sem grid, sem filters)

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-quote/variants.tsx` — criar

## Detalhes Técnicos

**Estrutura sugerida:**

```tsx
import { w2Tokens } from '@/brands/w2-agencia/tokens';
import { logoPrimaryDark, logoPrimaryLight, patternTile } from '@/brands/w2-agencia/assets';
import type { FeedQuoteInput } from './schema';

function getPalette(colorVariant: FeedQuoteInput['colorVariant']) {
  switch (colorVariant) {
    case 'yellow':  return { bg: w2Tokens.colors.yellow,  fg: w2Tokens.colors.black, accent: w2Tokens.colors.magenta, logo: 'dark' as const };
    case 'magenta': return { bg: w2Tokens.colors.magenta, fg: w2Tokens.colors.white, accent: w2Tokens.colors.black,   logo: 'light' as const };
    case 'black':   return { bg: w2Tokens.colors.black,   fg: w2Tokens.colors.white, accent: w2Tokens.colors.magenta, logo: 'light' as const };
  }
}

export function FeedQuoteVariantA({ input }: { input: FeedQuoteInput }) {
  const palette = getPalette(input.colorVariant);
  return (
    <div style={{ width: 1080, height: 1080, background: palette.bg, display: 'flex', flexDirection: 'column', alignItems: 'center', justifyContent: 'center', padding: 80, fontFamily: 'Barlow Condensed' }}>
      <span style={{ fontSize: 84, fontWeight: 900, color: palette.fg, textAlign: 'center', lineHeight: 1.05, letterSpacing: -2 }}>
        {input.quote}
      </span>
      {/* logo rodapé */}
    </div>
  );
}

// VariantB e VariantC seguem o mesmo padrão estrutural

export function FeedQuoteRender({ input }: { input: FeedQuoteInput }) {
  switch (input.variant) {
    case 'A': return <FeedQuoteVariantA input={input} />;
    case 'B': return <FeedQuoteVariantB input={input} />;
    case 'C': return <FeedQuoteVariantC input={input} />;
  }
}
```

**Anti-patterns a evitar:**
- Não usar CSS Grid (Satori não suporta)
- Não usar `gap` em flex container — usar `marginTop/marginBottom` ou wrappers
- Não usar `box-shadow` com blur grande
- Não usar variáveis CSS (`var(--x)`) — passar valor direto
- Não usar `position: fixed` — apenas `relative` ou `absolute`

**Aplicar tagline opcional:** quando `signature` estiver preenchido, exibir no rodapé. Quando vazio, ocultar o elemento.

## Verificação

- [ ] `FeedQuoteRender` aceita `FeedQuoteInput` e despacha para a variante correta
- [ ] 3 variantes implementadas e visualmente distintas
- [ ] Substituir o JSX de teste da Task 06/Fase 0 por `<FeedQuoteRender input={mockInput} />` e PNG renderiza corretamente
- [ ] Testar as 3 paletas (yellow/magenta/black) — cores aplicam corretamente
- [ ] Testar quote curto (10 chars) e longo (120 chars) — texto se adapta sem quebrar layout
- [ ] Logo aparece nas 3 variantes nos lugares definidos
