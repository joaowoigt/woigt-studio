# Task Tracking — Posts Studio (w² Agência)

**Plano fonte:** [`d:/woigt-studio/posts-studio/PLAN.md`](../PLAN.md)
**Gerado em:** 2026-05-15
**Repo do código:** `d:/w2-posts-studio/` (criado na Fase 0)
**Primeiro brand alvo:** w² Agência

---

## Como Usar

1. Abra a próxima task `pending` na ordem numérica dentro da fase atual
2. Leia a task completa antes de começar (incluindo "Detalhes Técnicos" e "Verificação")
3. Execute os passos descritos em "O Que Fazer"
4. Confirme TODOS os itens de "Verificação" antes de fechar
5. Mude o status no topo do arquivo para `done`
6. Adicione a seção "Como Testar (manual)" no final do task file conforme regra global
7. Prossiga para a próxima task

## Princípio de Execução

**Não pular a Fase 0.** É a fase de PoC do Satori — se a renderização de fontes/cores não funcionar, todo o projeto trava. Validar antes de investir em templates.

## Progresso

### Fase 0 — Setup & Proof of Concept (1-2 dias)
| Task | Título | Status | Estimativa |
|------|--------|--------|------------|
| 01 | Criar repo Next.js + TypeScript | done | 20min |
| 02 | Configurar Tailwind v4 + shadcn/ui base | done | 30min |
| 03 | Configurar deploy Vercel | done | 20min |
| 04 | Estruturar `src/brands/` e tokens w² | done | 30min |
| 05 | Carregar fontes custom (Barlow Condensed) | done | 30min |
| 06 | PoC Satori `/api/render` | done | 1h |
| 07 | Validação end-to-end Fase 0 | done | 30min |

### Fase 1 — Primeiro Template feed-quote (2-3 dias)
| Task | Título | Status | Estimativa |
|------|--------|--------|------------|
| 01 | Schema Zod + meta do template feed-quote | pending | 30min |
| 02 | 3 variantes JSX de feed-quote | pending | 2h |
| 03 | Componente studio-form (form factory) | pending | 1h |
| 04 | Componente live-preview com escala | pending | 1h |
| 05 | Página `/studio/[brand]/[template]` | pending | 45min |
| 06 | API `/api/render` aceitando inputs | pending | 1h |
| 07 | Botão exportar PNG + download nomeado | pending | 30min |
| 08 | Validação end-to-end Fase 1 | pending | 30min |

### Fase 2 — Restante dos Templates (4-5 dias)
| Task | Título | Status | Estimativa |
|------|--------|--------|------------|
| 01 | Componente upload de imagem + crop fixo | pending | 1h30 |
| 02 | Template feed-tip (3 variantes) | pending | 2h |
| 03 | Template feed-case (3 variantes + upload) | pending | 2h |
| 04 | Template feed-cta (3 variantes + upload opcional) | pending | 2h |
| 05 | Template story-vertical (3 variantes, 9:16, safe zones) | pending | 2h30 |
| 06 | Landing `/studio/w2-agencia/` lista templates | pending | 1h |
| 07 | Validação end-to-end Fase 2 | pending | 30min |

### Fase 3 — UX & Polish (1-2 dias)
| Task | Título | Status | Estimativa |
|------|--------|--------|------------|
| 01 | Char counter + bloqueio em todos os campos | pending | 45min |
| 02 | Overflow detection visual no preview | pending | 1h |
| 03 | Naming automático do PNG exportado | pending | 20min |
| 04 | Loading state + tratamento de erro no export | pending | 30min |
| 05 | Landing `/studio/` lista brands | pending | 30min |
| 06 | Documentação `docs/como-usar.md` | pending | 45min |
| 07 | Validação end-to-end Fase 3 | pending | 30min |

### Fase 4 — Multi-Brand Prep (1 dia)
| Task | Título | Status | Estimativa |
|------|--------|--------|------------|
| 01 | Auditoria de acoplamento brand-específico | pending | 30min |
| 02 | Refactor para tokens via prop/context | pending | 1h30 |
| 03 | Stub `src/brands/splitpost/` com 1 template | pending | 1h |
| 04 | Documentar checklist "Adicionar novo brand" | pending | 30min |
| 05 | Validação final do MVP | pending | 45min |

---

## Status Values

- `pending` — Not started
- `in-progress` — Currently being worked on
- `done` — Completed and verified
- `blocked` — Can't proceed (note the reason)

## Referências de Brand (w² Agência)

- Brandbook: `d:/woigt-studio/brand/brand-book.md`
- Design handoff técnico: `d:/woigt-studio/design-handoff-claude.md`
- Logos SVG: `d:/woigt-studio/brand/assets/logo/`
- Voice/social: `d:/woigt-studio/brand/voice-guide.md`, `social-media-guide.md`

## Tokens-Chave w² (referência rápida)

- **Amarelo Elétrico** `#F5C100` — primary background
- **Magenta** `#E01A5A` — accent, "²", CTAs
- **Preto Total** `#0D0D0D` — text, borders
- **Grafite** `#1A1A1A` — dark surfaces secundárias
- **Branco** `#FFFFFF` — light backgrounds
- **Tipografia display:** Barlow Condensed (Black, Italic)
