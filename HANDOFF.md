# w² Agência — Handoff de Sessão

**Data:** 2026-05-03
**Status:** Design aprovado. Aguardando export do Claude Design para iniciar implementação.

---

## O que foi decidido nesta sessão

- **w² Agência é a prioridade principal** de Woigt — acima do Splitpost, acima de tudo
- Shadowpages Manager permanece no autopiloto, sem foco até a agência estar lançada
- Splitpost em last-chance: plano mais barato + dashboard de posts prontos para copiar/colar (baixa prioridade)
- Andreza Crochê é o projeto de referência técnica da agência — criticidade máxima em todos os aspectos

---

## Estado atual da w² Agência

| Item | Status |
|------|--------|
| Nome | **w² Agência** — definido |
| Brand direction | **"Explosão" (Opção C)** — aprovada |
| Design handoff | Completo em `design-handoff-claude.md` |
| Design exportado (HTML/CSS) | **Pendente — Woigt vai exportar do Claude Design** |
| Landing page | Não implementada |
| Perfis sociais | Não criados |
| Domínio | A registrar: `w2agencia.com.br` |
| CRM | A configurar (HubSpot free) |
| E-mail marketing | A configurar (Brevo) |

---

## Próxima sessão — O que fazer

### Pré-requisito (Woigt faz antes de abrir a sessão)
- [ ] Exportar o design do Claude Design (HTML/CSS ou arquivos de assets)
- [ ] Ter os arquivos salvos em `d:/woigt-studio/brand-options/` ou pasta equivalente

### Agenda da próxima sessão (em ordem)
1. **Revisar o export** — conferir se as 3 opções de brand (option-a, option-b, option-c "Explosão") estão corretas e completas
2. **Implementar a landing page** com `/frontend-design` — usar `design-handoff-claude.md` como spec técnica
3. **Gerar logo SVG** — extrair do HTML ou recriar como SVG standalone (W² | AGÊNCIA)
4. **Criar assets para perfis sociais** — avatar (ícone W²), banner Instagram, banner LinkedIn
5. **Configurar perfis** (se houver tempo) — Instagram e LinkedIn da agência

---

## Brand DNA — Resumo para implementação

### Identidade
- **Nome:** w² Agência
- **Tagline:** "Você fala com quem faz."
- **Personalidade:** Bold, energético, direto. Brasileiro. Sem enrolação.
- **Público:** MEIs e microempresas brasileiras

### Paleta (não negociável)
| Role | Hex |
|------|-----|
| Amarelo Elétrico | `#F5C100` |
| Magenta | `#E01A5A` |
| Preto Total | `#0D0D0D` |
| Grafite | `#1A1A1A` |
| Branco | `#FFFFFF` |

**Regra de contraste:** Amarelo em fundo preto. Branco em fundo preto. Nunca amarelo em branco.

### Tipografia
- **Headings:** Barlow Condensed 900 (Black), uppercase, leading 0.9–1.0
- **Subheadings:** Barlow Condensed 700, uppercase
- **Body:** Barlow 400/500/600
- **Ênfase:** Barlow Condensed Italic 900 em Magenta
- Fonte via Google Fonts: `Barlow Condensed` + `Barlow`

### Logo
```
W²  |  AGÊNCIA
```
- W grande em Barlow Condensed Black
- ² superscript em Magenta (#E01A5A)
- | separador fino
- AGÊNCIA em Barlow Condensed Bold, tracked wide

Variações: Dark BG (W amarelo, ² magenta, AGÊNCIA branco) · Light BG (W preto, ² magenta, AGÊNCIA preto) · Icon (quadrado preto, W amarelo, ² magenta)

### Princípios de design
1. Alto contraste como padrão — nunca cinza-sobre-cinza
2. Bordas como elemento de design — 3–4px solid, sem sombras suaves
3. Tipografia faz o layout — sem ilustrações decorativas
4. Sem border-radius (exceto avatares) — arestas duras
5. Magenta é cirúrgico — um detalhe, nunca área grande (exceto CTAs em fundo escuro)

---

## Estrutura da Landing Page (spec)

Seções em ordem:
1. **Navbar** — dark bg, underline amarelo, logo + nav + CTA button
2. **Hero** — fundo amarelo, headline bold, barra de stats
3. **Serviços** — 4 cards: Branding, Landing Page, Kit Digital, Gestão Mensal
4. **Como funciona** — processo em 3 passos
5. **Prova social / depoimentos**
6. **CTA banner** — fundo magenta
7. **Footer** — dark, acentos amarelos

---

## Portfólio disponível (para publicar nas redes logo após o lançamento)

- **Josi Fit** — plataforma fitness (case concluído)
- **Andreza Crochê (Entrelaçada)** — e-commerce (em andamento, publicar quando entregar)
- **Splitpost** — micro-SaaS (produto próprio, conta como case de produto)

---

## Planejamento Maio–Julho 2026 (referência rápida)

- **Maio:** Existir — landing page, perfis, cases publicados
- **Junho:** Funil — e-mail nurturing ativo, produto de ticket menor lançado
- **Julho:** Captação — 3–4 clientes fechados, 1 no recorrente

Meta de Q2: 1 novo cliente pagante via w², agência oficialmente lançada.

---

## Arquivos de referência

- `design-handoff-claude.md` — spec técnica completa da identidade (fonte da verdade)
- `brand-options/option-c.html` — Opção C "Explosão" (aprovada)
- `references/planejamento-estrategico-v2.md` — planejamento estratégico Mai–Jul 2026
- `references/swot-diagnostico-completo.md` — diagnóstico de mercado
- `discovery.md` — discovery completo da empresa
