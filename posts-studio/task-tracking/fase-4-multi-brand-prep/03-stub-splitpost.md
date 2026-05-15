# Task 03: Stub `src/brands/splitpost/` com 1 template

**Fase:** Fase 4 — Multi-Brand Prep
**Depende de:** Fase 4 Task 02
**Estimativa:** 1h
**Status:** pending

---

## Objetivo

Validar que o refactor multi-brand funciona criando um stub real do Splitpost com tokens próprios + 1 template (feed-quote) usando os mesmos componentes mas brand diferente. Não é o brand final — é prova de conceito.

## O Que Fazer

1. Criar `src/brands/splitpost/` com estrutura espelhada de w2-agencia:
   - `tokens.ts` (cores do Splitpost — buscar no `d:/splitpost/` se houver, senão usar placeholders alinhados com visual atual)
   - `fonts.ts` com `loadSplitpostFonts()`
   - `assets.ts` com logo do Splitpost
   - `templates/feed-quote/` (apenas esse template para o stub)
2. Registrar no `templateRegistry` e em `fontLoaders`
3. Adicionar entrada do Splitpost no `brandsRegistry`
4. Testar: acessar `/studio/splitpost/feed-quote` → studio funciona com tokens do Splitpost
5. Exportar 1 PNG → confirmar visualmente que segue brand Splitpost (não w²)

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/brands/splitpost/*` — criar estrutura completa
- `d:/w2-posts-studio/src/lib/load-brand-fonts.ts` — adicionar splitpost
- `d:/w2-posts-studio/src/lib/template-registry.ts` — adicionar splitpost
- `d:/w2-posts-studio/src/lib/brands-registry.ts` — adicionar splitpost

## Detalhes Técnicos

**Tokens placeholder do Splitpost (a confirmar no brand real):**

```ts
export const splitpostTokens = {
  colors: {
    primary: '#000000',     // ajustar com tokens reais do Splitpost
    accent: '#FF5A5F',
    background: '#FFFFFF',
    text: '#0D0D0D',
    muted: '#666666',
  },
  fonts: {
    display: 'Inter',
    body: 'Inter',
  },
  // ...
} as const;
```

**Importante:** o template `feed-quote` do Splitpost pode ser COPIADO de w2-agencia e adaptado, OU usar os mesmos componentes JSX consumindo tokens via prop. Decisão: na primeira implementação, copiar (templates são brand-específicos por design). Refatorar para componentes genéricos só se houver duplicação real depois.

**Logo do Splitpost:** se não houver SVG no `d:/splitpost/`, usar placeholder text "Splitpost".

## Verificação

- [ ] `src/brands/splitpost/` existe com estrutura completa
- [ ] Acessar `/studio/splitpost/feed-quote` carrega studio
- [ ] PNG exportado segue tokens do Splitpost (cores, fontes diferentes de w²)
- [ ] `/studio/` lista 2 brands agora: w² Agência + Splitpost
- [ ] Posts de w² continuam idênticos (zero regressão)
- [ ] Tempo total para criar o stub Splitpost: documentado para validar que <2h (critério de sucesso)
