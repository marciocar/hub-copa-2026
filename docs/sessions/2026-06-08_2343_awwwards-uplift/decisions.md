# Decisões — Awwwards Uplift

## D-01 — Mirar Awwwards SOTD como prêmio-alvo
- **Decisão:** entre os prêmios de UI/UX web (Awwwards, CSSDA, FWA, Webby, Red Dot),
  adotar o **Awwwards Site of the Day** como meta canônica.
- **Por quê:** é o selo de maior prestígio para sites web modernos e a régua dele
  (Design/Usability/Creativity/Content) é objetiva e acionável.

## D-02 — Seguir a Regra de Ouro (spec antes de código)
- **Decisão:** registrar F-06 em `business-context-lite.md` e o plano em
  `technical-context-lite.md` **antes** de codar.
- **Por quê:** disciplina Spec-as-Code do Onion; critérios de aceite mensuráveis evitam
  "polimento sem fim".

## D-03 — Parallax em CSS/JS puro, sem WebGL
- **Decisão:** o "hero moment" usa `pointermove` + `transform` no container `.aurora`,
  não WebGL/Canvas 3D.
- **Por quê:** mantém o **invariante single-file / zero-dependência / offline** e o peso baixo
  (bom para Lighthouse). WebGL traria dependência/complexidade sem ganho proporcional aqui.

## D-04 — Acessibilidade como cidadã de primeira classe
- **Decisão:** implementar padrão WAI-ARIA completo nas tabs (roles + teclado + roving
  tabindex) e `:focus-visible` global; o brilho do botão funciona mesmo com reduced-motion,
  mas o parallax é desligado.
- **Por quê:** Usability vale 30% no Awwwards e o júri testa teclado/leitor de tela;
  movimento deve ser opcional.

## D-06 — Conceito-âncora "O Caminho do Brasil" (F-07)
- **Decisão:** parar de "cumprir requisitos" e dar uma **ideia única** ao site — o palpite vira
  uma simulação viva do futuro apostado, terminando num card compartilhável.
- **Por quê:** parallax/glow/A11y são *piso*, não inovação. SOTD premia **conceito**. O palpite
  estava morto num formulário; vira o coração da experiência.
- **Escopo consciente:** modelamos **o caminho do Brasil** (1 trajetória pelo mata-mata), não o
  chaveamento completo das 48 seleções — é o núcleo emocional e mantém o build tratável e
  single-file. Sinalizado para o usuário.

## D-05 — Fix de regressão do reduced-motion
- **Decisão:** adicionar `.team,.reveal{opacity:1!important}` dentro do bloco
  `prefers-reduced-motion`.
- **Por quê:** o stagger dos times começa em `opacity:0`; com `animation:none!important`
  eles ficariam invisíveis para quem prefere menos movimento. Bug detectado e corrigido
  na mesma sessão.
