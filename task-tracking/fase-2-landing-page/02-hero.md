# Task 2.02 — Hero

**Fase:** 2 — Landing page
**Status:** Pendente

## Objetivo

Seção hero da landing page — a primeira dobra, impacto máximo.

## Escopo

- [x] Fundo amarelo (`#F5C100`), full-width, full-height ou altura generosa
- [x] Headline massiva: Barlow Condensed 900 uppercase, texto preto, leading apertado (~0.9)
- [x] Subheadline em Barlow 500
- [x] CTA primário: botão preto, texto branco, sem border-radius, borda 3px solid preto
- [x] Barra de stats abaixo do headline (ex: N projetos entregues, N clientes, etc.)
- [x] Sem imagens decorativas — tipografia faz o layout

## Referências

- Protótipo: `d:/woigt-studio/design_handoff_w2agencia/Landing Page.html`

## Status

✅ Concluída — 2026-05-03

## Como Testar (QA Automatizado)

Script: `projects/qa-automation/tests/w2-agencia/task-02-hero.spec.js`

Para re-executar:
```bash
cd projects/qa-automation && npx playwright test tests/w2-agencia/task-02-hero.spec.js --reporter=list
```

Cobertura: 16 testes — fundo amarelo, eyebrow, headline, acento magenta, body text, CTAs, stats bar (4 números), mobile.
Última execução: 2026-05-03 — ✅ PASSED (16/16)
