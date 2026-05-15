# Task 05: Página `/studio/[brand]/[template]`

**Fase:** Fase 1 — Primeiro Template feed-quote
**Depende de:** Tasks 03 e 04 da Fase 1
**Estimativa:** 45min
**Status:** done

---

## Objetivo

Criar a página dinâmica do estúdio que combina `<StudioForm>` (esquerda) com `<LivePreview>` (direita), permitindo ao irmão preencher o template e ver o resultado em tempo real.

## O Que Fazer

1. Criar rota dinâmica `src/app/studio/[brand]/[template]/page.tsx`
2. No MVP, aceitar apenas `brand=w2-agencia` e `template=feed-quote`. Outros params retornam 404
3. Layout: split horizontal — formulário esquerda (40% largura), preview direita (60%)
4. Estado local `formData` controla o input do form e o preview reage via `onChange`
5. Header da página: nome do template + breadcrumb (`Studio → w² Agência → Quote`)
6. Botão "Exportar PNG" no topo direito (implementação completa na Task 07)

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/app/studio/[brand]/[template]/page.tsx` — criar
- `d:/w2-posts-studio/src/app/studio/[brand]/[template]/_template-registry.ts` — criar (mapa brand+template → componente+meta+schema)

## Detalhes Técnicos

**Template registry (simplificado MVP):**

```ts
import { feedQuoteSchema, feedQuoteMeta, FeedQuoteRender } from '@/brands/w2-agencia/templates/feed-quote';

export const templateRegistry = {
  'w2-agencia': {
    'feed-quote': {
      schema: feedQuoteSchema,
      meta: feedQuoteMeta,
      Render: FeedQuoteRender,
      fields: [
        { name: 'quote' as const, label: 'Quote / Frase', maxLength: 120, multiline: true },
        { name: 'signature' as const, label: 'Assinatura (opcional)', maxLength: 30, optional: true },
      ],
      defaultValues: { quote: '', signature: '', variant: 'A', colorVariant: 'yellow' },
    },
  },
} as const;
```

**Página:**

```tsx
'use client';
import { useState } from 'react';
import { templateRegistry } from './_template-registry';
import { StudioForm } from '@/components/studio-form';
import { LivePreview } from '@/components/live-preview';
import { notFound } from 'next/navigation';

export default function StudioPage({ params }: { params: { brand: string; template: string } }) {
  const entry = templateRegistry[params.brand]?.[params.template];
  if (!entry) notFound();
  const [data, setData] = useState(entry.defaultValues);

  return (
    <div className="flex h-screen">
      <aside className="w-2/5 p-8 border-r overflow-y-auto">
        <StudioForm schema={entry.schema} meta={entry.meta} fields={entry.fields} defaultValues={entry.defaultValues} onChange={setData} />
      </aside>
      <main className="flex-1 flex items-center justify-center bg-neutral-50">
        <LivePreview width={entry.meta.width} height={entry.meta.height}>
          <entry.Render input={data} />
        </LivePreview>
      </main>
    </div>
  );
}
```

**Nota Next.js 15:** `params` é Promise no App Router atual. Usar `use(params)` no Client Component ou converter pra Server Component que repassa pro Client.

## Verificação

- [ ] Acessar `http://localhost:3000/studio/w2-agencia/feed-quote` carrega a página
- [ ] Form esquerda + preview direita visíveis e proporcionais
- [ ] Digitar no campo quote atualiza o preview em tempo real
- [ ] Mudar variante no radio reflete no preview imediatamente
- [ ] Mudar paleta de cor reflete no preview
- [ ] Acessar URL inválida (ex: `/studio/foo/bar`) retorna 404
