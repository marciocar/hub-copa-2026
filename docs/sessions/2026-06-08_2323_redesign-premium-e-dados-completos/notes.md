# Notas e Observações — Redesign Premium + Dados Completos

## Insights e Aprendizados
- **Emoji de bandeira não renderiza no Windows** (Chrome/Edge) — vira o par de letras do código
  regional. Solução portável: medalhão com código FIFA + cor da nação (sem depender do SO).
- Glassmorphism premium: borda em gradiente feita com `mask-composite` (truque 1px) e
  `backdrop-filter` — sem imagens externas, mantém single-file/offline.
- Contadores e reveal via `IntersectionObserver` (sem libs); `prefers-reduced-motion` respeitado.

## Próximos Passos
- Atualizar horários/estádios exatos dos jogos do Brasil perto das datas.
- Possíveis incrementos: bracket completo do mata-mata, classificação ao vivo, modo claro,
  fontes premium (se relaxar a restrição offline).
- Confetes/partículas na seção da final (efeito de torcida).

## Pontos de Atenção
- Manter `t(name, code, color)` ao adicionar seleções; cores devem ter contraste com texto branco.
- Honestidade de dados: nada de placares/cruzamentos inventados.
