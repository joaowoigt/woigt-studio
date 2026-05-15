# Task 02: Overflow detection visual no preview

**Fase:** Fase 3 — UX & Polish
**Depende de:** Fase 3 Task 01
**Estimativa:** 1h
**Status:** pending

---

## Objetivo

Detectar quando o texto preenchido fica grande demais para o layout (mesmo dentro do `maxLength`) e mostrar aviso visual no studio, evitando que o irmão exporte posts com texto cortado/feio.

## O Que Fazer

1. Em cada variante JSX, definir uma estratégia: ou (a) usar `auto-fit` font-size (responsive), ou (b) detectar overflow via `useResizeObserver` no preview e mostrar warning
2. **Estratégia recomendada MVP:** strings dentro do limite máximo do schema NUNCA devem causar overflow se o template foi bem desenhado. Logo, ajustar `maxLength` no schema é a forma correta — apertar os limites se necessário.
3. Para garantir margem: revisar cada template com a string máxima (texto exatamente no `maxLength`) e ajustar `maxLength` se houver overflow
4. Adicionar warning genérico no studio: "Se o texto parecer cortado no preview, considere encurtar"

## Arquivos Envolvidos

- Schemas de cada template — ajustar `max()` se necessário
- `d:/w2-posts-studio/src/components/studio-form.tsx` — adicionar warning genérico

## Detalhes Técnicos

**Por que não detectar overflow programaticamente:** Satori não suporta `useResizeObserver`. O preview e o PNG podem renderizar tamanhos ligeiramente diferentes em alguns casos. Detectar overflow no preview não garante que o PNG está OK.

**Abordagem mais robusta:** calibrar `maxLength` para que o texto SEMPRE caiba, considerando fonte e tamanho do template. Isso é trabalho de design, não de runtime.

**Auto-shrink (alternativa):** alguns templates podem implementar `fontSize` adaptativo baseado em `text.length`:

```tsx
const fontSize = quote.length > 80 ? 64 : quote.length > 50 ? 84 : 104;
```

Aplicar onde fizer sentido (feed-quote especialmente).

## Verificação

- [ ] Em cada template, gerar PNG com string no `maxLength` exato — texto cabe sem cortar
- [ ] Onde for útil, fontSize adaptativo implementado (feed-quote.variant.A pelo menos)
- [ ] Warning visual genérico aparece no studio: "Se algum texto parecer cortado, encurte"
- [ ] `maxLength` ajustado nos schemas se algum template tiver problema com o limite atual
