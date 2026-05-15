# Task 04: Documentar checklist "Adicionar novo brand"

**Fase:** Fase 4 — Multi-Brand Prep
**Depende de:** Fase 4 Task 03
**Estimativa:** 30min
**Status:** pending

---

## Objetivo

Gerar `docs/adicionar-brand.md` — checklist de ~6 passos baseado no que de fato foi feito para adicionar o stub Splitpost. Documentação derivada da prática, não da teoria.

## O Que Fazer

1. Criar `docs/adicionar-brand.md` no repo
2. Listar exatamente os passos executados na Task 03 da Fase 4
3. Para cada passo, dar exemplo de arquivo + 2-3 linhas de código
4. Incluir checklist no final que pode ser copiado pra issue do GitHub
5. Copiar para `d:/woigt-studio/posts-studio/adicionar-brand.md`

## Arquivos Envolvidos

- `d:/w2-posts-studio/docs/adicionar-brand.md` — criar
- `d:/woigt-studio/posts-studio/adicionar-brand.md` — cópia HQ

## Detalhes Técnicos

**Estrutura sugerida:**

```markdown
# Adicionar novo brand ao Posts Studio

## Pré-requisitos

- Brand book com tokens definidos (cores hex, tipografia)
- Logos em SVG
- Fontes em `.ttf` ou `.otf` (ou disponíveis no Google Fonts)

## Passos

### 1. Criar pasta do brand
[exemplo de comando + estrutura]

### 2. Configurar tokens
[exemplo de `tokens.ts` com cores e fontes]

### 3. Carregar fontes
[exemplo de `fonts.ts` com loader]

### 4. Importar assets (logos)
[copiar SVGs para `src/brands/[brand]/logos/`]

### 5. Criar templates
[adaptar templates existentes ou criar novos]

### 6. Registrar nos índices
[exemplo de adição em `brands-registry.ts`, `template-registry.ts`, `load-brand-fonts.ts`]

### 7. Testar
[acessar `/studio/[brand]/[template]`, exportar PNG, validar]

## Checklist final (copiar pra issue)

- [ ] Pasta `src/brands/[brand]/` criada
- [ ] `tokens.ts` com cores e fontes
- [ ] `fonts.ts` com loader funcional
- [ ] Logos SVG em `logos/`
- [ ] Pelo menos 1 template implementado
- [ ] Registrado em `brands-registry.ts`
- [ ] Registrado em `template-registry.ts`
- [ ] Registrado em `load-brand-fonts.ts`
- [ ] PNG de teste exportado e validado visualmente
- [ ] Deploy produção atualizado
```

## Verificação

- [ ] `adicionar-brand.md` lista exatamente os passos feitos para o Splitpost
- [ ] Cada passo tem exemplo de código copiável
- [ ] Checklist final tem <10 itens
- [ ] Outro dev consegue adicionar um brand em <2h seguindo o doc
