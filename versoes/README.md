# Versões do `copa-2026.html` 🧅⚽

Histórico das versões do Hub da Copa 2026. Todos os arquivos são **single-file**
(HTML+CSS+JS), sem dependências, funcionam offline — basta abrir no navegador.

| # | Arquivo | Visual | Dados | Bandeiras | Tamanho |
|---|---------|--------|-------|-----------|---------|
| 1 | [01-festivo-claro.html](01-festivo-claro.html) | Tema claro festivo (verde/amarelo/azul) | Apenas Grupo C real; A,B,D–L como "a definir" | Emoji 🇧🇷 | 22 KB |
| 2 | [02-premium-dark-emoji.html](02-premium-dark-emoji.html) | Premium dark + glassmorphism + aurora | 12 grupos reais, estádios, mata-mata | Emoji 🇧🇷 | 30 KB |
| 3 | [03-premium-badges-ATUAL.html](03-premium-badges-ATUAL.html) | Premium dark (idem v2) | 12 grupos reais, estádios, mata-mata | Medalhões FIFA (`BRA`) | 31 KB |
| 4 | [04-jornada-brasil-FINAL.html](04-jornada-brasil-FINAL.html) | Premium dark + **conceito-âncora** + cinematográfico | idem v3 + chaveamento vivo | Medalhões FIFA | ~64 KB |
| 5 | [05-bastidores-showcase.html](05-bastidores-showcase.html) ⭐ | idem v4 + **seção Bastidores** (case study) | idem v4 | Medalhões FIFA | ~72 KB |

⭐ = **versão atual** (cópia de `../copa-2026.html`).

## Evolução / diferenças

### 1 — Festivo claro
Primeira versão. Layout claro e vibrante, hero com gradiente escuro. Só o Grupo C
estava confirmado na época (demais grupos exibidos como "a definir", por honestidade de dados).

### 2 — Premium dark (emoji)
Redesign visual completo: fundo escuro com **aurora animada**, **glassmorphism** (bordas em
gradiente via máscara CSS), título com gradiente animado, **contadores animados**, **barra de
progresso de scroll**, navbar com blur, transição nas abas e `prefers-reduced-motion`.
Já com **todos os dados reais** (sorteio FIFA 05/12/2025), estádios e calendário do mata-mata.
Bandeiras ainda em emoji.

### 3 — Premium badges
Mesmo visual da v2, mas as bandeiras emoji foram trocadas por **medalhões com código FIFA +
cor da nação** (ex.: `BRA`, `ARG`, `MEX`). Motivo: emoji de bandeira **não renderiza no
Windows/Chrome** (aparecia como "AR", "DZ", "Brasil BR"). Os medalhões renderizam idênticos
em qualquer sistema operacional.

### 4 — Jornada do Brasil (FINAL) ⭐
Salto de **conceito**, não só de visual. O palpite deixa de ser um formulário e vira o coração
da experiência — **"O caminho do Brasil até a taça"**:
- Os 6 palpites do Grupo C **calculam ao vivo** a classificação e a posição do Brasil.
- **Chaveamento vivo** com adversários reais e crescentes (Suécia → Alemanha → França →
  Argentina → Espanha); você decide cada mata-mata e a estrada se acende.
- **Medidor "chance de ser campeão"**, **troféu-destino** que ignita e **takeover de tela
  cheia "HEXACAMPEÃO" com confete** ao vencer a final.
- **Som de torcida** sintetizado (WebAudio, opt-in) no avanço/título; **card "Minha Copa 2026"**
  gerado em canvas com download PNG.
- Acessibilidade: tabs WAI-ARIA + teclado, `:focus-visible`, contraste AA, Open Graph/favicon.
  Tudo respeitando `prefers-reduced-motion` e mantendo single-file/offline.

### 5 — Bastidores / showcase (atual) ⭐
Tudo da v4, mais a correção do confete (anima sempre) e da lógica de botões do mata-mata
(só o jogo atual decide; decididos mostram "↩ refazer"). Adiciona a seção **Bastidores**
(item de menu novo): conta como o site foi feito — a estratégia Spec-as-Code de melhoria
contínua (diagnóstico → spec → build → feedback → iterar), a evolução das versões e o
ecossistema (Onion Portable, Marcio Carvalho, Grana.Ai, Arandek, Sacola de Ideias).

## Qual usar?
- **Experiência completa (recomendada):** a **v5** (atual) — conceito + bastidores.
- **Só consulta/dados, mais leve:** a **v3**.
- **Mac / Linux e quer bandeiras emoji reais:** a **v2**.
- **Visual claro/festivo:** a **v1**.

> Fonte dos dados: `../docs/knowledge-base/copa-do-mundo-2026.md`.
