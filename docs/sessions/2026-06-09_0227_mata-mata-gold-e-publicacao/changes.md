# Mudanças — Mata-mata GOLD e Publicação

## Arquivos
| Arquivo | Tipo | Resumo |
|---|---|---|
| `copa-2026.html` | Editado | Mata-mata editável, QR, og:image, CTA "próximo jogo", Sedes, migração |
| `index.html` | Editado | Cópia do canônico (servido pelo GitHub Pages) |
| `og-card.png` | Novo | Card "Minha Copa 2026" usado como preview social |
| `versoes/06-mata-mata-gold.html` | Novo | Snapshot da versão atual (v6) |
| `versoes/05-bastidores-showcase.html` | Novo (sessão anterior) | Milestone Bastidores (congelado) |
| `versoes/README.md` | Editado | Tabela v1–v6 + descrições |
| `docs/business-context-lite.md` | Editado | F-06/F-07 concluídas; F-08, F-09, F-10 + specs |
| `docs/technical-context-lite.md` | Editado | Plano F-08/09/10 (modelo road, QR, deploy, verificação) |
| `docs/sessions/README.md` | Editado | Índice: sessão 004 |

## Destaques técnicos em `copa-2026.html`
- **Road model:** `copa2026:road = {stage:{opp,gh,ga,ph,pa}}`; `stageOutcome`, `availableTeams`
  (anti-trapaça), `scoreLine`. `loadRoad()` **migra** dados antigos (descarta não-objeto).
- **Seletor de adversário:** modal `#opp-modal` com busca + `SUGGEST` por fase; placar com
  update ao vivo (`input`, sem rerender) e rerender no `change`; pênaltis quando empata.
- **CTA:** `#next-btn` ("Ir para o próximo jogo") rola até a fase ativa; "Gerar card" vira
  primário só ao concluir.
- **QR:** `QR_MATRIX` (29×29) + `drawQR()` no canvas; card mostra placares + link + QR.
- **og:image/twitter:image** → `og-card.png`; **Sedes** em grid de 16 cards; selo "v5/GOLD".
- **Bastidores:** cards de versão viram **links** (v1–v6) + "ver todas no GitHub".

## Histórico de commits da sessão (mais recente → primeiro)
54eaf60 links das versões + versiona v6 · fa905d7 og:image · f8ae443 QR no card ·
3760637 CTA próximo jogo + link no card · c7bf335 migração localStorage · 1fbc345 Sedes grid +
selo · 0533c44 MASTER GOLD (adversário+placar+pênaltis) · e902495 link/ícone GitHub ·
ac7d047 ecossistema real · 58a456d Bastidores + v5 · b94fff0/e892328 confete + escada ·
5280a08 deploy · 6b542cf conceito Caminho do Brasil + Pages.

## Verificação
`node --check` (JS) em cada etapa; Chrome headless (puppeteer-core) para seleção/pênaltis/
anti-trapaça/campeão/download; **jsQR** confirma o QR → `https://marciocar.github.io/hub-copa-2026/`.
Arquivos de versão v1–v6 respondem HTTP 200 no Pages.
