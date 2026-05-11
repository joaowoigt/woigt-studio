# Task 3.01 — Logo SVG standalone

**Fase:** 3 — Assets
**Status:** Concluída

## Objetivo

Gerar o logo W² como arquivo SVG standalone para uso em perfis, favicon, e impressos.

## Escopo

- [ ] SVG versão dark BG: W amarelo, ² magenta, separador + AGÊNCIA branco
- [ ] SVG versão light BG: W preto, ² magenta, AGÊNCIA preto
- [ ] SVG versão ícone: quadrado preto, W amarelo, ² magenta (para avatar/favicon)
- [ ] Favicon (`favicon.ico` ou `.svg`) gerado a partir do ícone
- [ ] Todos os arquivos em `d:/w2-project/public/brand/`

## Logo spec

```
W²  |  AGÊNCIA
```
- W: Barlow Condensed Black, maiúsculo
- ²: superscript, magenta (#E01A5A)
- |: separador fino, espaçado
- AGÊNCIA: Barlow Condensed Bold, letter-spacing amplo

---

## Entregáveis gerados em 2026-05-03

- [x] `d:/w2-project/public/brand/logo-dark.svg` — fundo preto (#0D0D0D), W amarelo, ² magenta, AGÊNCIA branco
- [x] `d:/w2-project/public/brand/logo-light.svg` — fundo branco, W preto, ² magenta, AGÊNCIA preto
- [x] `d:/w2-project/public/brand/logo-icon.svg` — ícone quadrado 200×200, fundo preto, W amarelo, ² magenta, barra magenta no topo
- [x] `d:/w2-project/public/brand/favicon.svg` — versão 32×32 para favicon
- [x] `d:/w2-project/app/layout.tsx` — favicon referenciado via metadata.icons

## Como usar

```tsx
// Em componentes Next.js
import Image from 'next/image'
<Image src="/brand/logo-dark.svg" alt="w² Agência" width={364} height={80} />
<Image src="/brand/logo-light.svg" alt="w² Agência" width={364} height={80} />
<Image src="/brand/logo-icon.svg" alt="w² Agência" width={200} height={200} />
```

**Nota:** Os SVGs referenciam Barlow Condensed via Google Fonts — renderizam corretamente em browsers com internet. Para uso offline ou exportação PNG (social media), abrir o SVG no browser com fonte carregada e exportar via screenshot/print.
