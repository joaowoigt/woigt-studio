# Task 02: Configurar Tailwind v4 + shadcn/ui base

**Fase:** Fase 0 — Setup & Proof of Concept
**Depende de:** Task 01
**Estimativa:** 30min
**Status:** done

---

## Objetivo

Configurar Tailwind v4 (mesma versão usada em `d:/w2-project/`) e instalar componentes base do shadcn/ui necessários para forms (Input, Label, Button, RadioGroup, Card).

## O Que Fazer

1. Confirmar Tailwind v4 já instalado pelo `create-next-app` (caso seja v3, upgradar)
2. Instalar shadcn/ui CLI: `npx shadcn@latest init`
3. Aceitar defaults com:
   - Style: New York
   - Base color: Neutral
   - CSS variables: yes
4. Adicionar componentes:
   ```
   npx shadcn@latest add button input label radio-group card textarea
   ```
5. Verificar que `src/components/ui/` foi criado com componentes
6. Criar `src/app/globals.css` apontando para tokens custom (será preenchido na Task 04)
7. Atualizar `src/app/page.tsx` para um placeholder simples ("Posts Studio — em construção")

## Arquivos Envolvidos

- `d:/w2-posts-studio/components.json` — config shadcn
- `d:/w2-posts-studio/src/components/ui/*` — componentes base
- `d:/w2-posts-studio/src/app/globals.css` — Tailwind + tokens
- `d:/w2-posts-studio/src/app/page.tsx` — placeholder
- `d:/w2-posts-studio/tailwind.config.ts` ou config inline v4

## Detalhes Técnicos

- Tailwind v4 usa `@theme` inline em CSS — sem `tailwind.config.ts` obrigatório
- shadcn/ui v4-compatible: garantir versão atual da CLI
- Manter import alias `@/components/ui/*`

## Verificação

- [ ] `src/components/ui/button.tsx`, `input.tsx`, `label.tsx`, `radio-group.tsx`, `card.tsx`, `textarea.tsx` existem
- [ ] Importar `<Button>` em `src/app/page.tsx` e renderizar — botão aparece com estilo shadcn
- [ ] `npm run dev` sem warnings de Tailwind
- [ ] `npm run build` completa sem erros
