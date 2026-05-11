# w² Agência — Brand Assets · Prompts para Geração Manual

**Marca:** w² Agência
**Status do logo:** Aprovado · 9 SVGs em `brand/assets/logo/` + pattern + preview-all.html
**Contexto:** Brandbook completo em `brand/brand-book.md` · Paleta e tipografia travadas em `design-handoff-claude.md`

---

## Estratégia de cota

- **ChatGPT free** = 3 imagens/dia. Os 3 prompts marcados `[ChatGPT]` são os críticos da apresentação do brandbook.
- **Ideogram** = ~10–25/dia. Use pra peças com tipografia exata.
- **Nano Banana (Google AI Studio)** = livre. Use pra lifestyle e mood.
- **Privacy:** ative Temporary Chat / Activity Off antes de colar prompts (evita uso pra treinamento).

---

## Sequência sugerida

| # | Asset | Ferramenta | Cota | Salvar como |
|---|-------|------------|------|-------------|
| 1 | Hero shot manifesto da marca | ChatGPT | 1/3 | `brand/assets/01-hero-manifesto.png` |
| 2 | Aplicação em devices (laptop + celular) | ChatGPT | 2/3 | `brand/assets/02-aplicacao-devices.png` |
| 3 | Papelaria (cartão de visita + capa de proposta) | ChatGPT | 3/3 | `brand/assets/03-papelaria.png` |
| 4 | Post Instagram "VOCÊ EXISTE. NINGUÉM TE ACHA." | Ideogram | livre | `brand/assets/04-post-manifesto.png` |
| 5 | Mood board / lifestyle dos sócios | Nano Banana | livre | `brand/assets/05-lifestyle.png` |
| 6 | Pattern repetitivo W² (variação orgânica) | Ideogram (opcional) | livre | `brand/assets/06-pattern-organico.png` |

Logos SVG já estão em `brand/assets/logo/` — geração separada via Claude (não usar IA externa pra logo).

---

## Bloco de contexto da marca (cole no início de prompts ChatGPT)

```
CONTEXTO DA MARCA:
- Nome: w² Agência
- Categoria: agência de presença digital para pequenos negócios brasileiros (MEIs, microempresas, autônomos)
- Personalidade: bold, energético, direto, brasileiro, ousado
- Arquétipo: Outlaw com sombra de Sage (rebelde contra agência cara, mas consultivo)
- Paleta: amarelo elétrico #F5C100 (primário) · magenta #E01A5A (acento cirúrgico) · preto total #0D0D0D · branco #FFFFFF
- Tipografia: Barlow Condensed Black 900 em headlines (uppercase, leading 0.9-1.0) · Barlow regular em body
- Estilo visual: alto contraste, bordas 3-4px, sem sombras, sem gradientes, sem rounded corners (exceto avatares), tipografia faz o layout, sem ilustração decorativa
- Referências de espírito: Studio Feixen, Sagmeister & Walsh, Büro Destruct, streetwear brasileiro de qualidade (Piet, Pace), cartazes de São Paulo
- O que a marca NÃO é: corporativa · amadora · elitista · genérica · fofa
- Taglines aprovadas: "VOCÊ EXISTE. NINGUÉM TE ACHA." (hero) · "SEU CONCORRENTE JÁ APARECE." (provocação) · "Você fala com quem faz." (assinatura)
```

---

## Prompt 01 — Hero shot manifesto

**Ferramenta:** ChatGPT (https://chatgpt.com)
**Salvar como:** `brand/assets/01-hero-manifesto.png`
**O que estamos testando:** abertura visual do brandbook · capa de apresentação ao cliente · imagem que sintetiza "Explosão" em uma única foto editorial

--- PROMPT START ---

[COLE O BLOCO DE CONTEXTO ACIMA]

Create a photorealistic editorial hero image that captures the essence of the brand.

Scene: minimalist agency studio interior, late afternoon. Black concrete wall as the dominant background. On the wall, massive industrial yellow neon-style typography reads "VOCÊ EXISTE." on top line and "NINGUÉM TE ACHA." on bottom line — both in heavy condensed sans-serif font (Barlow Condensed Black style), uppercase, tight leading, the period after each phrase glowing slightly more saturated. The neon yellow color is exactly #F5C100 — vibrant and electric, not pale.

In the foreground, slightly out of focus: a single matte black workspace with a closed laptop, a white ceramic coffee mug, and a small magenta-colored stack of papers (pure #E01A5A magenta). No people. No other branding visible. No window light — only the neon as the dominant light source casting yellow ambient onto the workspace.

Composition: horizontal 16:9, eye-level perspective, the typography wall takes 70% of the frame. Cinematic dramatic lighting, slight chiaroscuro, photographic depth of field. The mood is brutalist editorial — bold, confident, slightly intimidating. Reference: think São Paulo gallery space meets industrial studio.

No text artifacts, no other logos, no people, no decorative illustrations. Sharp 90-degree angles, no rounded corners anywhere in the architecture.

--- PROMPT END ---

**Caveats validados em teste:**
- Texto longo borra. Se "NINGUÉM TE ACHA." sair errado, regenere. Caso persista, simplifique pra apenas "VOCÊ EXISTE." (1 linha) e mantém o impacto.
- Acento em "NINGUÉM" pode falhar — se rodar 2x e o "É" sair errado, aceite "NINGUEM" e adicione manualmente em pós-produção.
- Caso o ChatGPT recuse "neon" por moderação, reescreva como "industrial yellow letters painted on the wall, illuminated dramatically".

---

## Prompt 02 — Aplicação em devices

**Ferramenta:** ChatGPT (https://chatgpt.com)
**Salvar como:** `brand/assets/02-aplicacao-devices.png`
**O que estamos testando:** mostrar visualmente o tipo de entrega da agência · prova de competência via auto-referência · imagem central da seção "serviços" no brandbook PDF

--- PROMPT START ---

[COLE O BLOCO DE CONTEXTO ACIMA]

Create a photorealistic flat-lay top-down product mockup of an agency's work-in-progress desk.

Center of frame: a 14-inch matte black laptop, screen open and facing camera, displaying a yellow website hero section with massive condensed black uppercase headline "VOCÊ EXISTE. NINGUÉM TE ACHA." in pure black on yellow #F5C100 background. Below the headline on the screen, a small black rectangular button with the word "FALA COM A GENTE" in white, and a subtle horizontal divider in magenta #E01A5A. The website is clean, no decorative illustrations, no rounded corners on any UI element.

To the left of the laptop: an iPhone (matte black) with the screen showing an Instagram profile feed — three columns of square posts, each post is a high-contrast black/yellow/magenta composition, no images of people, only typographic posts. The Instagram bio at the top of the phone screen reads "Você existe. Ninguém te acha. A gente resolve." in compact rendering.

Surrounding props on a dark walnut wooden desk surface: a single pencil, a folded magenta-colored paper card, a small white ceramic espresso cup with black coffee, a notebook with a black leather cover.

Lighting: soft natural daylight from upper left, no harsh shadows, slight overhead diffused. Top-down 90-degree angle. Photographic, editorial product photography style. The colors must read accurately — saturated yellow, deep black, vibrant magenta accents.

No people, no faces, no other brand logos, no text artifacts on the wood surface, no decorative items beyond what's specified.

--- PROMPT END ---

**Caveats:**
- Tela do laptop pode renderizar texto borrado. Se "VOCÊ EXISTE. NINGUÉM TE ACHA." sair ilegível, aceite — o ponto da imagem é mostrar o sistema visual em uso, não a frase exata.
- Instagram feed mockup é genérico — GPT não vai conseguir replicar um feed real com fidelidade. Aceite o resultado se as cores e o ritmo do grid (preto/amarelo/magenta) estiverem coerentes.
- Se o magenta sair desbotado, reforce na próxima iteração: "vibrant saturated magenta — exactly Pantone Rubine Red, hex #E01A5A, do not desaturate".

---

## Prompt 03 — Papelaria (cartão de visita + capa de proposta)

**Ferramenta:** ChatGPT (https://chatgpt.com)
**Salvar como:** `brand/assets/03-papelaria.png`
**O que estamos testando:** touchpoint físico real · prova de profissionalismo · evidência de "agência grande, preço de quem cabe" — premium sem ser luxuoso

--- PROMPT START ---

[COLE O BLOCO DE CONTEXTO ACIMA]

Create a photorealistic editorial flat-lay of agency stationery.

Two main objects on a matte concrete-grey surface:

1. A black business card (90mm x 50mm landscape orientation), upper portion shows the wordmark "W² | AGÊNCIA" in compact condensed black sans-serif — W is yellow #F5C100, the superscript 2 is magenta #E01A5A, the divider line is white, the word AGÊNCIA is white with wide letter-spacing. Lower portion of the card shows three small text lines in white sans-serif: a name placeholder "JOÃO SOBRENOME", a role "SÓCIO", and a website "w2agencia.com.br". Card has crisp 90-degree corners, no rounded edges, matte black finish with slightly visible texture.

2. A folded yellow A4 proposal cover (#F5C100 background) lying partially open. The cover shows a massive condensed black uppercase headline "VOCÊ EXISTE." on top half, "NINGUÉM TE ACHA." on bottom half, both in pure black. A thin black horizontal rule separates them. In the bottom-right corner of the cover, a small "W²" mark in black with magenta superscript.

Compositional details: cards arranged at slight angle, the business card on top of the proposal corner. Soft natural daylight from above-left, casting subtle shadows. The whole composition reads as "premium without being luxurious — confident, contemporary, brazilian editorial design".

Top-down 90-degree perspective, square 1:1 framing, sharp focus throughout.

No people, no other logos, no decorative illustrations, no rounded corners on any element, no gradients.

--- PROMPT END ---

**Caveats:**
- Texto pequeno no cartão de visita vai sair borrado em parte — aceite se a hierarquia (W² em destaque + nome + role + site) estiver legível.
- Acento em "NINGUÉM" pode falhar — se acontecer, regenerar 1-2 vezes. Caso persista, ajustar manualmente em Photoshop/Affinity após receber o asset.

---

## Prompt 04 — Post Instagram manifesto

**Ferramenta:** Ideogram (https://ideogram.ai)
**Salvar como:** `brand/assets/04-post-manifesto.png`
**O que estamos testando:** template de post manifesto pra os 15% do feed que carregam afirmação forte · primeiro post de lançamento da conta

--- PROMPT START ---

Instagram post 1:1 square for "w² Agência".

Background: solid pure black #0D0D0D, edge to edge.

Typography (place exactly as described):
- Top eyebrow: tiny uppercase "W² · MANIFESTO" in monospace style, color yellow #F5C100, top-left corner with 80px margin
- Center headline (dominant element): massive Barlow Condensed Black 900 uppercase in two stacked lines:
  Line 1: "VOCÊ EXISTE."
  Line 2: "NINGUÉM TE ACHA."
  Color: bright yellow #F5C100. The period (.) at the end of each line in saturated magenta #E01A5A.
  Letter-spacing: tight (-2%). Line-height: 0.92.
- Bottom-right corner: small "W²" mark in yellow with magenta superscript 2, plus the word "AGÊNCIA" in white with wide letter-spacing — all small, 60px from bottom edge, signature-style

No decorative illustrations, no icons, no shadows, no gradients, no rounded corners. Brutalist editorial design. Sharp 2px borders if any framing is applied.

--ar 1:1

--- PROMPT END ---

**Caveats críticos (testado):**
- Mesmo o Ideogram pode duplicar palavras, trocar acentos, inverter cores entre linhas. **Sempre regenere 2-3 vezes** e escolha a melhor.
- Acentos: "VOCÊ" e "NINGUÉM" são os pontos de risco — se Ideogram errar 3 vezes seguidas, **pivote pra HTML+screenshot.mjs** (descrição abaixo).
- Pontos magenta: o Ideogram pode pintar a palavra inteira de magenta em vez de só o ponto. Se acontecer, refrasear o prompt: "the ONLY magenta element is the period dot at end of each line — everything else is yellow".

**Fallback definitivo (HTML+screenshot.mjs):**
Se Ideogram falhar em 3 tentativas, peça ao Vergil pra gerar um HTML com a tipografia exata + paleta + Barlow Condensed via Google Fonts, e capture com `node scripts/screenshot.mjs`. Resultado 100% fiel à marca.

---

## Prompt 05 — Mood board / lifestyle dos sócios

**Ferramenta:** Google AI Studio · Nano Banana (https://aistudio.google.com)
**Salvar como:** `brand/assets/05-lifestyle.png`
**O que estamos testando:** universo da marca · "quem somos" sem stock photo corporativa · atmosfera real de trabalho

--- PROMPT START ---

Brand: w² Agência — small Brazilian digital agency for small businesses, palette yellow electric / magenta / black / white, aesthetic bold and direct.

Lifestyle photograph capturing the world where the founders of w² work daily.

Customer profile of the founders: two brazilian men in their early thirties, one with focus on technology and one on commercial — they work side by side in a small studio.

Scene: small contemporary work studio in Brazil, late afternoon golden hour light coming through a single industrial window. A long wooden desk with two laptops side by side (closed or partially closed), two ceramic espresso cups, scattered papers with sketches, a single yellow Post-it note with handwritten brazilian portuguese marker writing visible but blurred. A small W² symbol painted or printed on the back wall in yellow. The wall behind is dark grey concrete.

Customer profile in scene: capture the studio FROM BEHIND or AT AN ANGLE that does not show faces. People can be seen from behind (back of head, shoulders) or only their hands visible on the keyboard / sketching. No frontal face shots.

Mood: focused, productive, contemporary, energetic but calm — the moment between deep work and break.
Dominant palette: warm wood tones, dark grey wall, yellow accents (lamp, post-it, painted symbol), small magenta accent (a folder, a marker).
Lighting: soft natural golden hour, no flash, no studio lights.
No people with visible faces, no logos from other brands, no clichéd "creative agency" stock photo elements (no exposed brick walls without context, no neon "create" signs, no plants in clay pots posing).

Composition: horizontal 16:9.

--- PROMPT END ---

**Caveats:**
- Nano Banana às vezes interpreta paleta de forma livre — verifique se as cores predominantes batem (preto, amarelo accent, magenta accent).
- Pode insistir em mostrar rosto. Se acontecer, refrase: "people are positioned WITH BACKS TO CAMERA — only backs of heads, hands, and shoulders visible — no facial features at all".
- Lifestyle gerada por IA pode ter "ar fake" — use 2-3 imagens em sobreposição com baixa opacidade no brandbook em vez de uma única hero, fica mais "real".

---

## Prompt 06 — Pattern orgânico (variação opcional)

**Ferramenta:** Ideogram (https://ideogram.ai)
**Salvar como:** `brand/assets/06-pattern-organico.png`
**O que estamos testando:** variação orgânica do pattern W² pra contextos onde o tile geométrico do SVG fica seco demais (capa de podcast, fundo de vídeo, banner de campanha emocional)

> **Nota:** o pattern primário é o SVG já gerado em `brand/assets/logo/pattern-w2-tile.svg`. Este aqui é uma variação orgânica raster — opcional.

--- PROMPT START ---

seamless repeating pattern, abstract typographic graffiti texture inspired by the letter "W" with a small superscript "2", chaotic but structured layout, yellow #F5C100 and magenta #E01A5A on solid black #0D0D0D background, brutalist editorial style, hand-painted feel mixed with stencil precision, tileable, flat brand asset, no shadows, no gradients

--ar 1:1

--- PROMPT END ---

**Caveats:**
- Pattern orgânico via IA raramente fica perfeitamente tileable — teste tiling em Photoshop/Affinity antes de usar. Se a emenda aparecer, peça ao Vergil pra fazer a costura via SVG.

---

## Após gerar todos os assets

1. Salvar PNGs com nomes exatos da tabela acima em `brand/assets/`
2. Avisar Vergil — ele lê todos, avalia contra os Critérios de Aprovação da skill, e:
   - Se 100% aprovados → integra no brand-book.md (Module 4 — Visual Direction recebe os mockups)
   - Se algum reprovado → ajusta prompt e refaz
3. Logos SVG já estão em `brand/assets/logo/` — geração separada via Claude (esta skill)

---

## Critérios de aprovação (checklist por imagem)

Antes de aprovar qualquer asset:

- [ ] Bate com a paleta da w² (amarelo elétrico + magenta + preto dominam — nada de cor estranha)
- [ ] Transmite a personalidade definida no Module 2 (bold, direto, ousado, brasileiro)
- [ ] Tipografia, quando presente, parece Barlow Condensed Black ou família próxima
- [ ] Funciona em fundo branco E em fundo escuro do brandbook PDF
- [ ] Tem resolução suficiente pro uso pretendido (mínimo 1080px no lado menor pra impressão; 1920px pra hero web)
- [ ] Não contradiz os anti-padrões visuais (sem gradiente pastel, sem ilustração fofa, sem stock photo corporativa, sem rounded corners desnecessários)
- [ ] Acentuação correta em qualquer texto visível (VOCÊ, AGÊNCIA, NINGUÉM) — se sair errada, fix em pós ou descarte
- [ ] Cliente final reconheceria como "premium" sem parecer "luxuoso/elitista"

---

## Decisão sobre cota: priorizar os 3 do ChatGPT

Se você só consegue rodar 3 prompts no ChatGPT hoje, escolha nesta ordem:

1. **Hero shot manifesto (Prompt 01)** — sem isso o brandbook não tem capa visual
2. **Papelaria (Prompt 03)** — touchpoint físico real, vende premium na primeira reunião com cliente
3. **Aplicação em devices (Prompt 02)** — auto-referência, mostra escopo de entrega

Se sobrar uma cota só, **pula o 02** — Ideogram + Nano Banana cobrem o resto sem comprometer a qualidade do brandbook.
