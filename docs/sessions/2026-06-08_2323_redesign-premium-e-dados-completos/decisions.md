# Decisões Tomadas — Redesign Premium + Dados Completos

## Decisão 1: Buscar e preencher todos os dados reais (online)
- **Contexto**: v1 tinha só o Grupo C; demais grupos eram placeholders.
- **Decisão**: Pesquisar o sorteio final e preencher os 12 grupos, estádios e mata-mata.
- **Justificativa**: Confirmado em 2 fontes (página do sorteio na Wikipédia + busca FIFA), sem inventar dados.
- **Impacto**: KB e `GROUPS`/`MATCHES`/`HOSTS` atualizados; lacunas reduzidas a horários/cruzamentos.

## Decisão 2: Redesign visual premium (dark glass + aurora)
- **Contexto**: Usuário questionou se era o limite de UI/UX possível.
- **Opções Consideradas**:
  - Manter o tema festivo claro (v1). Contras: menos sofisticado.
  - Dark premium com glassmorphism + aurora + animações, mantendo cores festivas como acento.
- **Decisão**: Dark premium.
- **Justificativa**: Maior percepção de qualidade mantendo a identidade verde/amarelo/azul.
- **Impacto**: Reescrita do CSS e da camada visual; mesma lógica/dados.

## Decisão 3: Medalhões de código FIFA no lugar de emoji de bandeira
- **Contexto**: Screenshot do usuário (Windows/Chrome) mostrou emojis de bandeira virando
  letras ("AR", "DZ", "Brasil BR") — quebra o visual premium.
- **Opções Consideradas**:
  - Manter emoji. Contras: quebrado no Windows (público principal).
  - SVGs inline de 48 bandeiras. Contras: arquivo pesado, complexo.
  - Medalhão com código FIFA (3 letras) + cor da nação. Prós: idêntico em todo SO, leve, premium.
- **Decisão**: Medalhões de código.
- **Justificativa**: Cross-platform garantido, mantém leveza e single-file.
- **Impacto**: `t(name, code, color)`; helper `badge()`; emojis removidos de textos corridos.
