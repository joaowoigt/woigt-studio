# Task 06: API `/api/render` aceitando inputs

**Fase:** Fase 1 — Primeiro Template feed-quote
**Depende de:** Fase 0 Task 06 + Fase 1 Task 02
**Estimativa:** 1h
**Status:** done

---

## Objetivo

Evoluir a rota `/api/render` do PoC para aceitar parâmetros (brand, template, inputs do template) e retornar o PNG renderizado dinamicamente baseado nos dados recebidos.

## O Que Fazer

1. Refatorar `src/app/api/render/route.ts` para aceitar `POST`
2. Body do request: `{ brand: string, template: string, input: FeedQuoteInput }`
3. Validar inputs via Zod schema do template (lookup no registry)
4. Renderizar via `renderToPng()` usando a função `Render` do template registry
5. Retornar PNG com `Content-Type: image/png` e header `Content-Disposition` para download
6. Tratamento de erro: input inválido → 400 com mensagem; brand/template não encontrado → 404; erro de render → 500

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/app/api/render/route.ts` — refatorar
- `d:/w2-posts-studio/src/lib/template-registry.ts` — extrair registry para compartilhar entre rota e página

## Detalhes Técnicos

**Estrutura da route:**

```ts
import { NextResponse } from 'next/server';
import { templateRegistry } from '@/lib/template-registry';
import { renderToPng } from '@/lib/render';
import { loadW2Fonts } from '@/brands/w2-agencia/fonts';

export const runtime = 'nodejs'; // Satori + fs.readFile precisam de Node, não Edge

export async function POST(req: Request) {
  const body = await req.json();
  const { brand, template, input } = body;

  const entry = templateRegistry[brand]?.[template];
  if (!entry) {
    return NextResponse.json({ error: 'Template não encontrado' }, { status: 404 });
  }

  const parseResult = entry.schema.safeParse(input);
  if (!parseResult.success) {
    return NextResponse.json({ error: 'Input inválido', issues: parseResult.error.issues }, { status: 400 });
  }

  const fonts = await loadW2Fonts();
  const png = await renderToPng(<entry.Render input={parseResult.data} />, {
    width: entry.meta.width,
    height: entry.meta.height,
    fonts,
  });

  return new Response(png, {
    headers: {
      'Content-Type': 'image/png',
      'Cache-Control': 'no-store',
    },
  });
}
```

**Mover o registry para `src/lib/template-registry.ts`** para evitar import cross entre `app/` e `app/api/` (Server Component + Route Handler).

**Tratamento de fontes:** se brand for diferente de `w2-agencia`, carregar o loader correto (na Fase 4 isso vira config). No MVP, hardcoded `loadW2Fonts()`.

## Verificação

- [ ] POST `/api/render` com body válido retorna PNG (200, content-type image/png)
- [ ] POST com input inválido (ex: quote vazio) retorna 400 com mensagem
- [ ] POST com brand/template inexistente retorna 404
- [ ] PNG retornado reflete os inputs (mudar quote → PNG tem o quote correto)
- [ ] Trocar `variant` no body → PNG mostra a variante correspondente
- [ ] Testar com `curl -X POST -H "Content-Type: application/json" -d '{...}' http://localhost:3000/api/render -o out.png`
