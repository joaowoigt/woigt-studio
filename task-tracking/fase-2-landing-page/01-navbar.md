# Task 2.01 — Navbar

**Fase:** 2 — Landing page
**Status:** Pendente

## Objetivo

Implementar a navbar da landing page conforme `Landing Page.html`.

## Escopo

- [x] Fundo grafite (`#1A1A1A`), full-width
- [x] Logo W² à esquerda (SVG ou texto estilizado temporário)
- [x] Links de navegação centralizados com underline amarelo no hover/active
- [x] Botão CTA à direita: "Diagnóstico" — fundo amarelo, texto preto, sem border-radius
- [x] Sticky no scroll
- [x] Responsivo: menu hambúrguer em mobile

## Referências

- Protótipo: `d:/woigt-studio/design_handoff_w2agencia/Landing Page.html`

## Status

✅ Concluída — 2026-05-03

## Como Testar (QA Automatizado)

Script: `projects/qa-automation/tests/w2-agencia/task-01-navbar.spec.js`

Para re-executar:
```bash
cd projects/qa-automation && npx playwright test tests/w2-agencia/task-01-navbar.spec.js --reporter=list
```

Cobertura: 17 testes — fundo/borda, logo, links, CTA, sticky, mobile hambúrguer, menu aberto.
Última execução: 2026-05-03 — ✅ PASSED (17/17)
