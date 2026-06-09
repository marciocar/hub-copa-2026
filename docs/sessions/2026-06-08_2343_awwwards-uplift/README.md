# Awwwards Uplift — 2026-06-08

## 🎯 Objetivo
Elevar o `copa-2026.html` rumo a nível de premiação **Awwwards Site of the Day (SOTD)**.
Diagnóstico inicial contra a régua do Awwwards deu média ≈ 6.5 (limítrofe para Honorable
Mention). Ataque faseado nos pontos fracos: **Creativity** (peso 20%) e **acessibilidade**.

## 📊 Resultados
- **Specs (Spec-as-Code):**
  - `docs/business-context-lite.md` — novo épico **F-06** com critérios de aceite mensuráveis.
  - `docs/technical-context-lite.md` — plano técnico F-06 (fases P1 e P0).
- **P1 — Quick wins UX/A11y** em `copa-2026.html`:
  - Tabs de grupo com padrão WAI-ARIA (`tablist`/`tab`/`tabpanel`), `aria-selected`,
    roving `tabindex` e navegação por teclado (←/→/↑/↓/Home/End).
  - `:focus-visible` global (anel de foco da marca) sem roubar foco do mouse.
  - Contraste AA: `--muted`/`--muted-2` clareados.
  - `theme-color`, `color-scheme`, favicon SVG inline (data-URI), Open Graph + Twitter Card.
- **P0 — Creativity / hero moment** em `copa-2026.html`:
  - Aurora reage ao ponteiro (parallax sutil via `pointermove` + `requestAnimationFrame`).
  - Botão primário com brilho radial que segue o cursor.
  - Entrada escalonada (stagger) dos times ao trocar de grupo.
  - Tudo respeitando `prefers-reduced-motion` (com fix de visibilidade do stagger).

## 🔗 Links Relacionados
- Arquivo: `copa-2026.html`
- Specs: `docs/business-context-lite.md` (F-06), `docs/technical-context-lite.md` (Plano F-06)
- Régua de referência: Awwwards (Design 40% / Usability 30% / Creativity 20% / Content 10%)

## ⏱️ Tempo Investido
~1 hora (diagnóstico + specs + implementação P1/P0).

## 🚀 Deploy (2026-06-09)
- Repo público novo: **https://github.com/marciocar/hub-copa-2026** (origin trocada de
  `onion-portable` para `hub-copa-2026`).
- **GitHub Pages ao vivo:** https://marciocar.github.io/hub-copa-2026/ (main / raiz, build `built`, HTTP 200).
- `index.html` = cópia do `copa-2026.html` para o Pages; versão final salva em `versoes/04-jornada-brasil-FINAL.html`.

## ⏭️ Próximos passos sugeridos
- Rodar **Lighthouse** local (meta ≥ 90 nas 4 categorias) e validar contraste com ferramenta.
- Avaliar P2: cursor customizado, page-transition/loading com personalidade, display font.
- Considerar um hero ainda mais marcante (mapa interativo das 16 sedes) para SOTD.
