# Task 01: Auditoria de acoplamento brand-específico

**Fase:** Fase 4 — Multi-Brand Prep
**Depende de:** Fase 3 completa
**Estimativa:** 30min
**Status:** pending

---

## Objetivo

Mapear todo lugar do código que tem dependência hardcoded de `w2-agencia` ou tokens específicos do brand, gerando uma lista de pontos a refatorar na Task 02.

## O Que Fazer

1. Grep no repo: `w2-agencia`, `w2Tokens`, `F5C100`, `E01A5A`, `loadW2Fonts`, `Barlow Condensed`
2. Listar todos os arquivos e linhas que aparecem
3. Para cada ocorrência, classificar:
   - **OK** — dentro de `src/brands/w2-agencia/` (correto)
   - **REFATORAR** — fora dessa pasta, hardcoded em código compartilhado
4. Gerar `docs/multi-brand-audit.md` com a lista
5. Decidir abordagem de fix para cada item da Task 02

## Arquivos Envolvidos

- `d:/w2-posts-studio/docs/multi-brand-audit.md` — criar com findings

## Detalhes Técnicos

**Arquivos suspeitos de acoplamento (check explícito):**
- `src/lib/render.ts` — `loadW2Fonts()` hardcoded?
- `src/app/api/render/route.ts` — importa fonts especificamente de w2?
- `src/lib/template-registry.ts` — estrutura permite múltiplos brands?
- `src/components/studio-form.tsx` — refs ao brand?
- `globals.css` — tokens com prefixo `--w2-*` (precisa virar dinâmico ou scoped?)

**Critério de "acoplamento":** se adicionar um novo brand exige modificar código fora de `src/brands/[novo-brand]/` em mais de 2 lugares, há acoplamento.

## Verificação

- [ ] `multi-brand-audit.md` lista todos os hits do grep
- [ ] Cada ocorrência classificada como OK ou REFATORAR
- [ ] Lista de refactors necessários é objetiva e curta (idealmente <10 itens)
