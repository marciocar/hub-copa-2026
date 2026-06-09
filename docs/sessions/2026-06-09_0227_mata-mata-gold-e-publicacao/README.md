# Mata-mata GOLD e Publicação — 2026-06-09

## 🎯 Objetivo
Levar o "Caminho do Brasil" a um mata-mata **editável** (escolher adversário, placar e
pênaltis), adicionar **compartilhamento** (card + QR + preview social), uma seção
**Bastidores** (case study), e **publicar** o projeto público no GitHub Pages com versões.

## 📊 Resultados (features F-06 → F-10 concluídas)
- **F-06 Awwwards uplift** e **F-07 Caminho do Brasil**: concluídas.
- **F-08 Mata-mata GOLD:** escolher adversário (modal + busca + sugestões, **anti-trapaça**),
  placar por jogo e **pênaltis** no empate; só o jogo atual editável; "↩ refazer".
- **F-09 Compartilhamento:** card em canvas com placares + **QR estático** do site (offline,
  sem lib); download PNG; **og:image/twitter:image** (`og-card.png`) para preview social.
- **F-10 Bastidores + publicação:** seção "Como foi feito" (5 passos Spec-as-Code), evolução
  das versões com **links (v1–v6)** + "ver todas no GitHub", ecossistema (Onion Portable,
  Marcio Carvalho, Grana.Ai, Arandek, Sacola de Ideias). Repo público + GitHub Pages.
- **Correções/UX:** confete sempre anima (chuva contínua); Sedes em grid equilibrado de 16
  cards; CTA "Ir para o próximo jogo" guia a jornada; **migração de localStorage antigo**
  (string `win/lose` → objeto) que causava crash na seleção.

## 🔗 Links
- Demo: https://marciocar.github.io/hub-copa-2026/
- Repo: https://github.com/marciocar/hub-copa-2026
- Versões: `versoes/` (atual = `06-mata-mata-gold.html`)
- Specs: `docs/business-context-lite.md` (F-06…F-10), `docs/technical-context-lite.md`

## 🧪 Verificação
Testes em **Chrome headless** (puppeteer-core): seleção de adversário (clique/teclado/span),
anti-trapaça, pênaltis no empate, sequência até campeão, download do PNG e **leitura do QR**
(jsQR → URL correta). JS validado com `node --check` a cada etapa.

## ⏱️ Tempo
Sessão longa de iteração guiada por feedback real (vários ciclos diagnóstico→fix→deploy).
