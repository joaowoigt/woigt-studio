# Posts Studio — Plano de Implementação

**Projeto:** Ferramenta proprietária da w² Agência para criação padronizada de posts on-brand.
**Data:** 2026-05-15
**Status:** Planning
**Owner técnico:** Woigt
**Owner operacional:** Irmão (commercial/marketing)

---

## 1. Visão Geral

Estúdio interno (Next.js + Satori) que renderiza posts a partir de templates JSX **rígidos por design**. O brand é o próprio componente — não há como sair dele. O irmão preenche campos, escolhe variantes pré-aprovadas e exporta PNG pronto para publicar.

**Por que construir em vez de usar Canva:**
- Stack já dominado (Next.js + Tailwind + Vercel)
- Brand enforcement total (impossível violar)
- Zero custo recorrente
- Vira diferencial e case da w² ("usamos nossa própria ferramenta")
- Multi-cliente vira config, não conta nova

**Por que aceitar o trade-off de menos flexibilidade:**
- Velocidade de criação > flexibilidade visual (irmão preenche 4 campos vs. desenhar do zero)
- Consistência é o produto da agência

---

## 2. Decisões Cravadas

| Decisão | Escolha |
|---|---|
| Modelo de posicionamento | **Variantes radio por template** (3-5 layouts pré-aprovados, sem drag-drop) |
| Primeiro brand do MVP | **w² Agência** (brand Explosão aprovado, baixo risco, case próprio) |
| Editáveis pelo irmão | Textos (título + subtítulo), upload de imagem com crop fixo, variante de cor (paletas do brand), CTA/handle/URL |
| Engine de render | **Satori + Resvg** via `@vercel/og` (JSX → PNG, sem Puppeteer) |
| Hospedagem | Vercel (free tier) |
| Localização do código | `d:/w2-posts-studio/` (repo separado) |
| Auth no MVP | Link público com slug obscuro (`/studio/[token]`) — sem login no v1 |
| Foco do MVP | Desktop-only (irmão usa do PC para criar posts) |

---

## 3. Stack Técnica

```
Next.js 15 (App Router, RSC)
Tailwind v4 (mesma versão de d:/w2-project/)
@vercel/og (Satori + Resvg) — render JSX → PNG
shadcn/ui — formulários e UI
React Hook Form + Zod — validação de inputs
TypeScript
Vercel — hosting
```

**Sem backend persistente no MVP.** Upload de imagem fica em memória (data URL) até exportar. Se precisar de histórico, adiciona Vercel Blob na v2.

---

## 4. Arquitetura

```
d:/w2-posts-studio/
├── src/
│   ├── brands/
│   │   └── w2-agencia/
│   │       ├── tokens.ts          # cores, fontes, espaçamentos
│   │       ├── fonts.ts           # carrega TTF/OTF para Satori
│   │       ├── assets.ts          # logos, ícones (importados de d:/woigt-studio/brand-assets/)
│   │       └── templates/
│   │           ├── feed-quote/
│   │           │   ├── variants.tsx    # 3 layouts pré-aprovados
│   │           │   ├── schema.ts       # Zod (campos + limites)
│   │           │   └── meta.ts         # nome, descrição, aspect ratio
│   │           ├── feed-tip/
│   │           ├── feed-case/
│   │           └── feed-cta/
│   ├── app/
│   │   ├── studio/
│   │   │   └── [brand]/[template]/page.tsx   # formulário + preview live
│   │   └── api/render/route.ts               # POST → PNG download
│   ├── components/
│   │   ├── studio-form.tsx        # gera form a partir do schema Zod
│   │   ├── live-preview.tsx       # mesmo JSX que Satori renderiza
│   │   └── variant-picker.tsx     # radio de variantes
│   └── lib/
│       ├── render.ts              # Satori → Resvg → Buffer PNG
│       └── image-crop.ts          # processa upload (resize, object-fit)
└── package.json
```

**Princípio de design:** o mesmo componente JSX é usado pelo `live-preview` (no browser) e pelo `api/render` (Satori server-side). Garante WYSIWYG.

**Brand isolation:** cada cliente vira uma pasta em `src/brands/`. Adicionar novo cliente = copiar pasta + trocar tokens + adicionar/ajustar templates.

---

## 5. Templates do MVP (w² Agência)

5 templates × 3 variantes = 15 combinações.

### 5.1 `feed-quote` — Frase/insight de marca
**Uso:** "Marca não é logo, é experiência" / quotes de posicionamento.
**Aspect ratio:** 1:1 (1080×1080)
**Variantes:**
- A) Texto centro + fundo cor sólida + logo rodapé
- B) Texto topo + faixa accent + assinatura "— w² Agência" rodapé
- C) Texto centralizado + textura/ruído de fundo + logo discreto canto

**Campos:** quote (max 120 char), assinatura opcional (max 30 char), variante de cor (3 paletas)

### 5.2 `feed-tip` — Dica/lista numerada
**Uso:** "3 erros que pequenos negócios cometem no Instagram"
**Aspect ratio:** 4:5 (1080×1350) — formato Instagram preferido
**Variantes:**
- A) Título topo + lista numerada (3 itens) + CTA rodapé
- B) Título lateral esquerdo + lista direita + accent
- C) Título centro + lista 2 colunas

**Campos:** título (max 60 char), 3 itens de lista (max 50 char cada), CTA (max 40 char)

### 5.3 `feed-case` — Antes/depois ou social proof
**Uso:** "Cliente X aumentou 300% o engajamento" / case visual
**Aspect ratio:** 4:5 (1080×1350)
**Variantes:**
- A) Foto à esquerda + métrica destaque direita + nome cliente
- B) Foto fundo + overlay escuro + métrica + nome
- C) Split 50/50 — antes/depois lado a lado

**Campos:** upload de imagem, métrica destaque (max 20 char), descrição (max 80 char), nome do cliente

### 5.4 `feed-cta` — Oferta/chamada para ação
**Uso:** "Diagnóstico gratuito de presença digital" / oferta de serviço
**Aspect ratio:** 1:1 (1080×1080)
**Variantes:**
- A) Headline grande topo + benefícios curtos + CTA box rodapé
- B) Headline centro + ícone/asset accent + CTA texto
- C) Background imagem + overlay + headline + CTA

**Campos:** headline (max 50 char), subline opcional (max 80 char), CTA (max 25 char), URL/handle (max 40 char), upload opcional de imagem

### 5.5 `story-vertical` — Story para Instagram/LinkedIn
**Uso:** Story padrão — anúncio rápido, quote em formato vertical, CTA com link.
**Aspect ratio:** 9:16 (1080×1920)
**Variantes:**
- A) Quote/headline centro + logo topo + assinatura rodapé (safe zones respeitadas para UI nativa do IG)
- B) Imagem fundo + overlay gradiente + headline + CTA "arraste pra cima" / link sticker placeholder
- C) Split horizontal — bloco cor topo (headline) + bloco imagem baixo (foto/asset) + CTA central

**Campos:** headline (max 80 char), subline opcional (max 60 char), CTA (max 25 char), upload opcional de imagem, variante de cor

**Nota:** Layout respeita safe zones do Instagram Stories (topo 220px e rodapé 250px reservados para UI nativa). Textos importantes ficam na área central segura.

---

## 6. Fases e Tasks

### Fase 0 — Setup & Proof of Concept (1-2 dias)
**Objetivo:** Provar que Satori renderiza JSX com fonte custom + imagem corretamente.

- [ ] **0.1** Criar repo `d:/w2-posts-studio/` (Next.js 15 + Tailwind v4 + TS)
- [ ] **0.2** Configurar deploy Vercel (conectar repo, deploy preview funcionando)
- [ ] **0.3** Importar brand tokens de w² (`d:/woigt-studio/brand/`) para `src/brands/w2-agencia/tokens.ts`
- [ ] **0.4** Carregar fontes custom do brand (TTF/OTF como arrayBuffer para Satori)
- [ ] **0.5** PoC: renderizar 1 JSX simples ("Hello w²" com fonte do brand) via `/api/render` → PNG
- [ ] **0.6** Validar: PNG baixado, fonte aplicada, cor correta

**Critério de saída:** PNG 1080×1080 baixa com texto, fonte e cor do brand w².

### Fase 1 — Primeiro Template End-to-End (2-3 dias)
**Objetivo:** `feed-quote` 100% funcional com 3 variantes, preview live e export.

- [ ] **1.1** Definir schema Zod do template (campos + limites)
- [ ] **1.2** Implementar 3 variantes JSX (`variants.tsx`)
- [ ] **1.3** Construir `studio-form` que gera UI a partir do schema (input texto, char counter, radio de variante, radio de cor)
- [ ] **1.4** Construir `live-preview` que renderiza o mesmo JSX no browser (clipping/escala para caber na tela)
- [ ] **1.5** API `/api/render` aceita POST com campos + variante → retorna PNG
- [ ] **1.6** Botão "Exportar PNG" no studio → trigger download nomeado (`w2_feed-quote_2026-05-15.png`)
- [ ] **1.7** Validar paridade visual: o que aparece no preview é idêntico ao PNG baixado

**Critério de saída:** Irmão acessa URL, preenche 1 quote, escolhe variante e cor, baixa PNG pronto para Instagram.

### Fase 2 — Restante dos Templates (4-5 dias)
**Objetivo:** `feed-tip`, `feed-case` (com upload), `feed-cta` (com upload opcional), `story-vertical`.

- [ ] **2.1** Implementar `feed-tip` (schema + 3 variantes + meta)
- [ ] **2.2** Implementar `feed-case` (schema + 3 variantes + meta) — inclui upload de imagem
- [ ] **2.3** Implementar lógica de upload com crop fixo (object-cover, dimensões pré-definidas por variante)
- [ ] **2.4** Implementar `feed-cta` (schema + 3 variantes + meta)
- [ ] **2.5** Implementar `story-vertical` (schema + 3 variantes + meta) — 9:16, respeitando safe zones do Instagram
- [ ] **2.6** Landing `/studio/w2-agencia/` lista todos os templates como cards clicáveis (agrupados por aspect ratio: feed / story)

**Critério de saída:** Todos os 5 templates funcionam com export PNG. Upload de imagem renderiza corretamente no Satori. Story 9:16 respeita safe zones.

### Fase 3 — UX & Polish (1-2 dias)
**Objetivo:** Ferramenta agradável de usar, com guardrails que evitam erros.

- [ ] **3.1** Char counter em todos os campos + bloqueio ao exceder limite
- [ ] **3.2** Avisos visuais quando texto fica grande demais para o layout (overflow detection)
- [ ] **3.3** Naming automático do arquivo exportado (`[brand]_[template]_[YYYY-MM-DD].png`)
- [ ] **3.4** Loading state no botão "Exportar PNG" + tratamento de erro
- [ ] **3.5** Página inicial `/studio/` lista brands disponíveis (no MVP só w²)
- [ ] **3.6** Documentar fluxo em 1 página (`docs/como-usar.md` no repo + cópia em `d:/woigt-studio/posts-studio/`)

**Critério de saída:** Irmão consegue criar 5 posts sem precisar perguntar nada.

### Fase 4 — Multi-Brand Prep (1 dia)
**Objetivo:** Refatorar para garantir que adicionar Splitpost (próximo brand) é trabalho de horas, não dias.

- [ ] **4.1** Auditar acoplamento brand-específico fora de `src/brands/w2-agencia/`
- [ ] **4.2** Garantir que templates referenciam apenas tokens via prop (não imports diretos)
- [ ] **4.3** Adicionar `src/brands/splitpost/` como stub com 1 template para validar o caminho
- [ ] **4.4** Documentar checklist "Como adicionar novo brand" (`docs/adicionar-brand.md`)

**Critério de saída:** Adicionar novo brand é seguir um checklist de ~6 passos.

---

## 7. Decisões Pendentes

| Decisão | Opções | Quando decidir |
|---|---|---|
| **Carrossel multi-slide?** | Não inclui no v1 (cada slide é post separado) | v2 — só se virar gargalo real |
| **Histórico de posts gerados** | Sem persistência (v1) vs. Vercel Blob salva últimos 50 (v2) | v2, baseado em uso real |
| **Auth/proteção** | Link com slug obscuro (v1) vs. NextAuth com magic link (v2) | v2, se houver risco de vazamento |

**Decisões resolvidas em 2026-05-15:**
- ✅ Repo em `d:/w2-posts-studio/` (separado)
- ✅ Story 9:16 incluído no MVP como 5º template (`story-vertical`)
- ✅ Domínio: URL Vercel padrão no v1 (sem subdomain customizado)

---

## 8. Riscos & Mitigações

| Risco | Impacto | Mitigação |
|---|---|---|
| **Satori não suporta todo CSS** | Pode quebrar layouts complexos (grid avançado, filters, etc.) | Restringir a flexbox + posicionamento absoluto + box-shadow. Validar cada variante no PoC. |
| **Fontes custom não carregam corretamente** | Tipografia errada = brand quebrado | Carregar TTF/OTF via arrayBuffer no boot da rota. Testar na Fase 0. |
| **Upload de imagem pesada degrada render** | Lentidão no preview + render demora | Resize client-side antes de enviar (max 2048px lado maior). |
| **Irmão acha mais fácil voltar pro Canva** | Ferramenta morre por não-uso | Onboarding presencial + checklist visual + métrica de uso semanal. |
| **Você vira blocker único de manutenção** | Bug pequeno trava produção da agência | Documentar tudo. Manter código simples (no over-engineering). Build = deploy. |
| **Over-engineering: virar editor genérico** | Projeto cresce, nunca termina | Régua: se uma feature parece "tipo Canva", recusar. Constraints são o produto. |
| **Volume real exigir batch automático** | Estúdio fica gargalo | Reusar o `api/render` como API pública na v2 — input JSON, output PNG. |

---

## 9. Métricas de Sucesso

**MVP (após Fase 3):**
- Irmão cria 10 posts da w² sozinho, sem perguntar nada, em <1 hora
- Tempo médio por post: <5 min (do brief mental ao PNG exportado)
- Zero violação de brand observada nos 10 posts (cores, fontes, espaçamentos)

**3 meses pós-MVP:**
- 2º brand (Splitpost) adicionado em <2 dias
- ≥30 posts/mês gerados pela ferramenta (substituindo Canva/Stitch)
- Custo recorrente: $0 (Vercel free tier)

---

## 10. Próximos Passos

1. **Quebrar Fase 0 em tasks executáveis** via skill `plan-to-tasks`
2. **Iniciar Fase 0** — setup do repo `d:/w2-posts-studio/` + PoC de Satori com fonte do brand
3. **Validar PoC antes de avançar** — se Satori não renderizar fontes/cores corretamente, voltar pra prancheta antes de investir em templates

---

## Apêndice: Referências de Brand (w² Agência)

- Brandbook: `d:/woigt-studio/brand/brand-book.md`
- Voice guide: `d:/woigt-studio/brand/voice-guide.md`
- Social media guide: `d:/woigt-studio/brand/social-media-guide.md`
- Assets visuais: `d:/woigt-studio/brand-assets/`
- Design handoff: `d:/woigt-studio/design_handoff_w2agencia/`
