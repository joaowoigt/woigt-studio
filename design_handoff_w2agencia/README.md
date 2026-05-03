# Handoff: w² Agência — Identidade Visual Completa

**Versão:** 1.0 · Opção C "Explosão"
**Data:** Maio 2026
**Escopo:** Landing Page institucional + Design System + Social Media Kit

---

## ⚠️ Sobre os arquivos deste pacote

Os arquivos HTML incluídos são **referências de design de alta fidelidade** — protótipos que documentam com precisão a aparência, os tokens e os comportamentos pretendidos. Eles **não são código de produção** para ser copiado diretamente.

A tarefa do desenvolvedor é **recriar esses designs no ambiente do projeto real** (React, Next.js, Vue, etc.) usando os padrões e bibliotecas já estabelecidos — ou, se não houver ambiente definido, escolher o framework mais adequado e implementar a partir daqui.

---

## Fidelidade

**Alta fidelidade (hi-fi).** As cores, tipografia, espaçamentos, interações e cópias são finais. O desenvolvedor deve recriar o resultado visual de forma pixel-a-pixel usando as bibliotecas e o sistema de design do codebase.

---

## Arquivos do pacote

| Arquivo | Descrição |
|---|---|
| `Design System.html` | Manual completo de identidade visual — cores, tipo, logo, elementos, foto, editorial |
| `Landing Page.html` | Landing page institucional completa com Tweaks Panel |
| `Social Posts.html` | Kit de social media — 7 posts 1080×1080 + 2 stories 1080×1920 |
| `TOKENS.css` | Todos os tokens de design (cores, tipo, espaço, bordas, texturas) em CSS custom properties |
| `design-canvas.jsx` | Componente auxiliar de canvas (usado no Social Posts) |
| `tweaks-panel.jsx` | Componente auxiliar do painel de tweaks |

---

## Identidade da marca em uma frase

> **w² Agência** é uma agência digital para MEIs e pequenas empresas. A marca é direta, sem floreios, com personalidade editorial forte — tipografia massiva, contraste brutal, bordas sólidas. Sem arredondamentos, sem sombras, sem gradientes de fundo.

---

## 01 · Design Tokens

> Arquivo completo: `TOKENS.css`

### Cores

| Token | Valor | Uso |
|---|---|---|
| `--w2-yellow` | `#F5C100` | Cor primária — hero, fundos, logo sobre escuro |
| `--w2-magenta` | `#E01A5A` | Acento cirúrgico — o "²", itálicos, CTAs em fundo escuro |
| `--w2-black` | `#0D0D0D` | Texto, bordas, superfícies escuras |
| `--w2-graphite` | `#1A1A1A` | Superfícies secundárias — navbar, seções de fundo |
| `--w2-white` | `#FFFFFF` | Fundos claros, espaço negativo, texto sobre preto |

**Regra crítica de contraste:**
- ✅ Amarelo sobre preto
- ✅ Branco sobre preto
- ✅ Amarelo sobre magenta
- ❌ **NUNCA** amarelo sobre branco — ilegível

### Tipografia

**Fontes:** [Google Fonts — Barlow Condensed + Barlow](https://fonts.googleapis.com/css2?family=Barlow+Condensed:ital,wght@0,400;0,600;0,700;0,900;1,700;1,900&family=Barlow:wght@400;500;600;700&display=swap)

| Papel | Família | Peso | Tamanho | Line-height | Letter-spacing |
|---|---|---|---|---|---|
| Display / Hero | Barlow Condensed | 900 | 96px | 0.9 | -2px |
| Headline 1 | Barlow Condensed | 900 | 64px | 0.95 | -1px |
| Headline 2 | Barlow Condensed | 900 | 40px | 1.0 | normal |
| Label / Eyebrow | Barlow Condensed | 700 | 13px | — | 0.2em |
| Itálico de destaque | Barlow Condensed | 900 italic | 40px+ | — | — + cor magenta |
| Corpo | Barlow | 400/500 | 16px | 1.65 | — |
| Pequeno / meta | Barlow | 400 | 13px | 1.5 | — |

### Bordas

| Variante | Valor | Uso |
|---|---|---|
| Padrão | `3px solid #0D0D0D` | Cards, botões, separadores |
| Destaque | `4px solid #E01A5A` | Selos, badges especiais |
| Sutil (sobre escuro) | `1px solid rgba(245,193,0,0.12)` | Separadores internos em seções escuras |
| Borda superior amarela | `border-top: 3px solid #F5C100` | Cards de etapas/processo |

**Regra:** `border-radius: 0` em tudo. **Nunca** usar cantos arredondados — exceto avatares circulares (`border-radius: 50%`).

### Espaçamento

| Token | Valor | Uso |
|---|---|---|
| xs | 4px | Separadores internos, ícones |
| sm | 8px | Gap entre label e valor |
| md | 16px | Padding de badges, gap de colunas |
| lg | 24px | Padding de cards, gap de grid |
| xl | 40px | Padding lateral de seções |
| 2xl | 80px | Padding vertical de seções |

### Texturas (aplicadas via CSS background-image)

| Nome | Código CSS |
|---|---|
| Halftone (sobre amarelo) | `radial-gradient(circle, rgba(13,13,13,0.15) 1.5px, transparent 1.5px)` · size `18px 18px` |
| Grid (sobre amarelo) | `linear-gradient(rgba(13,13,13,0.08) 1px,transparent 1px), linear-gradient(90deg,rgba(13,13,13,0.08) 1px,transparent 1px)` · size `28px 28px` |
| Scanlines (sobre preto) | `repeating-linear-gradient(0deg, rgba(13,13,13,0.06) 0px, rgba(13,13,13,0.06) 1px, transparent 1px, transparent 6px)` |
| Noise (sobre grafite) | SVG feTurbulence, opacidade 12% |

---

## 02 · Logo

### Anatomia

```
W²  |  AGÊNCIA
```

- `W²` — Barlow Condensed 900, tamanho 52px (adaptável). O `²` em superscript, cor **magenta** `#E01A5A`.
- Separador — linha vertical `2px`, altura ~40px, cor contextual.
- `AGÊNCIA` — Barlow Condensed 700, uppercase, tracking `0.25em`.

### Versões

| Versão | Fundo | Cor do W² | Cor do AGÊNCIA |
|---|---|---|---|
| Principal (escuro) | `#0D0D0D` | `#F5C100` | `rgba(255,255,255,0.9)` |
| Claro | `#FFFFFF` | `#0D0D0D` | `#0D0D0D` |
| Amarelo / Hero | `#F5C100` | `#0D0D0D` | `#0D0D0D` |
| Avatar / Ícone | `#0D0D0D` com borda `3px #F5C100` | `#F5C100` | — (só marca) |

### Regras de uso
- Zona de exclusão: espaço mínimo ao redor = altura da letra "W".
- **Nunca** distorcer, rotacionar ou alterar proporções.
- **Nunca** amarelo sobre branco.

---

## 03 · Componentes da Landing Page

### Navbar
- **Fundo:** `#1A1A1A` (graphite)
- **Borda inferior:** `3px solid #F5C100`
- **Altura:** 64px, `position: fixed`
- **Logo:** versão escuro (W² amarelo)
- **Links de navegação:** Barlow Condensed 700, 12px, `uppercase`, `tracking 0.06em`, cor `rgba(255,255,255,0.65)` → hover `#F5C100`
- **Botão CTA "Diagnóstico":** Barlow Condensed 900, bg `#F5C100`, cor `#0D0D0D`, borda `3px solid #F5C100`, padding `8px 14px` → hover bg `#E01A5A`, borda `#E01A5A`, cor `#fff`
- **Scroll:** ao scrollar >40px, fundo vira `rgba(13,13,13,0.97)`

### Hero
- **Fundo:** `#F5C100` com textura halftone dots `rgba(13,13,13,0.15) 1.5px / 18px 18px`
- **Padding-top:** 64px (compensar navbar fixa)
- **Layout:** duas colunas — conteúdo (flex:1, max 620px) + showcase (360px, oculto abaixo de 900px)
- **Eyebrow:** inline-block, borda `3px solid #0D0D0D`, dot magenta 8×8px, Barlow Condensed 700, 13px, tracking 0.18em, uppercase, cor `#0D0D0D`
- **Headline:** Barlow Condensed 900, `clamp(36px, 3.8vw, 58px)`, lh 1.0, tracking -2px, uppercase, cor `#0D0D0D`; palavra de acento em `#E01A5A`
- **Body text:** Barlow 400, 18px, lh 1.6, cor `rgba(13,13,13,0.72)`, max-width 480px
- **Botão primário:** bg `#0D0D0D`, cor `#fff`, borda `3px solid #0D0D0D`, 17px → hover bg `#E01A5A`
- **Botão secundário:** bg `transparent`, cor `#0D0D0D`, borda `3px solid #0D0D0D`, 17px → hover bg `rgba(13,13,13,0.1)`

### Stats Bar (dentro do Hero)
- **Fundo:** `#0D0D0D`
- 4 estatísticas em grid horizontal (`display: table` para compatibilidade)
- Número: Barlow Condensed 900, 42px, cor `#F5C100`
- Label: Barlow 400, 13px, cor `rgba(255,255,255,0.5)`
- Separadores: `1px solid rgba(245,193,0,0.12)` entre células

### Showcase de Projetos (Hero — lateral)
- Cards com animação `sc-float` (translateY -9px, 3.2s infinite)
- Ao trocar projeto: animação `sc-spin` (rotateY 540deg, 0.8s cubic-bezier)
- Intervalo de troca: 4200ms
- Tag de projeto: bg `#F5C100` cor `#0D0D0D`; variante accent: bg `#E01A5A` cor `#fff`
- Pause no hover (`mouseenter`/`mouseleave`)

### Seções de conteúdo

**Estrutura padrão de seção:**
```html
<eyebrow>
  linha 24px · cor #F5C100 (inline-block) + texto Barlow Condensed 700, 13px, tracking 0.22em, uppercase
</eyebrow>
<título>
  Barlow Condensed 900, 58px, lh 1.0, uppercase
  palavra em itálico com cor #E01A5A
</título>
```

**Serviços** (`background: #1A1A1A`)
- Grid de 4 colunas, `display: table`
- Card base: padding 36px 24px, borda `1px solid rgba(245,193,0,0.1)`, hover → bg `#F5C100`, textos viram preto
- Número decorativo: Barlow Condensed 900, 44px, `rgba(245,193,0,0.2)`
- Título do serviço: Barlow Condensed 900, 34px, cor `#F5C100` → hover `#0D0D0D`
- Card "popular": `background: rgba(224,26,90,0.08)` → hover `#E01A5A`, textos viram branco
- Badge "POPULAR": rotação 45°, bg `#E01A5A`, posição `absolute top-right`

**Como Funciona** (`background: #0D0D0D`)
- 3 colunas, borda superior amarela em cada step (`border-top: 3px solid #F5C100`)
- Número fantasma: Barlow Condensed 900, 88px, `rgba(245,193,0,0.07)`, `margin-bottom: -14px`
- Título: Barlow Condensed 900, 34px, cor `#F5C100`
- Corpo: Barlow 400, 15px, lh 1.65, cor `rgba(255,255,255,0.55)`

**Depoimentos** (`background: #1A1A1A`)
- 3 colunas, borda ao redor `3px solid rgba(245,193,0,0.15)`
- Aspas: Barlow Condensed 900, 48px, cor `#F5C100`, opacity 0.3
- Avatar: círculo 44px, bg `#F5C100`, cor `#0D0D0D`, `border-radius: 50%`
- Nome: Barlow Condensed 700, 15px, uppercase, cor branco
- Negócio/cidade: Barlow 400, 12px, cor `rgba(255,255,255,0.35)`

**CTA Banner** (`background: #E01A5A`)
- Centralizado, padding 80px
- Headline: Barlow Condensed 900, 80px, branco; palavra destaque em `#F5C100`
- Watermark W² fantasma: 500px, `rgba(255,255,255,0.05)`
- Botão primário: bg `#F5C100`, cor `#0D0D0D`, `18px`
- Botão secundário: cor `#fff`, borda `rgba(255,255,255,0.45)`

### Footer
- **Fundo:** `#0D0D0D`, borda superior `3px solid rgba(245,193,0,0.2)`
- Descrição da marca: Barlow 400, 13px, cor `rgba(255,255,255,0.3)`
- Títulos de coluna: Barlow Condensed 700, 12px, tracking 0.2em, uppercase, cor `#F5C100`
- Links: Barlow 400, 14px, cor `rgba(255,255,255,0.35)`
- Copyright: Barlow 400, 12px, cor `rgba(255,255,255,0.18)`

### Tweaks Panel
- Posição: `fixed bottom-right`, `z-index: 9999`
- Fundo: `rgba(14,14,16,0.97)`, borda `1px solid rgba(255,255,255,0.07)`
- Controla: 6 temas de cores pré-definidos, pickers individuais (--y, --m, --b/--g), textura do hero (halftone / grid / off), headline itálico, visibilidade do showcase
- **Temas disponíveis:** Explosão (#F5C100/#E01A5A), Fogo (#FF5C00/#FF2D55), Neon (#00FF87/#E01A5A), Elétrico (#00CFFF/#7B2FFF), Coral (#FF6B6B/#F5C100), Bordeaux (#E8C547/#9B1B5A)
- Protocolo: registrar listener antes de anunciar `__edit_mode_available`

---

## 04 · Componentes Gráficos Reutilizáveis

### Badge / Etiqueta
```
display: inline-flex; align-items: center; gap: 8px;
font-family: Barlow Condensed 700; font-size: 13px;
letter-spacing: 0.15em; text-transform: uppercase;
padding: 8px 16px;
```
- Variante dark: bg `#0D0D0D`, cor `#F5C100`
- Variante magenta: bg `#E01A5A`, cor `#fff`
- Variante yellow: bg `#F5C100`, cor `#0D0D0D`, borda `3px solid #0D0D0D`

### Selo Circular
```
width: 120px; height: 120px;
border: 4px solid #E01A5A; border-radius: 50%;
transform: rotate(-10deg a -15deg);
```
- Borda interna tracejada: `border: 2px dashed #E01A5A; inset: 5px; border-radius: 50%`
- Apenas em magenta ou preto. Sempre inclinado entre -10° e -15°.

### Eyebrow Row
```
linha decorativa: display: inline-block; width: 24px; height: 3px; background: #F5C100; vertical-align: middle; margin-right: 10px;
texto: Barlow Condensed 700; font-size: 13px; letter-spacing: 0.22em; text-transform: uppercase
```

---

## 05 · Tratamento de Imagem

| Tratamento | CSS | Quando usar |
|---|---|---|
| P&B alto contraste | `filter: grayscale(1) contrast(1.6) brightness(1.1)` | Fotos de pessoas — **sempre** |
| Duotone amarelo | `filter: sepia(1) hue-rotate(330deg) saturate(3)` + `mix-blend-mode: multiply` | Fotos integradas ao fundo amarelo |
| Vinheta escura | radial-gradient overlay `rgba(245,193,0,0.15)` sobre `#0D0D0D` | Posts dark |
| Halftone overlay | `radial-gradient` dots 15–25% opacity sobre foto | Textura editorial |

**Regra:** Fotos com rosto → **sempre P&B**. Nunca fotos coloridas com baixa saturação.

---

## 06 · Social Media Kit

> Arquivo de referência: `Social Posts.html`
> Guia detalhado: `SOCIAL_MEDIA_GUIDE.md`

### Formatos

| Formato | Dimensões | Uso |
|---|---|---|
| Post quadrado | 1080 × 1080px | Feed do Instagram / LinkedIn |
| Story | 1080 × 1920px | Stories do Instagram |

### Templates disponíveis (7 posts + 2 stories)

| # | Nome | Fundo | Descrição |
|---|---|---|---|
| P01 | Provocação | Preto | Headline amarela massiva, sem imagem |
| P02 | Dado / Stat | Amarelo + halftone | Número gigante, fato conciso |
| P03 | Carrossel (capa) | Grafite + halftone | Pergunta/provação, "arrasta pra ver" |
| P04 | Carrossel (slide interno) | Preto | Número do slide + conteúdo educativo |
| P05 | CTA Magenta | Magenta | Chamada direta para WhatsApp/bio |
| P06 | Prova Social | Grafite | Depoimento com destaque amarelo |
| P07 | Verdade Incômoda | Amarelo + grid | Afirmação direta, texto sobre amarelo |
| S01 | Story CTA | Amarelo + halftone | Diagnóstico grátis, swipe up |
| S02 | Story Dados | Preto + scanlines | Stack de stats verticais |

---

## 07 · Voz & Tom

- **Direto:** Uma ideia por post. Frase curta vence frase longa.
- **Sem jargão:** "Apareça no Google", não "SEO otimizado"
- **Sem floreio:** Nunca "excelência em soluções digitais"
- **Verdadeiro:** Dados reais. Cases reais. Nomes reais.
- **Irreverente:** Pode provocar. Não pode ofender.

---

## 08 · Regras Absolutas de Layout

1. **`border-radius: 0`** em todos os elementos — exceto avatares circulares
2. **Sem `box-shadow`** — bordas fazem o trabalho
3. **Magenta:** máximo 1 elemento por composição. Use com precisão cirúrgica.
4. **Amarelo sobre branco:** proibido
5. **Fontes exclusivas:** Barlow Condensed (display) + Barlow (corpo). Nenhuma outra.
6. **Bordas sempre 3–4px sólidas** — nunca tracejadas no layout principal (exceto selos)
7. **Fotos de pessoas:** obrigatoriamente P&B com alto contraste

---

## 09 · Cadência Editorial Semanal

| Dia | Tipo de post |
|---|---|
| Segunda | Provocação |
| Terça | Educativo (carrossel) |
| Quarta | Dado / Stat |
| Quinta | CTA direto |
| Sexta | Case / Resultado |
| Sábado | Story |
| Domingo | Off |

---

## 10 · Checklist de implementação

- [ ] Importar fontes Barlow Condensed + Barlow do Google Fonts
- [ ] Configurar CSS custom properties de `TOKENS.css` no `:root` do projeto
- [ ] Implementar componente `Logo` com as 4 variantes
- [ ] Implementar `Badge` e `Eyebrow` como componentes reutilizáveis
- [ ] Implementar navbar fixa com comportamento de scroll
- [ ] Implementar hero com textura halftone e showcase animado
- [ ] Implementar showcase com rotação (rotateY) entre projetos
- [ ] Implementar seções: Serviços, Como Funciona, Depoimentos, CTA, Footer
- [ ] Implementar Tweaks Panel com os 6 temas de cores
- [ ] Implementar selo circular rotacionado para CTA de diagnóstico
- [ ] Criar templates de post para social media (7 posts + 2 stories)
- [ ] Garantir responsividade: breakpoint principal em 768px e 900px

---

*Dúvidas sobre algum componente? Todos os padrões estão demonstrados ao vivo no `Design System.html`. Abra o arquivo no browser para ver a referência visual completa.*
