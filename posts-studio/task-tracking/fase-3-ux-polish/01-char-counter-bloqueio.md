# Task 01: Char counter + bloqueio em todos os campos

**Fase:** Fase 3 — UX & Polish
**Depende de:** Fase 2 completa
**Estimativa:** 45min
**Status:** pending

---

## Objetivo

Garantir que TODOS os inputs de texto do studio mostram contador de caracteres ao vivo e impedem digitação além do `maxLength` definido pelo schema, evitando que o irmão ultrapasse o limite que quebraria o layout.

## O Que Fazer

1. Auditar componente `<StudioForm>` e confirmar que cada campo de texto:
   - Mostra `{currentLen} / {maxLen}` abaixo do input
   - Aplica atributo `maxLength` no DOM (bloqueia digitação além do limite)
   - Muda cor do counter para vermelho ao atingir 90%+ do limite
   - Trava digitação visualmente quando bater no limite
2. Para campos opcionais, deixar claro com `(opcional)` no label
3. Para campos multiline (textarea), aplicar mesmo padrão
4. Testar em todos os templates: limite respeitado, counter funcionando

## Arquivos Envolvidos

- `d:/w2-posts-studio/src/components/studio-form.tsx` — ajustar
- `d:/w2-posts-studio/src/components/char-counter.tsx` — extrair se virar grande

## Detalhes Técnicos

**Implementação:**

```tsx
function CharCounter({ current, max }: { current: number; max: number }) {
  const ratio = current / max;
  const color = ratio >= 1 ? 'text-red-600 font-semibold' : ratio >= 0.9 ? 'text-amber-600' : 'text-neutral-500';
  return <span className={`text-xs ${color}`}>{current} / {max}</span>;
}
```

**Bloqueio de digitação:** `<input maxLength={max} {...}>` — o browser já bloqueia nativamente. Não precisa de JS adicional. Para textarea, mesma coisa.

**Edge case:** colar texto >max no input — o browser trunca automaticamente com `maxLength`. Validar isso ainda dispara o `onChange` com o valor truncado.

## Verificação

- [ ] Em cada um dos 5 templates, todos os campos de texto têm char counter visível
- [ ] Digitar até o limite trava (browser bloqueia o teclado)
- [ ] Colar texto >limite resulta em truncamento visível
- [ ] Counter muda para amarelo a 90%+, vermelho a 100%
- [ ] Campos opcionais marcados com `(opcional)` no label
- [ ] UX visualmente consistente entre todos os templates
