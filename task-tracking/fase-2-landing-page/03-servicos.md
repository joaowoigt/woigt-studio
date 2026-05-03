# Task 2.03 — Serviços

**Fase:** 2 — Landing page
**Status:** ✅ Concluída — 2026-05-03

## Objetivo

Seção de serviços com os 4 cards da agência.

## Escopo

- [x] Fundo grafite (`#1A1A1A`) — conforme protótipo
- [x] 4 cards: Branding, Landing Page, Kit Digital, Gestão Mensal
- [x] Cards com grid layout, borda exterior amarela sutil
- [x] Sem border-radius, sem sombras suaves
- [x] Cada card: número sequencial, título em Barlow Condensed 900, subtítulo, descrição, preço
- [x] Grid 4 colunas em desktop, 2 colunas em tablet, 1 coluna em mobile
- [x] Badge "POPULAR" no Kit Digital (magenta, rotacionado)
- [x] Hover: fundo amarelo em cards normais, magenta no destaque

## Referências

- Protótipo: `d:/woigt-studio/design_handoff_w2agencia/Landing Page.html`

## Como Testar (QA Automatizado)

Script: `projects/qa-automation/tests/w2-agencia/task-03-services.spec.js`

Para re-executar:
```bash
cd projects/qa-automation && npx playwright test tests/w2-agencia/task-03-services.spec.js --reporter=list
```

Cobertura: 13 testes — fundo, eyebrow, título, acento magenta, 4 cards, badge POPULAR, preços, mobile.
Última execução: 2026-05-03 — ✅ PASSED (13/13)
