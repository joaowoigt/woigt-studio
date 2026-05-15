# Task 01: Criar repo Next.js + TypeScript

**Fase:** Fase 0 — Setup & Proof of Concept
**Depende de:** Nenhuma
**Estimativa:** 20min
**Status:** done

---

## Objetivo

Criar o repositório base do Posts Studio em `d:/w2-posts-studio/` com Next.js 15 (App Router), TypeScript e estrutura inicial de pastas.

## O Que Fazer

1. Criar pasta `d:/w2-posts-studio/`
2. Inicializar Next.js 15 com TypeScript e App Router:
   ```
   npx create-next-app@latest . --typescript --app --tailwind --eslint --src-dir --import-alias "@/*" --no-turbopack
   ```
3. Inicializar git: `git init` + `.gitignore` (já vem do Next)
4. Criar estrutura base de pastas:
   - `src/brands/` (vazia por enquanto)
   - `src/lib/`
   - `src/components/`
5. Atualizar `package.json` com nome `w2-posts-studio` e descrição
6. Criar `README.md` raiz curto: nome do projeto + link para PLAN.md no Vergil

## Arquivos Envolvidos

- `d:/w2-posts-studio/package.json` — criar
- `d:/w2-posts-studio/tsconfig.json` — criar (auto via Next)
- `d:/w2-posts-studio/src/` — estrutura base
- `d:/w2-posts-studio/README.md` — criar
- `d:/w2-posts-studio/.gitignore` — auto via Next

## Detalhes Técnicos

- **Node:** usar versão LTS atual (>=20)
- **Next.js:** 15.x com App Router
- **Sem Turbopack** no setup inicial (pode causar issues com Satori)
- Manter dependências mínimas — adicionar progressivamente

## Verificação

- [x] `d:/w2-posts-studio/` existe e contém projeto Next.js inicializado
- [x] `npm run dev` sobe servidor sem erros
- [x] `tsconfig.json` tem `"strict": true`
- [x] Pastas `src/brands/`, `src/lib/` existem
- [x] Repo inicializado com commit inicial

> **Nota:** Next.js instalado foi v16.2.6 (latest no momento), não 15.x. Compatível com o plano.

---

## Como Testar (manual)

```bash
cd D:/w2-posts-studio
npm run dev
```

1. Abrir http://localhost:3000 — deve mostrar "w² Posts Studio — em construção" com botão shadcn
2. Confirmar que não há erros no terminal
3. `cat tsconfig.json | grep strict` — deve retornar `"strict": true`
4. `ls src/brands src/lib src/components` — todas as pastas existem
