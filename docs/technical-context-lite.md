# Technical Context

> Este arquivo é a fonte de verdade para Engenharia. O agente `@engineer` atualizará este arquivo quando houver mudanças na arquitetura.

## 1. Stack Tecnológica
- **Linguagem:** HTML5 + CSS3 + JavaScript (Vanilla ES6+).
- **Framework:** Nenhum — single-file, zero dependências, sem build.
- **Banco de Dados:** `localStorage` do navegador (para palpites/bracket).
- **Infraestrutura:** Arquivo estático `copa-2026.html`; abre direto no navegador ou em
  qualquer host estático (GitHub Pages, etc.). Funciona offline.

## 2. Padrões de Código (Code Standards)
- JS em **inglês** (identificadores, funções); textos de UI em **pt-BR**.
- Aspas simples no JS; arquivos em kebab-case.
- CSS com **custom properties** (`:root`) para tema; mobile-first com `@media`.
- Acessibilidade: contraste AA, `aria-*` em controles interativos, navegação por teclado.
- Sem bibliotecas externas/CDN (mantém offline e single-file).

## 3. Arquitetura Lógica (Visão Simplificada)
```
copa-2026.html (único arquivo)
├── <style>   → tema vibrante (CSS vars), layout responsivo, animações
├── <body>
│   ├── Hero + Countdown (F-01)
│   ├── Seção Grupos A–L (F-02)
│   ├── Seção Calendário + Sedes (F-03)
│   └── Seção Simulador/Bracket (F-04)
└── <script>
    ├── DATA{}        → grupos, jogos, sedes (derivado da KB)
    ├── countdown()   → setInterval 1s, próximo evento
    ├── renderGroups()/renderSchedule()/renderHosts()
    ├── bracket+predictions → load/save localStorage
    └── observers      → microanimações on-scroll (IntersectionObserver)
```
- **Fonte de dados:** constantes JS embutidas, derivadas de
  `docs/knowledge-base/copa-do-mundo-2026.md` (datas, Grupo C do Brasil, sedes, formato).
- **Estado:** apenas palpites do usuário, persistidos em `localStorage` (chave `copa2026:predictions`).

## 4. Planos de Implementação Ativos
**Entrega:** criar `copa-2026.html` na raiz do projeto.

1. Estrutura HTML semântica + tema CSS vibrante (vars de cor, fontes do sistema, animações).
2. Hero com countdown (F-01): JS calcula próximo evento entre abertura e jogos do Brasil.
3. Grupos (F-02): dados dos 12 grupos; render em cards; Grupo C destacado. *(Grupos A–L
   completos podem ser parcialmente placeholders onde a KB ainda tem lacuna — sinalizar.)*
4. Calendário + sedes (F-03): lista cronológica de jogos-chave + grid das 16 cidades por país.
5. Simulador/bracket (F-04): inputs de placar + persistência localStorage + botão limpar.
6. Polimento de UX: responsivido, microanimações on-scroll, estados de foco/hover.

### Plano F-06 — Elevar a nível Awwwards SOTD (atualizado em 2026-06-08)
Mantém o invariante single-file / zero-dependência / offline. Faseado:

**Fase P1 — Quick wins UX/A11y (alto impacto, baixo custo):**
1. **Tabs de grupo com ARIA real:** `role="tablist"` no container, `role="tab"` +
   `aria-selected` + `aria-controls` nos botões, `role="tabpanel"` + `aria-live="polite"`
   no painel; navegação por **setas ←/→/Home/End** e foco gerenciado (roving tabindex).
2. **`:focus-visible` global:** anel de foco visível e estilizado (cor da marca) em todos os
   elementos interativos (links, botões, tabs, inputs).
3. **Contraste AA:** revisar `--muted-2` (#6b769a) em textos pequenos; clarear se < 4.5:1.
4. **Meta tags:** favicon inline (emoji/SVG data-URI), Open Graph + Twitter Card, `theme-color`.

**Fase P0 — Creativity / hero moment (maior salto de nota):**
5. **Hero interativo reativo ao ponteiro:** orbs da aurora reagem à posição do mouse
   (parallax leve via `mousemove` + `transform`, respeitando `prefers-reduced-motion`).
   CSS puro + JS mínimo; sem WebGL para manter peso baixo.
6. **Microinterações variadas:** botão primário com efeito magnético/brilho que segue o
   cursor; stagger na entrada dos times do grupo (`animation-delay` por índice).
7. **Tipografia de caráter:** display font opcional no H1 (só com `system-ui`/fonte segura
   para não quebrar offline) — avaliar trade-off.

**Verificação:** rodar Lighthouse local (DevTools) e checar contraste; validar teclado
navegando só com Tab/setas. Critérios de aceite em `business-context-lite.md` F-06.

### Plano F-07 — "O Caminho do Brasil" (conceito-âncora)
Tudo em `copa-2026.html`, sem dependências. Reaproveita os 6 palpites do Grupo C como
**entrada** que alimenta o chaveamento.

1. **`computeGroupC(preds)`** — round-robin dos 4 times (pts 3/1/0, saldo, gols pró);
   retorna tabela ordenada + posição do Brasil. Critério de desempate simplificado e sinalizado.
2. **Estado da escada** — `localStorage` chave `copa2026:road` com o destino do Brasil por
   rodada (`advance`/`out`) das 5 fases (R32, R16, QF, SF, Final).
3. **`renderRoad()`** — escada vertical reativa; acende as fases conquistadas com o gradiente
   da marca; marca o ponto de eliminação; estado "CAMPEÃO" se vence a final. Reage a
   qualquer mudança nos palpites do grupo (recalcula posição).
4. **Countdown** — reaproveita `EVENTS`; rótulo passa a enfatizar "próximo teste do seu palpite".
5. **Card compartilhável** — `<canvas>` desenha "Minha Copa 2026" (campeão + caminho) e
   `toBlob`/download PNG. Sem libs. Fallback se canvas indisponível.
6. **A11y/motion** — controles com `aria`; animações de acendimento respeitam reduced-motion.

### Plano F-08/F-09/F-10 — Mata-mata GOLD, compartilhamento e publicação (2026-06-09)
- **Modelo de dados do mata-mata:** `copa2026:road = { r32:{opp,gh,ga,ph,pa}, ... }`.
  `stageOutcome(s)` → `empty|pending|pending-pens|win|lose` (empate exige pênaltis ≠).
  `availableTeams(idx)` aplica anti-trapaça (exclui Brasil e adversários já usados).
  **Migração:** `loadRoad()` descarta valores não-objeto (formato antigo `'win'/'lose'`) —
  corrige `Cannot create property 'opp' on string`.
- **Seletor de adversário:** modal `#opp-modal` (busca + `SUGGEST` por fase). Inputs de placar
  com update **ao vivo** no `input` (sem rerender, preserva foco) e rerender no `change`.
- **QR no card:** `QR_MATRIX` estática (29×29, nível M) pré-gerada para a URL; `drawQR()` pinta
  no canvas — sem encoder/lib em runtime. Verificado decodificando com jsQR.
- **Preview social:** `og:image`/`twitter:image` → `og-card.png` (card gerado pela própria
  `drawShareCard`, 1080×1080) na raiz do site.
- **Versionamento:** snapshots em `versoes/NN-*.html` (atual = v6); cards linkados na seção
  Bastidores. Cada mudança grande vira nova versão (não sobrescrever).
- **Deploy/publicação:** repo público `marciocar/hub-copa-2026`; **GitHub Pages** servindo
  `main` na raiz (`index.html` = cópia de `copa-2026.html`). Workflow: editar canônico → copiar
  p/ `index.html` + `versoes/06` → commit → push → conferir Pages via `curl` cache-bustado.
- **Verificação:** testes em **Chrome headless** (`~/.cache/puppeteer/.../chrome` via
  `puppeteer-core`) cobrindo seleção, pênaltis, anti-trapaça, campeão, download e leitura do QR.

**Nota de dados (atualizado em 2026-06-08):** todos os 12 grupos (A–L) e as 48 seleções
foram preenchidos com o sorteio final da FIFA (05/12/2025), confirmado em duas fontes
(página do sorteio na Wikipédia + busca FIFA). Estádios reais por cidade e calendário do
mata-mata (fases/datas/sedes) também incorporados. Simulador expandido para os 6 jogos do
Grupo C. Fonte consolidada: `docs/knowledge-base/copa-do-mundo-2026.md`.
