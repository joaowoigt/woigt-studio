# Task 01: Componente upload de imagem + crop fixo

**Fase:** Fase 2 — Restante dos Templates
**Depende de:** Fase 1 completa
**Estimativa:** 1h30
**Status:** pending

---

## Objetivo

Construir componente `<ImageUpload>` reutilizável que: aceita upload de imagem do irmão, faz resize/encode client-side para data URI, e fornece o resultado para uso no preview e no Satori. Crop é fixo (object-cover/contain), sem editor visual.

## O Que Fazer

1. Criar `src/components/image-upload.tsx`
2. UI: input file estilizado + preview thumb + botão remover
3. No `onChange`:
   - Validar tipo (apenas image/jpeg, image/png, image/webp)
   - Validar tamanho (max 10MB raw)
   - Resize client-side via Canvas API: max 2048px no lado maior (mantém proporção)
   - Encode como data URI (base64) — guardar no state do form
4. Mostrar thumb 120×120 do que foi uploaded
5. Botão remover limpa o state
6. Acessibilidade: label clicável, aria-label apropriado

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/components/image-upload.tsx` — criar
- `d:/w2-posts-studio/src/lib/image-resize.ts` — criar utilitário de resize

## Detalhes Técnicos

**Util de resize:**

```ts
export async function resizeImageToDataUri(file: File, maxSize = 2048): Promise<string> {
  const img = await loadImage(file);
  const { width, height } = scaleToFit(img.width, img.height, maxSize);
  const canvas = document.createElement('canvas');
  canvas.width = width;
  canvas.height = height;
  const ctx = canvas.getContext('2d')!;
  ctx.drawImage(img, 0, 0, width, height);
  return canvas.toDataURL('image/jpeg', 0.85);
}

function scaleToFit(w: number, h: number, max: number) {
  if (w <= max && h <= max) return { width: w, height: h };
  const ratio = w > h ? max / w : max / h;
  return { width: Math.round(w * ratio), height: Math.round(h * ratio) };
}
```

**API do componente:**

```tsx
type ImageUploadProps = {
  value: string | undefined;             // data URI atual
  onChange: (dataUri: string | undefined) => void;
  label: string;
  optional?: boolean;
};
```

**Importante:** Satori aceita `<img src={dataUri}>` diretamente. O mesmo data URI funciona no preview e no render server-side. Isso garante paridade visual.

**Limitação aceita:** sem editor de crop. O template define `object-fit: cover` ou `contain` na área de imagem, e o resultado é determinístico. Se o irmão quer crop diferente, ele faz no celular antes de subir.

## Verificação

- [ ] Upload de JPEG/PNG/WebP funciona
- [ ] Upload de PDF ou outros tipos é rejeitado com mensagem clara
- [ ] Imagem >10MB rejeitada com mensagem
- [ ] Imagem 4K (3840×2160) é redimensionada para max 2048px no lado maior
- [ ] Data URI gerado é usado em `<img src={dataUri}>` no preview e renderiza
- [ ] Mesmo data URI funciona no Satori (testar com renderToPng manual)
- [ ] Botão "remover" limpa o state corretamente
