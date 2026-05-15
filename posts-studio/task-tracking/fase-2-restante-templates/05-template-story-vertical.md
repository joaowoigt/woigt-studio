# Task 05: Template story-vertical (3 variantes, 9:16, safe zones)

**Fase:** Fase 2 — Restante dos Templates
**Depende de:** Fase 2 Task 01
**Estimativa:** 2h30
**Status:** pending

---

## Objetivo

Implementar template `story-vertical` no formato 9:16 (1080×1920), com 3 variantes que respeitam as safe zones do Instagram Stories (topo e rodapé reservados para UI nativa).

## O Que Fazer

1. Criar `src/brands/w2-agencia/templates/story-vertical/`
2. Schema: headline (max 80), subline opcional (max 60), CTA (max 25), imagem opcional, variant, colorVariant
3. Meta: aspect ratio 9:16, dimensões 1080×1920
4. **Safe zones:** topo 220px reservado, rodapé 250px reservado para UI nativa do Instagram. Texto crítico fica na área central (1080×1450).
5. 3 variantes:
   - **A** — Quote/headline centro + logo topo (safe area) + assinatura rodapé (safe area)
   - **B** — Imagem fundo (se uploaded) + overlay gradiente + headline + CTA "→ link" no rodapé (mas dentro da safe area)
   - **C** — Split horizontal: bloco cor topo (50% — headline) + bloco imagem baixo (50%) + CTA central na junção
6. Adicionar ao template-registry
7. Renderizar uma linha tracejada de "safe zone" no preview (NÃO no PNG final) para visualizar limites

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/brands/w2-agencia/templates/story-vertical/{schema,meta,variants,index}`
- `d:/w2-posts-studio/src/components/live-preview.tsx` — adicionar prop opcional `safeZones` para visualização
- `d:/w2-posts-studio/src/lib/template-registry.ts`

## Detalhes Técnicos

**Safe zones do Instagram Stories (1080×1920):**

| Zona | Altura | Função |
|------|--------|--------|
| Topo | 0-220px | Profile pic, username, tempo (overlay do app) |
| Central | 220-1670px | Área segura para conteúdo importante |
| Rodapé | 1670-1920px | Reactions bar, link sticker, swipe up |

**Variante A esqueleto:**

```tsx
<div style={{ width: 1080, height: 1920, background: palette.bg, display: 'flex', flexDirection: 'column', fontFamily: 'Barlow Condensed' }}>
  {/* SAFE ZONE TOPO 220px — apenas elementos decorativos não-críticos */}
  <div style={{ height: 220, display: 'flex', alignItems: 'flex-end', justifyContent: 'center', paddingBottom: 24 }}>
    <img src={logoSymbolColor} style={{ width: 80, height: 80 }} />
  </div>
  {/* ÁREA CENTRAL SEGURA 1450px */}
  <div style={{ flex: 1, display: 'flex', alignItems: 'center', justifyContent: 'center', padding: 80 }}>
    <span style={{ fontSize: 96, fontWeight: 900, color: palette.fg, textAlign: 'center', lineHeight: 1.05 }}>
      {input.headline}
    </span>
  </div>
  {/* SAFE ZONE RODAPÉ 250px — assinatura discreta */}
  <div style={{ height: 250, display: 'flex', alignItems: 'flex-start', justifyContent: 'center', paddingTop: 24 }}>
    <span style={{ fontSize: 32, color: palette.fg, opacity: 0.7 }}>w² Agência</span>
  </div>
</div>
```

**Safe zones no preview:** adicionar prop `safeZones={{ top: 220, bottom: 250 }}` no `<LivePreview>` que desenha linhas tracejadas (apenas no preview, NÃO no PNG). Útil para o irmão entender visualmente onde não colocar texto crítico.

**Schema:**

```ts
export const storyVerticalSchema = z.object({
  headline: z.string().min(1).max(80),
  subline: z.string().max(60).optional(),
  cta: z.string().max(25).optional(),
  image: z.string().optional(),
  variant: z.enum(['A', 'B', 'C']),
  colorVariant: z.enum(['yellow', 'magenta', 'black']),
});
```

## Verificação

- [ ] Acessar `/studio/w2-agencia/story-vertical` carrega o template
- [ ] PNG exportado tem 1080×1920 (proporção 9:16 exata)
- [ ] No preview, linhas de safe zone aparecem (220px topo, 250px rodapé)
- [ ] No PNG final, NÃO há linhas de safe zone (só conteúdo)
- [ ] Textos importantes ficam dentro da área central (220-1670px)
- [ ] Variante A: headline centralizado + logo topo + assinatura rodapé
- [ ] Variante B: imagem fundo + overlay + headline (quando imagem uploaded)
- [ ] Variante C: split topo/baixo funcional
- [ ] 9 combinações funcionam visualmente
