# Task 03: Naming automático do PNG exportado

**Fase:** Fase 3 — UX & Polish
**Depende de:** Fase 1 Task 07
**Estimativa:** 20min
**Status:** pending

---

## Objetivo

Refinar a lógica de naming do arquivo exportado para incluir metadados úteis (brand, template, variante, data), facilitando organização em pastas de cliente.

## O Que Fazer

1. Refatorar `handleExport()` em `studio/[brand]/[template]/page.tsx`
2. Padrão final: `{brand}_{template}_v{variant}_{YYYY-MM-DD-HHmm}.png`
3. Exemplo: `w2-agencia_feed-quote_vA_2026-05-15-1430.png`
4. Garantir que data está em timezone do navegador (não UTC)
5. Slugificar brand e template (replace `_` por `-`, lowercase) para nomes consistentes

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/lib/file-naming.ts` — criar utilitário `generateFilename(input, params)`
- `d:/w2-posts-studio/src/app/studio/[brand]/[template]/page.tsx` — usar utilitário

## Detalhes Técnicos

```ts
export function generateFilename(params: {
  brand: string;
  template: string;
  variant?: string;
  ext?: 'png' | 'jpg';
}): string {
  const ts = new Date().toLocaleString('sv-SE', { timeZone: 'America/Sao_Paulo' })
    .replace(' ', '-')
    .replace(/:/g, '')
    .slice(0, 15);  // ex: "2026-05-15-1430"
  const variant = params.variant ? `_v${params.variant}` : '';
  return `${params.brand}_${params.template}${variant}_${ts}.${params.ext ?? 'png'}`;
}
```

**Timezone:** usar `'America/Sao_Paulo'` explicitamente (BRT) já que toda a operação é Brasil. Evita confusão se a Vercel rodar UTC.

## Verificação

- [ ] PNG baixado tem nome no padrão `{brand}_{template}_v{variant}_{ts}.png`
- [ ] Timestamp está em BRT (não UTC)
- [ ] Funciona para todos os 5 templates
- [ ] Nome do arquivo é válido em Windows (sem caracteres reservados como `:`, `/`, `\`)
