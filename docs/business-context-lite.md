# Business Context

> Este arquivo é a fonte de verdade para Produto. O agente `@product` atualizará este arquivo quando houver novas descobertas.

## 1. Visão do Produto
**Hub da Copa 2026** — um site de página única (single-file HTML) com UI/UX premium e visual
vibrante/festivo sobre a Copa do Mundo FIFA 2026 (EUA/México/Canadá).

- **Público-alvo:** torcedores brasileiros que querem acompanhar a Copa, fazer palpites e
  consultar grupos/jogos de forma rápida, bonita e sem fricção.
- **Principal diferencial:** experiência interativa e "viciante" em um único arquivo `.html`
  (zero backend, zero build), funcionando offline e abrindo direto no navegador. Dados-fonte
  na KB `docs/knowledge-base/copa-do-mundo-2026.md`.

## 2. Dores do Cliente (Problemas que resolvemos)
- Informação da Copa espalhada em vários sites com excesso de anúncios e lentidão.
- Falta de um lugar simples para **fazer e guardar palpites** sem cadastro/login.
- Dificuldade de saber **quando é o próximo jogo** (especialmente do Brasil) num relance.
- Sites pesados que não funcionam bem offline ou em conexões ruins.

## 3. Backlog de Épicos e Features
| ID | Título | Status | Notas |
|---|---|---|---|
| F-01 | Hero + Contagem regressiva | Feito | Countdown ao vivo p/ abertura (11/06) e próximo jogo do Brasil |
| F-02 | Grupos interativos (A–L) | Feito | 12 grupos reais (sorteio FIFA 05/12/2025); destaque do Grupo C |
| F-03 | Calendário e sedes | Feito | Calendário até a final + 16 estádios reais por país |
| F-04 | Simulador de palpites/bracket | Feito | 6 jogos do Grupo C; salva em localStorage |
| F-05 | Tema/estilo vibrante festivo | Feito | Cores fortes, tipografia grande, microanimações |
| F-06 | Elevar site a nível Awwwards SOTD | Em progresso | Candidatura a Site of the Day; foco em Creativity + Acessibilidade |
| F-07 | "O Caminho do Brasil até a taça" (conceito) | Em progresso | Chaveamento vivo: palpites propagam e geram card compartilhável da SUA Copa |

## 4. Especificações Ativas (Em Detalhe)

### F-01 — Hero + Contagem regressiva
- **Como** torcedor, **quero** ver um banner de abertura com a identidade da Copa e um
  cronômetro ao vivo, **para** saber quanto falta para a abertura e para o próximo jogo do Brasil.
- **Regras:** countdown calculado em JS a partir das datas (abertura 11/06/2026; jogos do
  Brasil 13/06, 19/06, 24/06). Após uma data passar, o cronômetro avança para o próximo evento.
- **Aceite:** ao abrir o site, vejo contagem em dias/horas/min/seg atualizando a cada segundo.

### F-02 — Grupos interativos
- **Como** torcedor, **quero** navegar pelos 12 grupos e ver as seleções de cada um,
  **para** acompanhar a fase de grupos. O Grupo C (Brasil) recebe destaque visual.
- **Aceite:** clico/seleciono um grupo (A–L) e vejo as 4 seleções; o do Brasil já vem destacado.

### F-03 — Calendário e sedes
- **Como** torcedor, **quero** ver os jogos por data e as cidades-sede,
  **para** me organizar. Foco nos jogos do Brasil + marcos (abertura/final).
- **Aceite:** vejo lista cronológica com data, confronto e cidade; vejo as 16 sedes por país.

### F-04 — Simulador de palpites / bracket
- **Como** torcedor, **quero** registrar meus palpites de placar e montar o mata-mata,
  **para** me divertir e comparar depois. Sem login.
- **Regras:** estado salvo em `localStorage`; botão "limpar palpites" reseta.
- **Aceite:** preencho placares, recarrego a página e meus palpites continuam lá.

### F-05 — Estilo vibrante festivo
- **Critérios de UX:** responsivo (mobile-first), cores fortes (verde/amarelo/azul),
  tipografia grande e impactante, microanimações em hover/scroll, alto contraste e acessível.

### F-06 — Elevar site a nível Awwwards SOTD
- **Como** dono do produto, **quero** que o Hub da Copa 2026 chegue a nível de premiação
  (Awwwards Site of the Day), **para** servir de portfólio/vitrine do que o Onion produz.
- **Contexto:** diagnóstico atual contra a régua do Awwwards (Design 40% / Usability 30% /
  Creativity 20% / Content 10%) deu média ≈ 6.5 — limítrofe para Honorable Mention, abaixo
  de SOTD (~6.5+ com voto popular). Ponto fraco: **Creativity** e **acessibilidade**.
- **Critérios de aceite (mensuráveis):**
  - **A11y:** contraste mínimo AA em todo texto; `:focus-visible` visível em toda navegação
    por teclado; tabs de grupo com padrão ARIA (`tablist`/`tab`/`tabpanel`) e setas do teclado.
  - **Creativity:** ao menos **1 "hero moment" interativo** (elemento reativo ao mouse/scroll)
    e microinterações variadas (não só `translateY` no hover).
  - **Performance:** Lighthouse ≥ 90 em Performance, Acessibilidade, Best Practices e SEO.
  - **Compartilhamento:** favicon + Open Graph/Twitter cards.
  - **Invariante:** manter single-file, zero dependências, offline-first.

### F-07 — "O Caminho do Brasil até a taça" (conceito-âncora)
- **Visão:** o site para de ser "um hub com seções" e passa a ter uma **ideia única** que
  organiza a experiência: *o site simula o futuro que você apostou.* O palpite — hoje morto
  num formulário — vira o coração da experiência.
- **Como** torcedor, **quero** que meus palpites do Grupo C **propaguem** para o mata-mata
  e desenhem, ao vivo, a estrada do Brasil até a final, **para** viver "a minha Copa" e
  poder **compartilhar** o resultado.
- **Mecânica:**
  1. Palpito os 6 jogos do Grupo C (já existe) → o site **calcula a classificação** e a
     posição do Brasil no grupo (1º/2º classifica; 3º depende; 4º elimina).
  2. Se classificado, abre uma **escada de mata-mata** (32-avos → 16-avos → quartas → semi →
     final no MetLife). A cada rodada eu decido o destino do Brasil; a escada **se acende**
     até onde ele chega — ou marca **onde a jornada terminou**.
  3. O **countdown** deixa de ser genérico: passa a contar para *"o próximo teste do seu
     palpite"* (próximo jogo do Brasil).
  4. **Desfecho compartilhável:** um card "Minha Copa 2026" gerado em canvas (campeão +
     caminho), com **download PNG** — viralidade e o "momento uau" do júri.
- **Aceite:**
  - Mudar um placar do Grupo C atualiza a posição do Brasil e a escada em tempo real.
  - A escada mostra claramente avanço/eliminação e o ponto final da jornada.
  - Botão gera e baixa um PNG legível da "Minha Copa".
  - Estado persistido em localStorage; respeita reduced-motion; mantém single-file/offline.
