# Task 05: Validação final do MVP

**Fase:** Fase 4 — Multi-Brand Prep
**Depende de:** Tasks 01-04 da Fase 4
**Estimativa:** 45min
**Status:** pending

---

## Objetivo

Validação final consolidada do MVP completo: ferramenta funciona em produção, 2 brands operacionais, irmão autônomo, brand enforcement intacto. Encerra o MVP e libera para uso real.

## O Que Fazer

1. Confirmar deploy de produção atualizado com Fase 4
2. Validação técnica:
   - Acessar `/studio/` → 2 brands listados
   - Acessar `/studio/w2-agencia/` → 5 templates listados
   - Acessar `/studio/splitpost/` → 1 template listado
   - Exportar 1 PNG de cada brand → ambos seguem seus respectivos tokens
3. Validação operacional:
   - Irmão acessa produção e cria 3 posts (1 por aspect ratio) sem ajuda
   - Tempo total <15min
4. Validação de roadmap:
   - Adicionar entrada do projeto Posts Studio na memória persistente do Vergil
   - Atualizar `d:/vergil/decisions/log.md` com decisão de construir ferramenta própria
   - Atualizar `context/current-priorities.md` do Vergil se aplicável
   - Atualizar `d:/woigt-studio/posts-studio/PLAN.md` status: "MVP concluído em [data]"
5. Documentar próximos passos pós-MVP em `d:/woigt-studio/posts-studio/notes/post-mvp-roadmap.md`:
   - Carrossel multi-slide?
   - Histórico de posts gerados?
   - Auth?
   - API pública para batch?

## Arquivos Envolvidos

- `d:/woigt-studio/posts-studio/PLAN.md` — atualizar status final
- `d:/woigt-studio/posts-studio/notes/post-mvp-roadmap.md` — criar
- `d:/vergil/decisions/log.md` — append decisão
- `C:/Users/woigt/.claude/projects/d--vergil/memory/` — adicionar entrada de projeto

## Detalhes Técnicos

**Critérios consolidados do MVP (do PLAN.md):**

- ✅ Irmão cria 10 posts da w² sozinho, sem perguntar nada, em <1h (validado na Fase 3 Task 07)
- ✅ Tempo médio por post: <5min
- ✅ Zero violações de brand observadas
- ✅ 2º brand (Splitpost) adicionado em <2 dias (validado na Fase 4 Task 03)
- ✅ Custo recorrente $0 (Vercel free tier)

**Entry de memória sugerida (Vergil):**

```markdown
---
name: project-posts-studio
description: Ferramenta proprietária w² para criação padronizada de posts on-brand (Next.js + Satori)
metadata:
  type: project
---

**Posts Studio** (MVP concluído em [data]) — Ferramenta interna w² Agência para criação de posts.

- Repo: `d:/w2-posts-studio/`
- HQ docs: `d:/woigt-studio/posts-studio/`
- Stack: Next.js 15 + Tailwind v4 + Satori (@vercel/og) + Vercel
- Brands ativos: w² Agência (5 templates), Splitpost (1 template)
- URL produção: [URL Vercel]
```

## Verificação

- [ ] Produção atualizada com Fase 4 completa
- [ ] 2 brands acessíveis e funcionais em produção
- [ ] Irmão cria 3 posts em <15min sem ajuda
- [ ] PLAN.md atualizado com status "MVP concluído"
- [ ] Decisão logada em `d:/vergil/decisions/log.md`
- [ ] Memória do Vergil atualizada com entrada do projeto
- [ ] Roadmap pós-MVP documentado
- [ ] Posts Studio passa a ser usado para conteúdo real da w² (e não mais Canva/Stitch)
