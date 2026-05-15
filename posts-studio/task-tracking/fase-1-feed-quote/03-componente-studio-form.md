# Task 03: Componente studio-form (form factory)

**Fase:** Fase 1 — Primeiro Template feed-quote
**Depende de:** Fase 1 Task 01
**Estimativa:** 1h
**Status:** done

---

## Objetivo

Construir o componente `<StudioForm>` que recebe um Zod schema + meta do template e gera automaticamente a UI do formulário (inputs de texto, radio de variantes, radio de paleta). Reutilizável para todos os templates futuros.

## O Que Fazer

1. Instalar React Hook Form + resolver Zod:
   ```
   npm install react-hook-form @hookform/resolvers zod
   ```
2. Criar `src/components/studio-form.tsx`
3. O componente aceita:
   - `schema`: Zod schema
   - `meta`: metadados do template (com `variants` e `colorVariants`)
   - `defaultValues`: estado inicial
   - `onChange`: callback chamado a cada mudança válida (para o live-preview reagir)
4. Renderiza:
   - Inputs de texto para cada campo string do schema (com label, char counter)
   - RadioGroup para campo `variant` usando `meta.variants`
   - RadioGroup visual (com swatches) para campo `colorVariant` usando `meta.colorVariants`
5. Validação client-side via React Hook Form + resolver Zod

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/components/studio-form.tsx` — criar
- `d:/w2-posts-studio/src/components/variant-picker.tsx` — criar (sub-componente)
- `d:/w2-posts-studio/src/components/color-picker.tsx` — criar (sub-componente com swatches)
- `d:/w2-posts-studio/package.json` — adicionar deps

## Detalhes Técnicos

**API do componente:**

```tsx
type StudioFormProps<T> = {
  schema: z.ZodSchema<T>;
  meta: {
    variants: ReadonlyArray<{ id: string; label: string }>;
    colorVariants: ReadonlyArray<{ id: string; label: string; preview: string }>;
  };
  defaultValues: T;
  onChange: (data: T) => void;
};
```

**Estratégia de geração de inputs:**
No MVP, em vez de introspectar o schema Zod automaticamente (complexo), aceitar uma prop adicional `fields` que descreve os campos de texto:

```ts
fields: Array<{
  name: keyof T;
  label: string;
  placeholder?: string;
  maxLength: number;
  optional?: boolean;
  multiline?: boolean;
}>;
```

Isso simplifica e mantém controle total sobre labels/placeholders.

**Char counter:** mostrar `{currentLength} / {maxLength}` abaixo de cada input. Vermelho quando atingir o limite.

**onChange:** usar `form.watch()` + `useEffect` para chamar `onChange` apenas quando dados forem válidos.

## Verificação

- [ ] `<StudioForm>` renderiza inputs para `quote` e `signature` com labels e char counters
- [ ] Radio buttons das 3 variantes (A/B/C) aparecem com labels descritivos
- [ ] Swatches de cor (3 paletas) aparecem com preview visual
- [ ] Mudar qualquer campo dispara `onChange` com dados atualizados
- [ ] Tentar passar de 120 chars no quote bloqueia (ou mostra erro visível)
- [ ] Tab order é lógico (quote → signature → variant → cor)
