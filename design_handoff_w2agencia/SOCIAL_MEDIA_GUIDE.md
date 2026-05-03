# w² Agência — Guia de Produção de Social Media

**Versão:** 1.0 · Maio 2026
**Uso:** Referência para criação e gerenciamento de conteúdo nas redes sociais

---

## Princípio editorial

> Toda publicação deve ter uma intenção clara:
> **provocar**, **informar**, **converter** ou **mostrar resultado**.
> A tipografia faz o layout. A cor faz o clima. A cópia faz a venda.

---

## Formatos e especificações técnicas

### Post quadrado — Feed
- **Dimensões:** 1080 × 1080px
- **Canais:** Instagram Feed, LinkedIn, Facebook
- **Zona segura:** margem interna de 48px em todos os lados
- **Onde está no kit:** `Social Posts.html` → seção "Posts Quadrados"

### Story / Reels (estático)
- **Dimensões:** 1080 × 1920px (ratio 9:16)
- **Canais:** Instagram Stories, WhatsApp Status
- **Zona segura superior:** 80px (área de avatar/nome do perfil)
- **Zona segura inferior:** 160px (área de swipe up / link)
- **Onde está no kit:** `Social Posts.html` → seção "Stories"

---

## Os 7 templates de post (1080×1080)

### P01 · Provocação
**Objetivo:** Parar o scroll, gerar engajamento com afirmação direta.

**Anatomia:**
- Fundo: `#0D0D0D` + overlay scanlines (2% opacity)
- Eyebrow: dot magenta 8px + label em `rgba(255,255,255,0.35)`
- Headline: Barlow Condensed 900, ~168px, cor `#F5C100`, lettering comprimido
- Último linha da headline: em `#E01A5A` + italic
- Subtexto: Barlow 400, 24px, `rgba(255,255,255,0.45)`, separado por linha `rgba(245,193,0,0.2) 3px`
- Logo: `top-right`, variante escuro
- Acento geométrico: quadrado(s) com borda `rgba(245,193,0,0.15)` em `bottom-right`

**Cópia sugerida:**
```
APAREÇA
OU SUMA.
// subtexto: No digital, quem não aparece não existe. Simples assim.
```

**Adaptar para:** qualquer afirmação direta sobre presença digital, mercado, resultado.

---

### P02 · Dado / Stat
**Objetivo:** Comunicar um número ou resultado de forma impactante.

**Anatomia:**
- Fundo: `#F5C100` + halftone dots `rgba(13,13,13,0.16) / 20px`
- Barra preta no topo: 12px height, `#0D0D0D`
- Logo + badge de contexto: `top`, logo variante claro, badge com borda preta
- Número principal: Barlow Condensed 900, ~300px, cor `#0D0D0D`, tracking -12px
- Separador: `width: 100%; height: 4px; background: #0D0D0D`
- Headline de suporte: Barlow Condensed 900, 64px, cor `#0D0D0D`; acento em `#E01A5A` italic
- Subtexto: Barlow 400, 22px, `rgba(13,13,13,0.55)`

**Cópia sugerida:**
```
48H
──────────────
DO BRIEFING AO AR.
// subtexto: Sua landing page no ar em 2 dias. Sem enrolação.
```

**Adaptar para:** qualquer métrica relevante — `+200`, `3×`, `R$890`, `1ª página`, etc.

---

### P03 · Carrossel (Capa)
**Objetivo:** Introduzir série educativa, provocar curiosidade para arrastar.

**Anatomia:**
- Fundo: `#1A1A1A` + halftone branco `rgba(255,255,255,0.12) / 20px`
- Eyebrow com borda: `border: 2px solid rgba(245,193,0,0.3)`, dot magenta, label
- Contador de slides: `1 — 5` (ou número real), top-right
- Headline: Barlow Condensed 900, ~136px, cor `#F5C100`; última linha `#E01A5A` italic
- Rodapé preto: bg `#0D0D0D`, "Arrasta para ver →" + logo

**Cópia sugerida:**
```
3 RAZÕES
PRA SUA
EMPRESA
SUMIR DO
GOOGLE.
// rodapé: Arrasta para ver as razões →
```

**Adaptar para:** qualquer série educativa — "X erros", "X passos", "X verdades sobre..."

---

### P04 · Carrossel (Slide Interno)
**Objetivo:** Entregar o conteúdo prometido na capa, um ponto por slide.

**Anatomia:**
- Fundo: `#0D0D0D` + acentos geométricos rotacionados (bordas `rgba(245,193,0,0.06)`)
- Número do slide: Barlow Condensed 900, 72px, cor `#F5C100` + linha vertical `3px magenta`
- Headline do ponto: Barlow Condensed 900, 80px, alinhado à direita; cor `#E01A5A` ou `#F5C100`
- Separador: `64px × 4px`, bg `#E01A5A`
- Corpo: Barlow 400, 28px, lh 1.6, `rgba(255,255,255,0.65)`, max-width 760px
- Callout de solução: borda `3px solid rgba(245,193,0,0.2)`, dot magenta, texto `rgba(255,255,255,0.6)`
- Rodapé amarelo: bg `#F5C100`, "← Razão X de Y" + logo variante claro

**Regra:** máximo **1 ponto** por slide. Corpo com no máximo **3 linhas**.

---

### P05 · CTA Magenta
**Objetivo:** Conversão direta. Levar para WhatsApp ou link na bio.

**Anatomia:**
- Fundo: `#E01A5A`
- Watermark W²: 500px, `rgba(255,255,255,0.05)`, centrado verticalmente, `right: -60px`
- Eyebrow: borda `rgba(255,255,255,0.3)`, dot amarelo, label
- Headline: Barlow Condensed 900, ~168px; "PRONTO / PRA" em branco, "APARECER?" em `#F5C100`
- CTA block: bg `#F5C100`, inline-flex, "Diagnóstico Grátis" + separador + "Link na bio →"
- Rodapé: URL + logo, cor `rgba(255,255,255,0.45)`

**Cópia sugerida:**
```
PRONTO
PRA
APARECER?
// CTA: Diagnóstico Grátis · Link na bio →
```

**Adaptar para:** qualquer chamada de ação — promoção, abertura de agenda, lançamento.

---

### P06 · Prova Social (Depoimento)
**Objetivo:** Construir confiança com resultado real de cliente.

**Anatomia:**
- Fundo: `#1A1A1A`, borda ao redor `3px solid rgba(245,193,0,0.15)`
- Aspas fantasma: Barlow Condensed 900, 280px, `rgba(245,193,0,0.08)`, `top-left`
- Depoimento: Barlow 400, 52px, lh 1.35, cor `#FFFFFF`; destaque do resultado em `background: #F5C100; color: #0D0D0D`
- Separador: `border-top: 3px solid rgba(245,193,0,0.2)`, padding-top 28px
- Avatar: círculo 72px, bg `#F5C100`, inicial em Barlow Condensed 900, 36px, cor `#0D0D0D`
- Nome: Barlow Condensed 900, 36px, uppercase, branco
- Negócio + cidade: Barlow 400, 20px, `rgba(255,255,255,0.4)`
- Logo: `margin-left: auto`, alinhado à direita

**Regra:** nome e cidade reais. Resultado específico em destaque amarelo. Máximo 2 linhas de depoimento.

---

### P07 · Verdade Incômoda
**Objetivo:** Posicionamento de marca, diferenciação, engajamento por concordância.

**Anatomia:**
- Fundo: `#F5C100` + textura grid `rgba(13,13,13,0.07) / 28px`
- Barra preta no topo: 10px
- Logo: `top-left`, variante claro
- Bloco 1: Barlow Condensed 900, ~136px, cor `#0D0D0D`; afirmação principal em 4 linhas
- Separador horizontal: `width: 100%; height: 4px; background: #0D0D0D`
- Bloco 2: Barlow Condensed 900, ~96px; "É " em `#0D0D0D` + "RESULTADO." em `#E01A5A` italic
- Rodapé preto: subtexto de posicionamento

**Cópia sugerida:**
```
PRESENÇA
DIGITAL
NÃO É
ESTÉTICA.
──────────────
É RESULTADO.
// rodapé: Agência para quem quer aparecer, não para quem quer elogios.
```

---

## Os 2 templates de story (1080×1920)

### S01 · Story CTA — Diagnóstico Grátis
**Objetivo:** Conversão. Levar para o diagnóstico gratuito.

**Anatomia:**
- Fundo: `#F5C100` + halftone
- Header: logo variante claro + badge com URL
- Selo circular: 200px, `border: 6px solid #E01A5A`, rotação -12°, tracejado interno; "DIAGNÓSTICO / GRÁTIS / Sem compromisso"
- Headline principal: Barlow Condensed 900, 172px, "VOCÊ / FALA / COM / QUEM / FAZ." — última linha `#E01A5A` italic
- CTA block preto: "Arrasta pra cima" + subtexto
- Footer: "↑ Swipe up · Link na bio", `border-top: 3px solid #0D0D0D`

**Zona segura:** conteúdo principal entre y=80px e y=1760px.

---

### S02 · Story Dados & Stats
**Objetivo:** Reforçar credibilidade com números reais.

**Anatomia:**
- Fundo: `#0D0D0D` + scanlines 1.5% opacity
- Barra de acento topo: 6px, bg `#E01A5A`
- Logo: `top: 80px, left: 48px`
- Stack de 3 stats: cada um com `border-top: 3px solid #F5C100` (primeiro) / `1px solid rgba(245,193,0,0.15)` (demais), padding 40px vertical
  - Número: Barlow Condensed 900, 144px, cor `#F5C100`
  - Label: Barlow 400, 32px, `rgba(255,255,255,0.5)`
- Rodapé: pergunta de CTA + subtexto link na bio

**Stats padrão da marca:**
```
+200  Clientes ativos
48h   Para ir ao ar
3×    Mais leads em média
```

---

## Processo de produção por tipo

### Para posts tipográficos (P01, P07)
1. Definir a afirmação principal — máximo 4 palavras por linha
2. Identificar a palavra de impacto → aplicar magenta + italic
3. Escrever subtexto de apoio — máximo 12 palavras
4. Redigir caption com 1-2 linhas + CTA + hashtags

### Para posts de dado (P02)
1. Selecionar 1 número relevante e verificável
2. Contextualizar em headline curta (máx. 5 palavras)
3. Adicionar subtexto explicativo (1 frase)
4. Badge de contexto no header (ex: "Entrega garantida", "Resultado real")

### Para carrosséis (P03 + P04)
1. Definir o tema e número de slides (recomendado: 4-6 incluindo capa e CTA final)
2. Capa: pergunta ou afirmação provocativa
3. Slides internos: 1 ponto por slide, corpo máx. 3 linhas, sempre com callout de solução
4. Último slide: CTA com botão/ação clara

### Para prova social (P06)
1. Obter depoimento real com autorização do cliente
2. Identificar o resultado específico → será o destaque amarelo
3. Extrair 1-2 frases do depoimento (máx. 52 chars por linha)
4. Coletar: nome completo, tipo de negócio, cidade

---

## Regras de copy para social

| ✅ Usar | ❌ Evitar |
|---|---|
| "Apareça no Google" | "SEO otimizado" |
| "Sua página no ar em 2 dias" | "Soluções digitais ágeis" |
| "Você fala com quem faz" | "Time especializado" |
| "Clientes novos vieram do site" | "Aumentamos sua presença online" |
| Nome + cidade do cliente | "Um cliente nosso" |
| Número específico | "Muitos clientes" |

---

## Paleta de uso por tipo de post

| Tipo | Fundo principal | Destaque | Textura |
|---|---|---|---|
| Provocação | `#0D0D0D` | `#F5C100` + `#E01A5A` | Scanlines |
| Dado / Stat | `#F5C100` | `#0D0D0D` + `#E01A5A` | Halftone |
| Carrossel capa | `#1A1A1A` | `#F5C100` + `#E01A5A` | Halftone branco |
| Carrossel slide | `#0D0D0D` | `#F5C100` | Geométrico |
| CTA | `#E01A5A` | `#FFFFFF` + `#F5C100` | Watermark |
| Prova social | `#1A1A1A` | `#F5C100` | Nenhuma |
| Verdade | `#F5C100` | `#0D0D0D` + `#E01A5A` | Grid |
| Story CTA | `#F5C100` | `#0D0D0D` + `#E01A5A` | Halftone |
| Story Stats | `#0D0D0D` | `#F5C100` | Scanlines |

---

## Cadência semanal sugerida

```
SEG   ████ Provocação          (P01 ou P07)
TER   ████ Educativo           (Carrossel P03+P04)
QUA   ████ Dado / Stat         (P02)
QUI   ████ CTA direto          (P05)
SEX   ████ Case / Resultado    (P06)
SÁB   ░░░░ Story               (S01 ou S02)
DOM   —    Off
```

**Volume:** 5–6 posts/semana + 1–2 stories.
**Horários recomendados:** Seg–Sex 8h ou 12h (pico de engajamento B2C local).

---

## Hashtags por tipo

**Base (sempre incluir):**
```
#w2agencia #presencadigital #agenciadigital #pequenasempresas #mei
```

**Por tipo de post:**
- Provocação: `#marketingdigital #vendasonline #digitalmarketing`
- Dado/Stat: `#resultados #crescimento #landingpage`
- Carrossel: `#dicasdigital #aprenda #google #seo`
- CTA: `#diagnósticogratis #vamosfalar #whatsapp`
- Prova Social: `#casesucesso #clientesatisfeito #resultado`

**Geolocalização (SP):**
```
#agenciaSP #saopaulodigital #negocioSP
```

---

*Para referência visual de todos os templates ao vivo, abra `Social Posts.html` no browser.*
