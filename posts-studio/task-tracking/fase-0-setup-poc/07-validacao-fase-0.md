# Task 07: Validação end-to-end Fase 0

**Fase:** Fase 0 — Setup & Proof of Concept
**Depende de:** Tasks 01-06
**Estimativa:** 30min
**Status:** done

---

## Objetivo

Validar que toda a base técnica da Fase 0 funciona em conjunto, tanto local quanto em produção Vercel. **Decisão crítica:** se algum item falhar, NÃO avançar para Fase 1 antes de resolver.

## O Que Fazer

1. Rodar `npm run build` localmente — deve completar sem erros nem warnings críticos
2. Rodar `npm run dev` e acessar `/api/render` — PNG retorna correto
3. Commit + push para `main` — deploy Vercel dispara automaticamente
4. Aguardar deploy concluir e acessar URL produção `*.vercel.app/api/render`
5. Confirmar que o PNG retornado em produção é visualmente idêntico ao local
6. Documentar resultado em `d:/woigt-studio/posts-studio/notes/fase-0-poc-result.md`:
   - URL Vercel
   - Screenshot do PNG gerado
   - Tempo de render observado (ms)
   - Qualquer issue encontrada e como foi resolvida

## Arquivos Envolvidos

- `d:/woigt-studio/posts-studio/notes/fase-0-poc-result.md` — criar

## Detalhes Técnicos

**Critérios de falha que bloqueiam Fase 1:**

- Satori não renderiza fonte custom em produção (acontece se loader de fonte usa `process.cwd()` errado no edge runtime)
- Cor visual difere entre local e produção
- Render demora >3s em produção (problema de cold start ou processamento)
- Build falha em produção mas passa local (config de runtime errada)

**Mitigações comuns:**
- Se Satori falhar em edge runtime, mudar route para Node runtime: `export const runtime = 'nodejs'`
- Se fontes não carregarem, usar `import` direto do arquivo `.ttf` (Webpack/Turbopack trata como asset) em vez de `fs.readFile`

## Verificação

- [ ] Build local passa sem erros
- [ ] `/api/render` local retorna PNG correto
- [ ] Deploy Vercel completa com status "Ready"
- [ ] `/api/render` produção retorna PNG visualmente idêntico ao local
- [ ] Tempo de render em produção <3s
- [ ] `fase-0-poc-result.md` documentado com URL e screenshot
- [ ] Decisão registrada: "PoC aprovada, prosseguir para Fase 1" OU "PoC bloqueada por X, replanejar"
