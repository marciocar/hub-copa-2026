# Contexto — Site Copa 2026

## Situação Inicial
Repositório Onion Portable com `ONION-MASTER-PROMPT.md`, `docs/` (3 arquivos de ciclo em estado
template) e `docs/sessions/`. Sem `CLAUDE.md` e sem KBs. Nenhum produto especificado.

## Motivação
O usuário pediu (1) registrar o master prompt como regra da IDE e (2) um site HTML único, com
UI/UX premium sobre a Copa 2026, com "funcionalidades que todo mundo vai querer usar". Antes,
solicitou um documento sobre a Copa (gerou a KB).

## Restrições
- **Single-file HTML**, sem backend, sem build, sem dependências/CDN (funcionar offline).
- **Honestidade de dados:** conhecimento do modelo vai até jan/2026; usar pesquisa web e não
  inventar dados não confirmados (grupos não sorteados ficam "a definir").
- Idioma: UI em pt-BR, código/identificadores em inglês.

## Referências
- KB `docs/knowledge-base/copa-do-mundo-2026.md` (FIFA, Wikipédia, veículos esportivos).
- `ONION-MASTER-PROMPT.md` (regras do fluxo).
