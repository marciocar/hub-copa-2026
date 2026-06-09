# Notas e Observações — Site Copa 2026

## Insights e Aprendizados
- Claude Code carrega `CLAUDE.md` da raiz automaticamente; `@import` é a forma idiomática de
  reaproveitar o master prompt sem duplicar conteúdo.
- O countdown foi modelado como lista ordenada de eventos: o JS seleciona o próximo evento futuro,
  então o cronômetro avança sozinho ao longo do torneio (abertura → jogos do Brasil → final).
- Persistência de palpites com `localStorage` entrega "feature viciante" sem backend nem login.

## Próximos Passos
- Completar os grupos A, B, D–L em `GROUPS` quando o sorteio oficial estiver na KB
  (acionar `@meta` para atualizar `docs/knowledge-base/copa-do-mundo-2026.md`).
- Possíveis incrementos: tabela de classificação ao vivo, aba de artilheiros, modo bracket
  completo do mata-mata, tema claro/escuro.
- Confirmar horários/estádios dos jogos do Brasil perto das datas (podem mudar).

## Pontos de Atenção
- Manter a regra de honestidade de dados: nada de seleções/datas inventadas no HTML.
- Emojis de bandeira (ex.: Escócia 🏴) podem variar de render por SO/navegador.
