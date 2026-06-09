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
