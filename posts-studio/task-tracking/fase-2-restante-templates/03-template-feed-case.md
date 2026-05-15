# Task 03: Template feed-case (3 variantes + upload)

**Fase:** Fase 2 — Restante dos Templates
**Depende de:** Fase 2 Task 01 (upload de imagem)
**Estimativa:** 2h
**Status:** pending

---

## Objetivo

Implementar template `feed-case` (antes/depois, social proof, case visual) com 3 variantes em 4:5, incluindo upload de imagem como elemento central.

## O Que Fazer

1. Criar `src/brands/w2-agencia/templates/feed-case/`
2. Schema: upload de imagem (data URI), métrica destaque (max 20), descrição (max 80), nome do cliente (max 40), variant, colorVariant
3. 3 variantes:
   - **A** — Foto à esquerda (50%) + métrica destaque direita (font grande) + nome cliente abaixo
   - **B** — Foto fundo (100%) + overlay escuro 60% + métrica + nome em sobreposição
   - **C** — Split horizontal 50/50: foto topo + bloco texto rodapé (ou antes/depois)
4. Integrar `<ImageUpload>` no studio-form para o campo `image`
5. No JSX, usar `<img src={input.image} style={{ objectFit: 'cover', width: ..., height: ... }} />`
6. Tratar caso de imagem ausente: mostrar placeholder cinza com texto "Foto do cliente"
7. Adicionar ao template-registry

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/brands/w2-agencia/templates/feed-case/{schema,meta,variants,index}`
- `d:/w2-posts-studio/src/components/studio-form.tsx` — adicionar suporte a campo de imagem
- `d:/w2-posts-studio/src/lib/template-registry.ts`

## Detalhes Técnicos

**Schema:**

```ts
export const feedCaseSchema = z.object({
  image: z.string().min(1, 'Imagem obrigatória'), // data URI
  metric: z.string().min(1).max(20),  // ex: "+300%", "12 leads/mês"
  description: z.string().min(1).max(80),
  clientName: z.string().min(1).max(40),
  variant: z.enum(['A', 'B', 'C']),
  colorVariant: z.enum(['yellow', 'magenta', 'black']),
});
```

**Campo de imagem no form:** o `studio-form` precisa de suporte a tipo `image`. Adicionar:

```ts
fields: [
  { name: 'image', label: 'Foto do cliente', type: 'image' },
  { name: 'metric', label: 'Métrica destaque', maxLength: 20, placeholder: '+300%' },
  ...
]
```

E no componente, branchar: se `type === 'image'`, renderizar `<ImageUpload>` em vez de `<Input>`.

**Tratamento no Satori:**
- Satori aceita data URIs em `<img src={...}>`
- Performance: data URIs grandes (>500KB) podem tornar render lento. O resize em 2048px da Task 01 mitiga.
- `objectFit: 'cover'` funciona no Satori

**Métrica destaque:** Barlow Condensed Black 120-160px, cor accent (magenta no fundo amarelo, amarelo no fundo preto)

## Verificação

- [ ] Acessar `/studio/w2-agencia/feed-case` carrega o template
- [ ] Upload de imagem funciona via studio-form
- [ ] Preview atualiza com a imagem uploaded
- [ ] PNG exportado contém a imagem do cliente nas 3 variantes
- [ ] Sem imagem uploaded: placeholder visível no preview + export bloqueado (validation error)
- [ ] Métrica destacada em font grande e cor de impacto
- [ ] 9 combinações (3 variantes × 3 cores) funcionam visualmente
- [ ] PNG em 1080×1350
