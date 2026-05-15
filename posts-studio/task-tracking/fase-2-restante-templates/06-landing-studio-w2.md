# Task 06: Landing `/studio/w2-agencia/` lista templates

**Fase:** Fase 2 — Restante dos Templates
**Depende de:** Tasks 02-05 da Fase 2 (todos os templates criados)
**Estimativa:** 1h
**Status:** pending

---

## Objetivo

Criar página `/studio/w2-agencia/` que lista todos os 5 templates disponíveis como cards clicáveis, agrupados por aspect ratio (feed 1:1 / feed 4:5 / story 9:16), para o irmão escolher rapidamente o template a criar.

## O Que Fazer

1. Criar `src/app/studio/[brand]/page.tsx`
2. Buscar templates do brand via `templateRegistry[params.brand]`
3. Layout grid responsivo: cards 3 colunas em desktop, 1 em mobile
4. Cada card mostra:
   - Thumbnail (ver "Detalhes Técnicos" — opções)
   - Nome do template
   - Descrição curta
   - Aspect ratio (badge: "1:1", "4:5", "9:16")
   - Link para `/studio/[brand]/[template]`
5. Agrupar por aspect ratio com headers ("Feed quadrado", "Feed retrato", "Story vertical")
6. Header da página: logo w² + título "Templates de Posts — w² Agência"

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/app/studio/[brand]/page.tsx` — criar
- `d:/w2-posts-studio/src/app/studio/[brand]/_template-card.tsx` — criar
- `d:/w2-posts-studio/src/lib/template-registry.ts` — adicionar campo `description` se ainda não tem

## Detalhes Técnicos

**Sobre thumbnails — escolher uma estratégia:**

1. **(Recomendado MVP)** Renderizar uma versão miniatura do template com valores default usando `<LivePreview>` em `maxDisplayWidth={200}`. Vantagem: sempre atualizado, zero arquivos extras. Desvantagem: bundle maior (todos os templates carregados na home).

2. PNG estático pré-renderizado salvo em `public/thumbs/[template-id].png`. Vantagem: leve. Desvantagem: precisa atualizar manualmente quando template mudar.

**Decisão para MVP:** opção 1 (LivePreview mini). Custo de bundle é baixo (4-5 componentes). Se virar problema, migrar para opção 2 na Fase 3.

**Card example:**

```tsx
<Link href={`/studio/${brand}/${templateId}`} className="block border rounded-lg p-4 hover:shadow-lg transition">
  <div className="mb-3 flex justify-center bg-neutral-50 p-4 rounded">
    <LivePreview width={meta.width} height={meta.height} maxDisplayWidth={200}>
      <Render input={defaultInput} />
    </LivePreview>
  </div>
  <h3 className="font-semibold">{meta.name}</h3>
  <p className="text-sm text-neutral-600">{meta.description}</p>
  <span className="text-xs bg-neutral-200 px-2 py-1 rounded mt-2 inline-block">{meta.aspectRatio}</span>
</Link>
```

**Agrupamento:** `Object.values(brandTemplates).reduce((groups, t) => { groups[t.meta.aspectRatio] ??= []; groups[t.meta.aspectRatio].push(t); return groups; }, {})`

## Verificação

- [ ] Acessar `/studio/w2-agencia/` mostra 5 cards (feed-quote, feed-tip, feed-case, feed-cta, story-vertical)
- [ ] Cards agrupados por aspect ratio com headers visíveis
- [ ] Cada thumbnail renderiza o template com valores default
- [ ] Clicar em card navega para a página do template correspondente
- [ ] Layout responsivo (3 col desktop, 1 col mobile)
- [ ] Performance: página carrega em <2s
