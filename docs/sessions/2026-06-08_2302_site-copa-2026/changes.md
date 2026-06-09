# Mudanças Realizadas — Site Copa 2026

## Arquivos Criados
- `CLAUDE.md` — regra de projeto do Claude Code; importa `ONION-MASTER-PROMPT.md` (fonte única).
- `docs/knowledge-base/copa-do-mundo-2026.md` — KB temática (visão geral, formato, sedes, Brasil, fontes).
- `copa-2026.html` — site single-file (hero+countdown, grupos A–L, calendário, sedes, simulador de palpites).
- `docs/sessions/2026-06-08_2302_site-copa-2026/` — registro desta sessão (README, context, decisions, changes, notes, files-changed, commands-executed).

## Arquivos Modificados
- `docs/business-context-lite.md`
  - Substituído template por spec real: visão, dores, backlog F-01…F-05 e critérios de aceite.
- `docs/technical-context-lite.md`
  - Substituído template por stack vanilla single-file, padrões, arquitetura ASCII e plano de implementação.
- `docs/sessions/README.md`
  - Índice central atualizado com a primeira entrada de sessão.

## Testes Adicionados
- Sem suíte de testes (projeto single-file). Validação de sintaxe do JS embutido via Node
  (`vm.compileFunction`) — resultado: OK, sem erros.
