# Task 06: Documentação `docs/como-usar.md`

**Fase:** Fase 3 — UX & Polish
**Depende de:** Tasks 01-05 da Fase 3
**Estimativa:** 45min
**Status:** pending

---

## Objetivo

Criar documentação clara e curta de como o irmão usa o Posts Studio, em linguagem simples e com screenshots. Garante que ele consegue se virar sozinho mesmo sem o Woigt presente.

## O Que Fazer

1. Criar `docs/como-usar.md` no repo `w2-posts-studio`
2. Estrutura sugerida:
   - **O que é** (1 parágrafo)
   - **Acesso** (URL Vercel)
   - **Passo a passo de criar um post** (com screenshots de cada etapa)
   - **Quando usar cada template** (1 frase por template)
   - **Dicas** (5 bullets curtos: respeitar limite de caracteres, fotos boas de 1080+, etc.)
   - **Problemas comuns** (3-4 issues + solução)
3. Tirar screenshots da UI (logo do studio, formulário, preview, botão exportar)
4. Salvar screenshots em `docs/images/`
5. Copiar versão final para `d:/woigt-studio/posts-studio/como-usar.md` (versão HQ)

## Arquivos Envolvidos

- `d:/w2-posts-studio/docs/como-usar.md` — criar
- `d:/w2-posts-studio/docs/images/*.png` — screenshots
- `d:/woigt-studio/posts-studio/como-usar.md` — cópia para HQ

## Detalhes Técnicos

**Tom da documentação:** direto, ações primeiro, jargão técnico zero. Foco no irmão (não-dev).

**Exemplo de seção "Quando usar cada template":**

```markdown
- **Quote / Insight** — quando quiser publicar uma frase de posicionamento ou pensamento de marca
- **Tip / Lista de 3** — quando quiser dar valor educacional rápido (3 erros, 3 dicas, etc.)
- **Case / Antes e Depois** — quando tiver resultado de cliente para mostrar com foto
- **CTA / Oferta** — quando quiser anunciar serviço, diagnóstico ou promoção
- **Story Vertical** — quando o conteúdo for para story (Instagram/LinkedIn), formato 9:16
```

**Section "Problemas comuns":**

```markdown
### "O texto está cortado no preview"
→ Encurte o texto. O contador de caracteres mostra o limite por campo.

### "A imagem ficou ruim"
→ Use fotos de pelo menos 1080×1080 px (uma foto boa do celular já serve).

### "Quero outra cor de fundo"
→ Use as 3 paletas pré-aprovadas (amarelo / magenta / preto). Outras cores fogem do brand.
```

## Verificação

- [ ] `docs/como-usar.md` existe com seções listadas
- [ ] Pelo menos 4 screenshots da UI incluídos
- [ ] Tom acessível para não-dev
- [ ] Irmão lê em <5min e entende o fluxo
- [ ] Cópia em HQ (`d:/woigt-studio/posts-studio/como-usar.md`) sincronizada
