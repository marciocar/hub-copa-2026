# Technical Context

> Este arquivo é a fonte de verdade para Engenharia. O agente `@engineer` atualizará este arquivo quando houver mudanças na arquitetura.

## 1. Stack Tecnológica
- **Linguagem:** HTML5 + CSS3 + JavaScript (Vanilla ES6+).
- **Framework:** Nenhum — single-file, zero dependências, sem build.
- **Banco de Dados:** `localStorage` do navegador (para palpites/bracket).
- **Infraestrutura:** Arquivo estático `copa-2026.html`; abre direto no navegador ou em
  qualquer host estático (GitHub Pages, etc.). Funciona offline.

## 2. Padrões de Código (Code Standards)
- JS em **inglês** (identificadores, funções); textos de UI em **pt-BR**.
- Aspas simples no JS; arquivos em kebab-case.
- CSS com **custom properties** (`:root`) para tema; mobile-first com `@media`.
- Acessibilidade: contraste AA, `aria-*` em controles interativos, navegação por teclado.
- Sem bibliotecas externas/CDN (mantém offline e single-file).

## 3. Arquitetura Lógica (Visão Simplificada)
```
copa-2026.html (único arquivo)
├── <style>   → tema vibrante (CSS vars), layout responsivo, animações
├── <body>
│   ├── Hero + Countdown (F-01)
│   ├── Seção Grupos A–L (F-02)
│   ├── Seção Calendário + Sedes (F-03)
│   └── Seção Simulador/Bracket (F-04)
└── <script>
    ├── DATA{}        → grupos, jogos, sedes (derivado da KB)
    ├── countdown()   → setInterval 1s, próximo evento
    ├── renderGroups()/renderSchedule()/renderHosts()
    ├── bracket+predictions → load/save localStorage
    └── observers      → microanimações on-scroll (IntersectionObserver)
```
- **Fonte de dados:** constantes JS embutidas, derivadas de
  `docs/knowledge-base/copa-do-mundo-2026.md` (datas, Grupo C do Brasil, sedes, formato).
- **Estado:** apenas palpites do usuário, persistidos em `localStorage` (chave `copa2026:predictions`).

## 4. Planos de Implementação Ativos
**Entrega:** criar `copa-2026.html` na raiz do projeto.

1. Estrutura HTML semântica + tema CSS vibrante (vars de cor, fontes do sistema, animações).
2. Hero com countdown (F-01): JS calcula próximo evento entre abertura e jogos do Brasil.
3. Grupos (F-02): dados dos 12 grupos; render em cards; Grupo C destacado. *(Grupos A–L
   completos podem ser parcialmente placeholders onde a KB ainda tem lacuna — sinalizar.)*
4. Calendário + sedes (F-03): lista cronológica de jogos-chave + grid das 16 cidades por país.
5. Simulador/bracket (F-04): inputs de placar + persistência localStorage + botão limpar.
6. Polimento de UX: responsivido, microanimações on-scroll, estados de foco/hover.

**Nota de dados (atualizado em 2026-06-08):** todos os 12 grupos (A–L) e as 48 seleções
foram preenchidos com o sorteio final da FIFA (05/12/2025), confirmado em duas fontes
(página do sorteio na Wikipédia + busca FIFA). Estádios reais por cidade e calendário do
mata-mata (fases/datas/sedes) também incorporados. Simulador expandido para os 6 jogos do
Grupo C. Fonte consolidada: `docs/knowledge-base/copa-do-mundo-2026.md`.
