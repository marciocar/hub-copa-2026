# Mudanças — Awwwards Uplift

## Arquivos alterados
| Arquivo | Tipo | Resumo |
|---|---|---|
| `copa-2026.html` | Editado | P1 (A11y/UX) + P0 (hero interativo) |
| `docs/business-context-lite.md` | Editado | Épico F-06 + spec com critérios de aceite |
| `docs/technical-context-lite.md` | Editado | Plano F-06 (fases P1/P0) |
| `docs/sessions/README.md` | Editado | Índice: sessão 003 |

## `copa-2026.html` — detalhe

### `<head>` (meta/SEO/compartilhamento)
- `theme-color`, `color-scheme=dark`.
- Favicon SVG inline (data-URI, bola ⚽ sobre fundo da marca).
- Open Graph (`og:type/title/description/locale`) e Twitter Card (`summary_large_image`).

### `<style>` (A11y + microinterações)
- `:focus-visible` global com anel verde; `:focus:not(:focus-visible)` remove outline no mouse.
- `--muted` `#9aa6c8→#aab4d4` e `--muted-2` `#6b769a→#8b95bd` (contraste AA).
- `.aurora` ganha `transform: translate3d(var(--px),var(--py),0)` + transição (parallax).
- `.btn-primary` `::after` com brilho radial em `var(--mx)/var(--my)` (segue o cursor).
- `.team` com `animation: teamIn` + `--d` por índice (stagger).
- Bloco `prefers-reduced-motion`: `.team,.reveal{opacity:1!important;transform:none!important}`.

### Marcação
- `#group-tabs` → `role="tablist"` + `aria-label`.
- `#group-panel` → `role="tabpanel"`, `tabindex="0"`, `aria-live="polite"`.

### `<script>`
- `renderTeam`: injeta `style="--d:${idx*0.07}s"` (stagger).
- `renderGroup`: seta `aria-selected` + roving `tabindex` + `aria-labelledby` no painel.
- `buildGroups`: botões com `role="tab"`/`id`/`aria-controls`; handler `keydown`
  (ArrowRight/Left/Up/Down/Home/End) com foco gerenciado.
- Novo `initPointerFx()`: brilho do botão (sempre) + parallax da aurora (só sem reduced-motion),
  com `requestAnimationFrame` para throttle. Chamado no INIT.

## F-07 — "O Caminho do Brasil" (conceito-âncora)
Transforma o palpite (antes formulário morto) no coração da experiência.

### Marcação
- Nova seção `#caminho` ("O caminho do Brasil até a taça") após `#palpites`.
- Modal `#share-wrap` com `<canvas id="share-canvas" 1080×1080>` + botões fechar/baixar.
- Nav ganha link "Meu caminho"; CTA do hero vira "Simular o caminho do Brasil".
- Subtítulo dos palpites explica que eles **alimentam** o caminho.

### `<style>`
- `.road-status` (posição do Brasil), `.ladder`/`.rung` (escada do mata-mata) com estados
  `reached`/`current`/`eliminated`/`champion`; `.mini-btn` win/lose; modal `.share-wrap`.

### `<script>` (novo módulo ROAD)
- `computeGroupC()`: round-robin dos 4 times (3/1/0 + saldo + gols), retorna tabela ordenada,
  posição do Brasil e flag `complete`. **Testado via harness Node** (ganha tudo→1º/9pts; perde
  tudo→4º).
- `loadRoad()/saveRoad()`: estado da escada em `localStorage` chave `copa2026:road`.
- `roadSummary()`: desfecho (incomplete / group-out / eliminated / inprogress / champion).
- `renderRoad()`: status + escada reativa; trava fases após eliminação; 4º = cai nos grupos;
  3º = "depende dos melhores terceiros". Reage a cada mudança de palpite.
- `buildRoad()`: delegação de clique na escada (toggle win/lose; mudar uma fase limpa as
  seguintes), abre/fecha modal (clique fora + ESC), download.
- `drawShareCard()`: desenha o card "Minha Copa 2026" (desfecho + escada) no canvas;
  `downloadShareCard()` via `toBlob` (fallback `toDataURL`).
- Countdown reframe: rótulo vira "O próximo teste do seu palpite" quando o próximo evento é
  jogo do Brasil.
- Cross-platform: removidos emojis de bandeira 🇧🇷 (não renderizam no Windows) do DOM e do canvas.

### F-07.1 — "Surpresa" (escada → jornada dramática)
Resposta ao feedback "o caminho está simples demais":
- **Adversários reais e crescentes** (`PATH_OPP`, puxados de `GROUPS`): Suécia → Alemanha →
  França → Argentina → Espanha. Cada degrau mostra "Brasil × [seleção]" com flag-badge.
- **Medidor "chance de ser campeão"** (`.hype`): barra + % que sobe a cada vitória (`HYPE_PCT`).
- **Troféu-destino** (`.trophy-goal`): acende (`.won`) quando o Brasil é campeão.
- **Takeover de campeão** (`#champ-fx`): tela cheia "HEXACAMPEÃO" + **confete em canvas**
  (`fireChampion`, ~5s, respeita reduced-motion) disparado ao decidir a final como vitória.
  Botões: gerar card / continuar; fecha com ESC ou clique fora.

## Verificação feita
- `node --check` no `<script>` extraído → **JS OK** (após cada fase).
- Harness Node validando `computeGroupC` (3 cenários).
- Conferência de que os 16 IDs referenciados no JS existem na marcação.
- Revisão manual de regressão do `prefers-reduced-motion` (corrigida).

## Verificação pendente (recomendada)
- Lighthouse local (Performance/A11y/Best Practices/SEO ≥ 90).
- Checagem de contraste com ferramenta dedicada.
- Teste de teclado real (Tab/setas) e leitor de tela.
