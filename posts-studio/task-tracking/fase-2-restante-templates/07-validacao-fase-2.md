# Task 07: Validação end-to-end Fase 2

**Fase:** Fase 2 — Restante dos Templates
**Depende de:** Tasks 01-06 da Fase 2
**Estimativa:** 30min
**Status:** pending

---

## Objetivo

Validar que os 5 templates (feed-quote, feed-tip, feed-case, feed-cta, story-vertical) funcionam end-to-end, upload de imagem funciona corretamente no Satori, e a landing `/studio/w2-agencia/` orienta o irmão a escolher o template certo.

## O Que Fazer

1. Para cada um dos 5 templates, criar 1 post de exemplo realista (não lorem ipsum) e exportar PNG
2. Para os templates com imagem (feed-case, feed-cta variante C, story-vertical variantes B e C), testar upload de foto real
3. Verificar paridade preview vs PNG nos 5 templates
4. Subir produção e repetir validação rápida (1 post por template)
5. Pedir ao irmão para criar 2 posts diferentes sem instruções e observar fricções
6. Documentar em `d:/woigt-studio/posts-studio/notes/fase-2-validation.md`

## Arquivos Envolvidos

- `d:/woigt-studio/posts-studio/notes/fase-2-validation.md` — criar
- `d:/woigt-studio/posts-studio/notes/sample-posts/` — salvar os 5+ PNGs gerados

## Detalhes Técnicos

**Casos de teste com conteúdo real w² Agência:**

1. **feed-quote** — Quote: "VOCÊ EXISTE. NINGUÉM TE ACHA." | Assinatura: "— w² Agência" | Variante A + amarelo
2. **feed-tip** — Título: "3 erros que matam o Instagram do seu negócio" | Itens: "Postar sem identidade visual", "Ignorar respostas em DM", "Tudo é promoção" | CTA: "Salva esse post" | Variante A + preto
3. **feed-case** — Foto: cliente real (ou stock) | Métrica: "+300% engajamento" | Descrição: "Em 60 dias, com presença consistente" | Cliente: "Andreza Crochê" | Variante A + amarelo
4. **feed-cta** — Headline: "Diagnóstico gratuito" | Subline: "Análise da sua presença digital em 24h" | CTA: "QUERO MEU DIAGNÓSTICO" | Handle: "@w2.agencia" | Variante A + magenta
5. **story-vertical** — Headline: "SEU CONCORRENTE JÁ APARECE." | CTA: "→ link na bio" | Variante A + amarelo

**Critérios de falha que bloqueiam Fase 3:**
- Imagens uploaded não aparecem no PNG final (problema no Satori com data URIs grandes)
- Story vertical: texto crítico cai dentro da safe zone (precisa reposicionar)
- Variantes ficam visualmente confusas/genéricas (problema de design — pode precisar refinar)
- Acentos PT-BR quebram em algum template

## Verificação

- [ ] 5 PNGs (1 por template) salvos com paridade preview/PNG perfeita
- [ ] Templates com imagem: foto renderiza corretamente no PNG
- [ ] Story vertical respeita safe zones (texto crítico fora das áreas reservadas)
- [ ] Landing `/studio/w2-agencia/` lista os 5 templates corretamente
- [ ] Irmão cria 2 posts sem ajuda em <15 minutos total
- [ ] Fricções documentadas em `fase-2-validation.md`
- [ ] Decisão registrada: "Fase 2 aprovada, prosseguir para Fase 3 (polish)" OU "Bloqueada por X"
