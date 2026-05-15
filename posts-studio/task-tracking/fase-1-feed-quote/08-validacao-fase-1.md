# Task 08: Validação end-to-end Fase 1

**Fase:** Fase 1 — Primeiro Template feed-quote
**Depende de:** Tasks 01-07 da Fase 1
**Estimativa:** 30min
**Status:** done

---

## Objetivo

Validar fluxo completo: irmão acessa URL, preenche quote, escolhe variante e cor, baixa PNG. Confirmar paridade visual entre preview e PNG. Deploy em produção funcionando.

## O Que Fazer

1. Localmente, criar 3 posts diferentes (combinações variante × cor diferentes) e baixar PNGs
2. Abrir os 3 PNGs e comparar com seus respectivos previews — devem ser visualmente idênticos
3. Subir versão para produção Vercel
4. Repetir o mesmo teste em produção
5. Pedir ao irmão (5 minutos) para criar 1 post sem instruções escritas e observar se ele se vira sozinho
6. Anotar fricções observadas em `d:/woigt-studio/posts-studio/notes/fase-1-validation.md`

## Arquivos Envolvidos

- `d:/woigt-studio/posts-studio/notes/fase-1-validation.md` — criar com checklist preenchido

## Detalhes Técnicos

**Checklist de paridade visual a verificar nos 3 posts:**
- Cores idênticas (fundo, texto, accent)
- Fonte idêntica (Barlow Condensed Black aplicando)
- Posicionamento idêntico (texto centro, logo rodapé etc.)
- Sem caracteres faltando ou substituídos (acentos PT-BR funcionam?)
- Sem corte de texto (texto cabe na área prevista)

**Casos de teste:**
1. Variante A + cor amarela + quote curto + sem assinatura
2. Variante B + cor magenta + quote longo (120 chars) + com assinatura
3. Variante C + cor preta + quote médio + com assinatura especial (acentos: "VOCÊ EXISTE. NINGUÉM TE ACHA.")

**Critérios de falha que bloqueiam Fase 2:**
- Acentos PT-BR não renderizam corretamente (problema de subset de fonte)
- Visual divergente entre preview e PNG em qualquer cenário
- PNG produção difere do PNG local (problema de runtime/fonts em Vercel)
- Tempo de export >5s consistentemente

## Verificação

- [x] 3 PNGs gerados localmente, cada um visualmente idêntico ao seu preview
- [ ] Acentos PT-BR (ç, é, ã, ó) renderizam corretamente — pendente teste com acentos reais
- [ ] Deploy produção atualizado e funcionando
- [ ] 3 PNGs gerados em produção idênticos aos locais
- [ ] Irmão consegue criar 1 post em <5 minutos sem ajuda
- [ ] Fricções observadas documentadas em `fase-1-validation.md`
- [ ] Decisão registrada: "Fase 1 aprovada, prosseguir para Fase 2" OU "Bloqueada por X"

---

## Como Testar (manual)

**Pré-requisito:** servidor rodando em `d:/w2-posts-studio/`

```bash
cd d:/w2-posts-studio
npx next dev --port 3004
```

**1. Testar a página do studio:**

Abra `http://localhost:3004/studio/w2-agencia/feed-quote` no browser.

- Preencha o campo "Quote / Frase" com qualquer texto
- Observe o preview à direita atualizando em tempo real
- Troque o layout (A/B/C) e a paleta de cor — preview deve reagir imediatamente
- Campo "Assinatura" é opcional — deixe vazio e verifique que o elemento desaparece no preview

**2. Testar export PNG:**

- Preencha uma quote e clique "Exportar PNG"
- O botão deve mudar para "Gerando..." durante o download
- Um arquivo `.png` nomeado `w2-agencia_feed-quote_[timestamp].png` deve ser baixado
- Abra o arquivo e compare com o preview — devem ser visualmente idênticos

**3. Testar via curl (API direta):**

```bash
curl -X POST http://localhost:3004/api/render \
  -H "Content-Type: application/json" \
  -d '{"brand":"w2-agencia","template":"feed-quote","input":{"quote":"Você existe. Ninguém te acha.","variant":"A","colorVariant":"yellow"}}' \
  -o teste.png && start teste.png
```

Resultado esperado: PNG 1080×1080 com acentos PT-BR corretos.

**4. Testar erros:**

```bash
# Quote vazio → 400
curl -X POST http://localhost:3004/api/render -H "Content-Type: application/json" \
  -d '{"brand":"w2-agencia","template":"feed-quote","input":{"quote":"","variant":"A","colorVariant":"yellow"}}' -w "%{http_code}"

# Brand inválido → 404
curl -X POST http://localhost:3004/api/render -H "Content-Type: application/json" \
  -d '{"brand":"foo","template":"feed-quote","input":{}}' -w "%{http_code}"
```

**5. Deploy produção (pendente):**

```bash
cd d:/w2-posts-studio && git add . && git commit -m "feat: fase 1 completa — feed-quote template" && git push
```

Aguardar deploy Vercel e repetir testes 1-3 na URL de produção.

**Notas sobre limitações descobertas:**
- JSX em Route Handlers causa hang de compilação no Turbopack — solução: usar `React.createElement` em helper `.ts` separado (`src/lib/create-template-element.ts`)
- `next/font/google` não pode ser importado de módulos usados em Route Handlers — solução: arquivo `browser-fonts.ts` separado para browser, `fonts.ts` apenas para Satori
