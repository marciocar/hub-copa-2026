# Hub da Copa 2026 ⚽ 🇺🇸 🇲🇽 🇨🇦

> Um site **single-file** (HTML+CSS+JS, zero dependências, funciona offline) sobre a Copa do
> Mundo FIFA 2026 — com um conceito-âncora: **simular o caminho do Brasil até a taça** e gerar
> o card da *sua* Copa.

### ▶️ Demo ao vivo: **https://marciocar.github.io/hub-copa-2026/**

---

## ✨ O conceito

A maioria dos "hubs" de Copa é um folheto bonito: contagem regressiva, grupos, calendário.
Aqui o **palpite é o coração da experiência** — ele não morre num formulário, ele **constrói um
futuro**:

1. Você chuta os **6 jogos do Grupo C** (Brasil, Marrocos, Haiti, Escócia).
2. O site **calcula ao vivo** a classificação e a posição do Brasil.
3. Abre **"O caminho do Brasil até a taça"**: um **chaveamento vivo** com adversários reais e
   crescentes — *Suécia → Alemanha → França → Argentina → Espanha*. Você decide cada mata-mata
   e a estrada se acende.
4. Vença a final e a tela explode num **takeover "HEXACAMPEÃO" com confete**. Depois, gere o
   **card "Minha Copa 2026"** (canvas) e baixe em PNG.

## 🎛️ Funcionalidades

- ⏱️ **Contagem regressiva** ao vivo (reframe: *"o próximo teste do seu palpite"* nos jogos do Brasil).
- 🗂️ **12 grupos reais** (sorteio FIFA de 05/12/2025), 48 seleções.
- 📅 **Calendário** da abertura à final + **16 cidades-sede** com estádios reais.
- 🎯 **Simulador de palpites** do Grupo C (salvo em `localStorage`).
- 🛣️ **Caminho do Brasil**: chaveamento vivo, adversários reais, **medidor "chance de ser campeão"**,
  **troféu-destino** que ignita.
- 🎉 **Takeover de campeão** com confete em canvas + **card compartilhável** (download PNG).
- 🔊 **Som de torcida** sintetizado (WebAudio, opt-in) — sem nenhum arquivo externo.

## ♿ Qualidade & acessibilidade

- Tabs de grupo no padrão **WAI-ARIA** (`tablist`/`tab`/`tabpanel`) com navegação por **teclado** (←/→/Home/End).
- `:focus-visible` global, **contraste AA**, `prefers-reduced-motion` respeitado em todas as animações.
- **Open Graph / Twitter Card**, favicon SVG inline, `theme-color`.
- **Cross-platform:** bandeiras em medalhões FIFA (`BRA`, `ARG`…) — emoji de bandeira não
  renderiza no Windows.

## 🚀 Rodando localmente

Não precisa de build, servidor ou dependências. Basta abrir o arquivo:

```bash
# clone e abra
git clone https://github.com/marciocar/hub-copa-2026.git
cd hub-copa-2026
xdg-open index.html      # Linux  (ou: open index.html no macOS / start no Windows)
```

`index.html` e `copa-2026.html` são o mesmo site (o `index.html` existe para o GitHub Pages).

## 📦 Estrutura

```
.
├── index.html          # site servido pelo GitHub Pages (cópia do copa-2026.html)
├── copa-2026.html      # o site (single-file canônico)
├── versoes/            # histórico de versões (v1 festivo → v4 jornada final)
├── docs/               # Spec-as-Code: contexto de negócio/técnico, KB e sessões
└── ONION-MASTER-PROMPT.md
```

## 🧅 Como foi construído — Spec-as-Code (Onion Portable)

Este projeto foi desenvolvido com a metodologia **[Onion Portable](./ONION-MASTER-PROMPT.md)**:
*especificação antes do código*. Cada feature passou por **@product** (o quê/por quê) e
**@engineer** (como) antes de uma linha ser escrita, com o histórico registrado em
[`docs/sessions/`](./docs/sessions/). Os dados saíram de uma Knowledge Base versionada em
[`docs/knowledge-base/copa-do-mundo-2026.md`](./docs/knowledge-base/copa-do-mundo-2026.md).

- 🧠 **Cérebro / regras:** [`ONION-MASTER-PROMPT.md`](./ONION-MASTER-PROMPT.md)
- 📋 **Negócio:** [`docs/business-context-lite.md`](./docs/business-context-lite.md)
- 🛠️ **Técnico:** [`docs/technical-context-lite.md`](./docs/technical-context-lite.md)

## 🗂️ Dados

Referência: [FIFA](https://www.fifa.com/pt/tournaments/mens/worldcup/canadamexicousa2026) ·
sorteio final em 05/12/2025. Estádios, grupos e calendário do mata-mata consolidados na KB do projeto.

---

Feito com ⚽ e disciplina Spec-as-Code pelo **Onion Portable**.
