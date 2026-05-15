# Task 04: Componente live-preview com escala

**Fase:** Fase 1 — Primeiro Template feed-quote
**Depende de:** Fase 1 Task 02
**Estimativa:** 1h
**Status:** done

---

## Objetivo

Construir `<LivePreview>` que renderiza o MESMO JSX do template no browser (não via Satori — direto React DOM), com escala automática para caber na tela do studio, mantendo proporção 1:1 ou 4:5 etc.

## O Que Fazer

1. Criar `src/components/live-preview.tsx`
2. O componente aceita:
   - `width`, `height`: dimensões reais do post (ex: 1080×1080)
   - `children`: o JSX do template (`<FeedQuoteRender input={...} />`)
   - `maxDisplayWidth`: largura máxima na tela (default 540px)
3. Renderiza um wrapper que escala o conteúdo via CSS `transform: scale(N)` onde `N = maxDisplayWidth / width`
4. O wrapper externo tem dimensões finais escaladas para layout não quebrar
5. Aplica borda/sombra sutil pra distinguir o "post" do resto da UI

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/components/live-preview.tsx` — criar

## Detalhes Técnicos

**Implementação:**

```tsx
type LivePreviewProps = {
  width: number;
  height: number;
  maxDisplayWidth?: number;
  children: React.ReactNode;
};

export function LivePreview({ width, height, maxDisplayWidth = 540, children }: LivePreviewProps) {
  const scale = maxDisplayWidth / width;
  const displayHeight = height * scale;

  return (
    <div
      style={{
        width: maxDisplayWidth,
        height: displayHeight,
        overflow: 'hidden',
        position: 'relative',
        borderRadius: 8,
        boxShadow: '0 4px 24px rgba(0,0,0,0.12)',
      }}
    >
      <div
        style={{
          width,
          height,
          transform: `scale(${scale})`,
          transformOrigin: 'top left',
        }}
      >
        {children}
      </div>
    </div>
  );
}
```

**Importante:**
- O JSX do template deve ser **idêntico** ao que vai pro Satori — qualquer divergência quebra paridade
- Fontes precisam estar carregadas no browser via `next/font` (Task 05 Fase 0)
- Imagens precisam estar acessíveis publicamente (não data URIs no preview se forem grandes — gera reflow)

**Estratégia de paridade:** o template renderiza com `width: 1080, height: 1080` reais. O wrapper escala via CSS. O Satori usa as MESMAS dimensões via prop. Logo, o mesmo JSX produz visual idêntico nos dois lados.

## Verificação

- [ ] `<LivePreview width={1080} height={1080}><FeedQuoteRender input={mockInput} /></LivePreview>` renderiza no browser
- [ ] Aparece em 540×540 px (escala 0.5) sem distorção
- [ ] Fonte Barlow Condensed aplica corretamente
- [ ] Mudar `mockInput.colorVariant` muda visualmente o preview
- [ ] Comparar lado-a-lado com PNG gerado por `/api/render`: visual idêntico (mesmas cores, fontes, posições)
