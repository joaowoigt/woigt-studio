# Task 2.05 — Prova Social / Depoimentos

**Fase:** 2 — Landing page
**Status:** ✅ Concluída — 2026-05-03 (com pendência — ver abaixo)

## Objetivo

Seção de depoimentos e casos de uso.

## Escopo

- [x] Cards de depoimento com borda, nome + cargo/empresa
- [x] 3 depoimentos ficcionais (Marcela T., Ricardo O., Camila N.) conforme protótipo
- [x] Avatar circular com inicial em amarelo
- [x] Fundo grafite conforme protótipo
- [ ] ⚠️ PENDENTE: substituir depoimentos fictícios por reais (Josi Fit, Andreza Crochê) — ver lista de pendências

## Referências

- Protótipo: `d:/woigt-studio/design_handoff_w2agencia/Landing Page.html`
- Cases disponíveis: Josi Fit (concluído), Entrelaçada (em andamento), Splitpost (produto próprio)

## Como Testar (QA Automatizado)

Script: `projects/qa-automation/tests/w2-agencia/task-05-testimonials.spec.js`

Para re-executar:
```bash
cd projects/qa-automation && npx playwright test tests/w2-agencia/task-05-testimonials.spec.js --reporter=list
```

Cobertura: 13 testes — fundo grafite, eyebrow, título, acento magenta, 3 depoimentos, avatares, mobile.
Última execução: 2026-05-03 — ✅ PASSED (13/13)
