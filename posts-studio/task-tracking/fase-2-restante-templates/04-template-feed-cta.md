# Task 04: Template feed-cta (3 variantes + upload opcional)

**Fase:** Fase 2 — Restante dos Templates
**Depende de:** Fase 2 Task 01
**Estimativa:** 2h
**Status:** pending

---

## Objetivo

Implementar template `feed-cta` (oferta/chamada para ação) em formato 1:1 (1080×1080), com 3 variantes e imagem opcional.

## O Que Fazer

1. Criar `src/brands/w2-agencia/templates/feed-cta/`
2. Schema: headline (max 50), subline opcional (max 80), CTA (max 25), URL/handle (max 40), imagem opcional, variant, colorVariant
3. 3 variantes:
   - **A** — Headline grande topo + 2-3 benefícios curtos (parseados da subline com `\n`) + CTA box destacado rodapé
   - **B** — Headline centro + ícone/asset accent (símbolo w² do brand) + CTA texto inline
   - **C** — Background imagem (se uploaded) ou cor sólida + overlay + headline + CTA
6. Imagem é opcional: se ausente, variante C usa cor sólida; A e B ignoram imagem
7. Adicionar ao template-registry

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-cta/{schema,meta,variants,index}`
- `d:/w2-posts-studio/src/lib/template-registry.ts`

## Detalhes Técnicos

**Schema:**

```ts
export const feedCtaSchema = z.object({
  headline: z.string().min(1).max(50),
  subline: z.string().max(80).optional(),
  cta: z.string().min(1).max(25),
  handle: z.string().max(40).optional(),  // ex: "@w2.agencia" ou "w2agencia.com.br"
  image: z.string().optional(),           // data URI opcional
  variant: z.enum(['A', 'B', 'C']),
  colorVariant: z.enum(['yellow', 'magenta', 'black']),
});
```

**CTA box estilizado:** retângulo arredondado com a cor accent, texto em maiúscula, padding generoso. Inspiração visual: botão "VOCÊ EXISTE." da identidade.

**Handle/URL:** font pequena (24-28px), no rodapé, com símbolo "@" ou "↗" antes.

**Variante C com imagem:**
```tsx
<div style={{ position: 'relative', width: 1080, height: 1080 }}>
  <img src={input.image} style={{ position: 'absolute', inset: 0, width: 1080, height: 1080, objectFit: 'cover' }} />
  <div style={{ position: 'absolute', inset: 0, background: 'rgba(0,0,0,0.6)' }} />
  <div style={{ position: 'absolute', inset: 0, display: 'flex', flexDirection: 'column', justifyContent: 'center', alignItems: 'center', padding: 80 }}>
    {/* headline + cta */}
  </div>
</div>
```

**Subline com benefícios curtos (variante A):** se subline contém quebras de linha (`\n`), renderizar como lista. Caso contrário, parágrafo único.

## Verificação

- [ ] Acessar `/studio/w2-agencia/feed-cta` carrega o template
- [ ] Sem imagem uploaded, variantes A e B funcionam normalmente
- [ ] Sem imagem uploaded, variante C usa fundo cor sólida
- [ ] Com imagem uploaded, variante C usa imagem como background com overlay
- [ ] CTA box visualmente destacado nas 3 variantes
- [ ] Handle/URL aparece quando preenchido, oculta quando vazio
- [ ] 9 combinações de variante × cor funcionam visualmente
- [ ] PNG em 1080×1080
