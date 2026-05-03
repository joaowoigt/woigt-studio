# Task 2.04 — Como Funciona

**Fase:** 2 — Landing page
**Status:** ✅ Concluída — 2026-05-03

## Objetivo

Seção de processo em 3 passos.

## Escopo

- [x] 3 passos numerados em Barlow Condensed 900 (números grandes 88px como elemento visual)
- [x] Cada passo: número decorativo, título amarelo, descrição muted
- [x] Borda amarela no topo de cada passo (3px)
- [x] Layout 3 colunas em desktop, 1 coluna em mobile
- [x] Sem ilustrações — tipografia e numeração fazem o design

## Referências

- Protótipo: `d:/woigt-studio/design_handoff_w2agencia/Landing Page.html`

## Como Testar (QA Automatizado)

Script: `projects/qa-automation/tests/w2-agencia/task-04-how-it-works.spec.js`

Para re-executar:
```bash
cd projects/qa-automation && npx playwright test tests/w2-agencia/task-04-how-it-works.spec.js --reporter=list
```

Cobertura: 10 testes — fundo preto, eyebrow, título, acento amarelo, 3 passos, bordas amarelas, mobile.
Última execução: 2026-05-03 — ✅ PASSED (10/10)
