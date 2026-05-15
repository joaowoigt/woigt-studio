# Task 07: Botão exportar PNG + download nomeado

**Fase:** Fase 1 — Primeiro Template feed-quote
**Depende de:** Tasks 05 e 06 da Fase 1
**Estimativa:** 30min
**Status:** done

---

## Objetivo

Implementar o botão "Exportar PNG" da página do studio: faz POST para `/api/render`, recebe o PNG, dispara download no browser com nome padronizado.

## O Que Fazer

1. Na página `studio/[brand]/[template]/page.tsx`, adicionar handler `handleExport()`
2. O handler:
   - Faz `fetch('/api/render', { method: 'POST', body: JSON.stringify({ brand, template, input: data }) })`
   - Recebe o blob da response
   - Cria URL temporária via `URL.createObjectURL(blob)`
   - Cria `<a download>` programaticamente e clica
   - Revoga a URL temporária após download
3. Naming do arquivo: `w2-agencia_feed-quote_YYYY-MM-DD_HHmm.png`
4. Loading state no botão durante o fetch
5. Mensagem de erro visível se falhar

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/app/studio/[brand]/[template]/page.tsx` — adicionar handler e botão
- `d:/w2-posts-studio/src/lib/download.ts` — criar utilitário `downloadBlob(blob, filename)`

## Detalhes Técnicos

**Utility `downloadBlob`:**

```ts
export function downloadBlob(blob: Blob, filename: string) {
  const url = URL.createObjectURL(blob);
  const link = document.createElement('a');
  link.href = url;
  link.download = filename;
  document.body.appendChild(link);
  link.click();
  document.body.removeChild(link);
  // pequeno delay antes de revogar para garantir que o download iniciou
  setTimeout(() => URL.revokeObjectURL(url), 1000);
}
```

**Handler na página:**

```tsx
const [isExporting, setIsExporting] = useState(false);
const [error, setError] = useState<string | null>(null);

async function handleExport() {
  setIsExporting(true);
  setError(null);
  try {
    const res = await fetch('/api/render', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ brand: params.brand, template: params.template, input: data }),
    });
    if (!res.ok) {
      const err = await res.json();
      throw new Error(err.error ?? 'Falha no render');
    }
    const blob = await res.blob();
    const ts = new Date().toISOString().replace(/[:T]/g, '-').slice(0, 16);
    downloadBlob(blob, `${params.brand}_${params.template}_${ts}.png`);
  } catch (e) {
    setError(e instanceof Error ? e.message : 'Erro desconhecido');
  } finally {
    setIsExporting(false);
  }
}
```

**Naming exemplo:** `w2-agencia_feed-quote_2026-05-15-1430.png`

## Verificação

- [ ] Botão "Exportar PNG" visível no canto superior direito da página do studio
- [ ] Clicar dispara download de PNG correto (abrir arquivo confirma)
- [ ] Nome do arquivo segue padrão `[brand]_[template]_[timestamp].png`
- [ ] Durante o fetch, botão mostra loading state (spinner ou texto "Gerando...")
- [ ] Botão desabilitado durante export para evitar clicks múltiplos
- [ ] Se API retornar erro (ex: enviar quote vazio), mensagem de erro aparece visivelmente
