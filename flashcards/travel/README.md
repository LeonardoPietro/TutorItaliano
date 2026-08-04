# Deck paralelo de viagem

Sistema **independente** do deck principal (`flashcards/deck.md`) e do
Consolidation Gate (CLAUDE.md §11). Existe pra você poder decorar
vocabulário prático de viagem no seu próprio ritmo, sem competir com — ou
atrapalhar — a progressão pedagógica do curriculo principal (que já cobre
isso, com mais profundidade, no Stage 03 quando você chegar lá).

## Como funciona
- Vocabulário puro: palavra PT → palavra IT (artigo incluído do lado
  italiano pra fixar o gênero junto). Sem frases/estrutura gramatical.
- Mesmo algoritmo SM-2-lite (CLAUDE.md §6), mesma estrutura de tabela do
  deck principal.
- IDs prefixados com `T` (T001, T002...) pra nunca colidir com o deck
  principal.
- **Não conta** em `progress/progress.json` (sessions, flashcards_total,
  etc.) — é puramente prático/situacional, não uma medida de mastery do
  curriculo.
- Revise com "review viagem" ou "flashcards viagem" — eu leio
  `travel/review-queue.md`, aplico as notas (Again/Hard/Good/Easy), e
  atualizo os dois arquivos.
- Categorias (tag `topic`): aeroporto, hotel, restaurante, direcoes,
  transporte, compras, emergencia, numeros-precos, situacoes.

## Arquivos
- `deck.md` — todas as cartas
- `review-queue.md` — cartas devidas, ordenadas por data
