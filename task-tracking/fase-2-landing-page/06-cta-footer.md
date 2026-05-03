# Task 2.06 — CTA Banner + Footer

**Fase:** 2 — Landing page
**Status:** ✅ Concluída — 2026-05-03 (com pendências — ver abaixo)

## Objetivo

CTA final e footer da landing page.

## Escopo

**CTA Banner:**
- [x] Fundo magenta (`#E01A5A`) com textura halftone dark
- [x] Headline "PRONTO PARA OCUPAR ESPAÇO?" — branco + amarelo
- [x] Corpo: "Diagnóstico gratuito. Sem compromisso."
- [x] Botão "Falar no WhatsApp" — fundo amarelo, texto preto, sem border-radius
- [x] Botão "Enviar e-mail" — transparente, borda branca
- [ ] ⚠️ PENDENTE: número WhatsApp real (hoje: placeholder 5511999999999)
- [ ] ⚠️ PENDENTE: e-mail real (hoje: oi@w2agencia.com.br — confirmar com Woigt)

**Footer:**
- [x] Fundo preto (`#0D0D0D`) com borda topo amarela sutil
- [x] Logo W² em amarelo + separador + "AGÊNCIA"
- [x] Tagline: "Presença digital para quem quer resultado, não reunião."
- [x] Coluna Serviços: links âncora para as seções
- [x] Coluna Contato: WhatsApp, E-mail, Instagram, São Paulo SP
- [x] Copyright "© 2026 w² Agência · CNPJ 00.000.000/0001-00"
- [ ] ⚠️ PENDENTE: CNPJ real quando abrir a empresa
- [ ] ⚠️ PENDENTE: links reais de Instagram e LinkedIn

## Referências

- Protótipo: `d:/woigt-studio/design_handoff_w2agencia/Landing Page.html`

## Como Testar (QA Automatizado)

Script: `projects/qa-automation/tests/w2-agencia/task-06-cta-footer.spec.js`

Para re-executar:
```bash
cd projects/qa-automation && npx playwright test tests/w2-agencia/task-06-cta-footer.spec.js --reporter=list
```

Cobertura: 18 testes — CTA fundo magenta, eyebrow, título, acento amarelo, 2 botões, footer fundo preto, logo, tagline, colunas, copyright, mobile.
Última execução: 2026-05-03 — ✅ PASSED (18/18)
