# Task 04: Loading state + tratamento de erro no export

**Fase:** Fase 3 — UX & Polish
**Depende de:** Fase 1 Task 07
**Estimativa:** 30min
**Status:** pending

---

## Objetivo

Garantir UX clara durante o export: spinner enquanto renderiza, mensagem de erro visível e acionável se falhar, e prevenção de cliques duplicados.

## O Que Fazer

1. Botão "Exportar PNG" mostra spinner + texto "Gerando..." durante fetch
2. Botão desabilitado durante export
3. Após sucesso, toast/notification rápida "PNG baixado!" (usar shadcn `<Toaster>` ou implementação inline)
4. Se erro: alerta visível embaixo do botão com mensagem do servidor + botão "Tentar novamente"
5. Adicionar timeout no fetch (30s) para não travar UI se servidor pendurar

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/app/studio/[brand]/[template]/page.tsx` — ajustar handler
- `d:/w2-posts-studio/src/components/ui/toast.tsx` — adicionar via shadcn se ainda não tem (`npx shadcn add toast`)

## Detalhes Técnicos

**Fetch com timeout:**

```ts
const controller = new AbortController();
const timeout = setTimeout(() => controller.abort(), 30_000);
try {
  const res = await fetch('/api/render', { method: 'POST', signal: controller.signal, ... });
  // ...
} catch (e) {
  if (e.name === 'AbortError') setError('Render demorou mais que 30s. Tente novamente.');
  else setError(e.message);
} finally {
  clearTimeout(timeout);
}
```

**Loading button:**

```tsx
<Button onClick={handleExport} disabled={isExporting}>
  {isExporting ? <><Spinner /> Gerando...</> : 'Exportar PNG'}
</Button>
```

## Verificação

- [ ] Durante o export, botão mostra spinner e texto muda
- [ ] Botão desabilitado durante export (cliques múltiplos ignorados)
- [ ] Após sucesso, toast aparece e some em ~3s
- [ ] Forçar erro (ex: API offline) mostra mensagem clara com botão de retry
- [ ] Timeout de 30s previne UI travada
