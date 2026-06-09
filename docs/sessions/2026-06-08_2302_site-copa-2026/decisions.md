# Decisões Tomadas — Site Copa 2026

## Decisão 1: Registrar o master prompt como regra via CLAUDE.md com import
- **Contexto**: Usuário pediu "colocar master prompt como regra"; ambiente é Claude Code.
- **Opções Consideradas**:
  - Opção A: Copiar o conteúdo do prompt para `CLAUDE.md`. Contras: duplicação, desatualiza.
  - Opção B: `.claude/rules/` (sugerido no README). Contras: não é auto-carregado pelo Claude Code.
  - Opção C: `CLAUDE.md` com `@ONION-MASTER-PROMPT.md`. Prós: auto-carregado e fonte única.
- **Decisão**: Opção C.
- **Justificativa**: O Claude Code carrega `CLAUDE.md` da raiz; o import mantém o master prompt como fonte única.
- **Impacto**: Editar regras = editar `ONION-MASTER-PROMPT.md`.

## Decisão 2: Seguir fluxo disciplinado (Spec-as-Code) antes de codar
- **Contexto**: Pedido de código direto disparou o Anti-Bypass do Onion.
- **Opções Consideradas**:
  - Opção A: Construir direto (forçar). Contras: sem rastro, viola a Regra de Ouro.
  - Opção B: Disciplinado — specs de produto/engenharia primeiro.
- **Decisão**: Opção B (escolhida pelo usuário).
- **Justificativa**: Mantém a metodologia; gera documentação reutilizável.
- **Impacto**: `business-context-lite.md` e `technical-context-lite.md` preenchidos antes do HTML.

## Decisão 3: Stack vanilla single-file (HTML+CSS+JS), sem dependências
- **Contexto**: Requisito de site HTML único, premium e fácil de distribuir.
- **Opções Consideradas**:
  - Opção A: Framework (React/Vite). Contras: build, múltiplos arquivos, não é single-file.
  - Opção B: Vanilla embutido. Prós: offline, zero build, 1 arquivo.
- **Decisão**: Opção B.
- **Justificativa**: Atende "single-file", abre direto no navegador, sem fricção.
- **Impacto**: Estado via `localStorage`; dados como constantes JS derivadas da KB.

## Decisão 4: Honestidade de dados — grupos não confirmados como "a definir"
- **Contexto**: A KB só confirma o Grupo C (Brasil); demais grupos não sorteados na fonte.
- **Opções Consideradas**:
  - Opção A: Inventar/estimar as 48 seleções. Contras: dados falsos.
  - Opção B: Exibir A,B,D–L como "a definir" e destacar o Grupo C real.
- **Decisão**: Opção B.
- **Justificativa**: Não apresentar informação não verificada ao usuário final.
- **Impacto**: Atualização futura trivial nas constantes `GROUPS`/`MATCHES` quando a KB evoluir.

## Decisão 5: Estilo vibrante festivo + 4 funcionalidades
- **Contexto**: Escolhas do usuário via perguntas direcionadas.
- **Decisão**: Tema vibrante (verde/amarelo/azul) com as 4 features (countdown, grupos, calendário/sedes, palpites).
- **Justificativa**: Alinha identidade de torcida brasileira e engajamento.
- **Impacto**: Define paleta CSS (`:root`) e seções do HTML.
