# Pendências — w² Agência Site

Itens que precisam de decisão ou ação de Woigt antes de ir ao ar.
Criado em: 2026-05-03

---

## 🔴 Bloqueadores (sem isso o site não vai ao ar)

### 1. Número de WhatsApp real
- **Onde está:** `app/components/CtaFooter.tsx` — botão "Falar no WhatsApp"
- **Hoje:** `https://wa.me/5511999999999` (placeholder)
- **Ação:** Substituir pelo número real da agência (ou pessoal do Woigt enquanto não tem número da empresa)

### 2. E-mail de contato real
- **Onde está:** `app/components/CtaFooter.tsx` — botão "Enviar e-mail"
- **Hoje:** `oi@w2agencia.com.br` (placeholder)
- **Ação:** Confirmar se vai usar esse domínio ou outro. Se não tiver o domínio ainda, usar Gmail temporariamente.

### 3. Links de Instagram e LinkedIn
- **Onde estão:** `app/components/CtaFooter.tsx` — coluna Contato no footer
- **Hoje:** `href="#contato"` (âncoras genéricas)
- **Ação:** Fornecer URLs dos perfis quando estiverem criados

---

## 🟡 Importantes antes do lançamento

### 4. Depoimentos reais na seção "Prova Social"
- **Onde está:** `app/components/Testimonials.tsx`
- **Hoje:** 3 depoimentos fictícios do protótipo (Marcela T., Ricardo O., Camila N.)
- **Ação:** Substituir por depoimentos reais de clientes existentes:
  - **Josi Fit** — cliente concluído, pode pedir depoimento
  - **Andreza Crochê** — cliente em andamento, verificar se já tem depoimento
  - Terceiro: cliente ou parceiro que queira participar como early adopter

### 5. CNPJ real no footer
- **Onde está:** `app/components/CtaFooter.tsx` — copyright no rodapé
- **Hoje:** `CNPJ 00.000.000/0001-00` (placeholder)
- **Ação:** Preencher quando a empresa estiver aberta formalmente (ou remover até lá)

### 6. Stats reais na seção Hero
- **Onde estão:** `app/components/Hero.tsx` — barra de stats preta
- **Hoje:** `+200 Clientes ativos`, `48h Para ir ao ar`, `3× Mais leads em média`, `100% Feito por quem faz`
- **Observação:** `+200` é número do protótipo e não condiz com a realidade da agência. Sugestão:
  - Mudar para algo que faça sentido agora: número de projetos entregues, anos de experiência, % de satisfação, etc.
  - Ou ajustar framing para ser aspiracional mas crível

---

## 🟢 Pós-lançamento (pode ir ao ar sem isso)

### 7. Showcase animado de projetos no Hero
- **O quê:** O protótipo tem um carrossel animado de projetos à direita do hero
- **Hoje:** Não implementado — hero está só com texto (conforme task 2.02)
- **Quando implementar:** Após ter 3+ projetos concluídos para mostrar (Josi Fit, Entrelaçada, próximo)

### 8. Formulário de contato
- **O quê:** Ao clicar em "Diagnóstico", atualmente vai para a seção CTA com botões
- **Quando implementar:** Se quiser capturar leads diretamente no site (vs. WhatsApp direto)

---

## 📋 Resumo de ações por prioridade

| # | Ação | Urgência | Responsável |
|---|------|----------|-------------|
| 1 | WhatsApp real | 🔴 Bloqueador | Woigt |
| 2 | E-mail real | 🔴 Bloqueador | Woigt |
| 3 | Instagram + LinkedIn URLs | 🔴 Bloqueador | Woigt + irmão |
| 4 | Depoimentos reais | 🟡 Importante | Woigt (pedir para clientes) |
| 5 | CNPJ real | 🟡 Importante | Woigt (quando abrir empresa) |
| 6 | Stats reais | 🟡 Importante | Woigt (definir números) |
| 7 | Showcase de projetos | 🟢 Pós-lançamento | Dev (depois de ter projetos) |
| 8 | Formulário de contato | 🟢 Pós-lançamento | Dev (se quiser) |
