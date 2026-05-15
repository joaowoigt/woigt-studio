# Task 03: Configurar deploy Vercel

**Fase:** Fase 0 — Setup & Proof of Concept
**Depende de:** Task 01, Task 02
**Estimativa:** 20min
**Status:** done

---

## Objetivo

Conectar repo `w2-posts-studio` à Vercel, configurar deploy automático em push, e validar que preview/produção sobem corretamente.

## O Que Fazer

1. Criar repo no GitHub: `joaowoigt/w2-posts-studio` (private)
2. Push inicial do repo local
3. Importar projeto no Vercel via dashboard (https://vercel.com/new)
4. Aceitar configurações default (Next.js framework detectado automaticamente)
5. Aguardar primeiro deploy concluir
6. Acessar URL `*.vercel.app` gerada e confirmar que a página placeholder carrega
7. Anotar a URL final do deploy (será a URL "padrão Vercel" usada como domínio do estúdio)

## Arquivos Envolvidos

- `d:/w2-posts-studio/.git/config` — remote GitHub
- Nenhum arquivo novo no projeto — config feita no dashboard Vercel

## Detalhes Técnicos

- **Framework:** Next.js (auto-detectado)
- **Build command:** `next build` (default)
- **Output directory:** `.next` (default)
- **Node version:** 20.x (default Vercel atual)
- **Variáveis de ambiente:** nenhuma necessária no MVP
- Domínio: usar URL `*.vercel.app` padrão (decisão cravada no PLAN — sem subdomain customizado no v1)

## Verificação

- [ ] Repo `w2-posts-studio` existe no GitHub
- [ ] Projeto importado no Vercel com build status "Ready"
- [ ] URL `*.vercel.app` retorna 200 e renderiza página placeholder
- [ ] Push em `main` dispara novo deploy automaticamente (testar com 1 commit dummy)
- [ ] URL final documentada em `README.md` raiz do projeto
