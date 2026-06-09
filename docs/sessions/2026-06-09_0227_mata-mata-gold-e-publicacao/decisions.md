# Decisões — Mata-mata GOLD e Publicação

## D-01 — Mata-mata editável em vez de binário "vence/cai"
- **Decisão:** escolher adversário + placar + pênaltis, com trava anti-trapaça.
- **Por quê:** o usuário pediu "UX SUPREME"; o binário era raso. Realismo (pênaltis) e
  liberdade (escolher quem enfrenta) elevam o engajamento.

## D-02 — QR estático pré-gerado, não encoder em runtime
- **Decisão:** o link é fixo → pré-gerar a `QR_MATRIX` (29×29, nível M) e desenhar no canvas.
- **Por quê:** mantém **single-file/offline/zero-dep**; embutir um encoder QR seria ~500 linhas
  e arriscado. Validado decodificando o canvas com jsQR (lê a URL certa).

## D-03 — Card vira og:image (preview social)
- **Decisão:** reaproveitar o card gerado pela `drawShareCard` como `og-card.png` + metas
  `og:image/twitter:image`.
- **Por quê:** dá ao link um preview atraente sem custo extra; o asset já existia.

## D-04 — Versionar (não sobrescrever) e linkar as versões
- **Decisão:** snapshots `versoes/NN-*.html` (atual = v6) e cards linkáveis na seção Bastidores.
- **Por quê:** o usuário quis acesso às outras versões e versionar a última; preserva o histórico
  da evolução como parte do case study.

## D-05 — Verificar em navegador real antes de declarar pronto
- **Decisão:** usar Chrome headless (puppeteer-core) e jsQR para reproduzir os fluxos.
- **Por quê:** num bug de seleção eu errei ao culpar cache/extensão; a causa real (dado antigo
  no localStorage: `Cannot create property 'opp' on string 'win'`) só apareceu no **console**.
  Lição: reproduzir com **estado realista** (incluindo dados legados) e pedir o console cedo.

## D-06 — Migração de dados ao mudar o formato de persistência
- **Decisão:** `loadRoad()` descarta valores não-objeto (formato antigo).
- **Por quê:** quem jogou na versão binária tinha `road={r32:'win'}`; o modelo novo usa objetos.
  Sempre tratar migração quando o schema persistido muda.
