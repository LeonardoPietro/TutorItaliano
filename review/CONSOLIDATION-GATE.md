# Consolidation Gate — single source of truth for thresholds

Full decision logic lives in `CLAUDE.md` §11. This file is the tunable
source of truth for the thresholds — edit here if they ever need to change.

**Grounding:** forgetting curve (Ebbinghaus) → overdue cards are urgent;
spacing/spaced-repetition (Cepeda et al.; SM-2/FSRS, ~90% target retention) →
review at due date; testing effect (Roediger & Karpicke) → active recall is
the review method; desirable difficulty / ~85% rule (Bjork; Wilson et al.
2019) → consolidate when recent success drops below ~80–85%; interleaving
(Rohrer) → even a "new" day opens with a few due cards.

**Decision ladder (first match wins):**
```
R0 OVERRIDE   learner named a topic or said "new" → LEARN it (warn if debt exists)
R1 COLD START total_cards == 0 → LEARN
R2 OVERDUE    overdue >= 1 → REVIEW
R3 WEAK SPOT  weak_open >= 1 → REVIEW (targeted re-teach)
R4 ACCURACY   last_review_accuracy != null AND < 0.80 → REVIEW
R5 LOAD       C < 0.67 (more than ~1/3 unconsolidated) → REVIEW
R6 BIG DUE    due_today >= 8 → REVIEW
R7 DEFAULT    else → LEARN new (warm up with any 1–7 due cards first)
```

**Current thresholds:**
- Accuracy floor: **0.80** (matches stage-pass bar, just under ~85% optimum)
- Consolidation floor `C`: **0.67** (caps review debt at one-third)
- Big-due trigger: **8** (≈ one review sitting)

**Current state (end of Session 30, 2026-08-10):**
- Due / overdue: **47 ainda vencidos** (lote de 06/08 e 08/08, não tocado) +
  **16 vencendo em 2026-08-11** (8 saíram Again hoje + 8 já agendados).
- Erro de processo descoberto e corrigido nesta sessão: `review-queue.md`
  lista o baralho inteiro ordenado por vencimento, não só os cartões
  realmente devidos. Achei que eram 19+6=25 vencidos e revisei só esse
  subconjunto (focado em pontos fracos); só ao fechar a sessão percebi que
  47 cartões do lote 06/08–09/08 nunca foram tocados. **Lição de processo:**
  antes de anunciar "fila zerada", contar overdue com base na data de
  vencimento de CADA linha do arquivo, não assumir que a lista já vem
  filtrada.
- Open weak spots: **0 formais** — os 5 da Sessão 29 foram resolvidos (chi/
  che, non c'è/non è, plural -cia/-gia, UN/UNO) ou fechados por remoção de
  escopo (posição de adjetivo — cards 096/096b/097 removidos a pedido do
  learner). 8 erros novos observados (2 vazamentos de espanhol, -ARE/-ERE
  confundido em loro, VOLERE/VENIRE com 1 erro cada) — ainda não formalizados
  como weak spots, monitorar na próxima revisão.
- Consolidação recalculada com varredura completa do baralho (111 cartões):
  **C = 54/111 = 48,6%** — bem abaixo do 86,8% que estava registrado, que
  refletia o mesmo erro de contagem (cartões vencidos sendo contados como
  consolidados por engano).
- Precisão da última revisão: **58,3% (14/24)**, sobre os cartões
  efetivamente revisados.
- Próxima sessão: **R2 OVERDUE / R5 LOAD → REVIEW**, com folga grande. Bater
  o backlog de 47 cartões antes de qualquer conteúdo novo ou quiz da Stage 02.

**Current state (end of Session 21):**
- Due / overdue: **0 due today, 0 overdue**. Next due 2026-07-31 (34 cards — 25 carried + 9 new).
- Open weak spots: **0** — all 4 flagged in Session 20 resolved via dedicated reteach this session (uo/ie diphthong in volere/venire, dovere noi/voi, a-vs-da for destino=pessoa, question-reading care).
- Consolidation: C = 80/100 = 80% (dip from 88% purely from 9 new reps=0 cards entering the denominator, not lost ground)
- Formal SM-2 review this session: a 3-card warm-up (059, 018, 048) outside the due queue — **67% (2/3)**, not 83% as first announced live (arithmetic error caught and corrected). Stored as `last_review_accuracy`.
- Two new Stage 02 topics taught (adjective agreement, possessive adjectives) — 9 new cards (093–101), Stage 02 now 6/9 (67%).
- Next session: 34 cards due 2026-07-31 → likely **R2 OVERDUE/R6 BIG DUE → REVIEW** the batch, then resume remaining Stage 02 content (negation, yes/no + wh-questions, days/months/hours).

**Prior state (end of Session 17):**
- Due / overdue: **0 due today, 0 overdue**. Next due 2026-07-28 (11 cards, incl. 3 new -ERE cards).
- Open weak spots: **0**
- Consolidation: C = 71/83 = 86% (dip from 89% is just 3 new reps=0 cards added to the denominator, not lost ground)
- Last review accuracy: **1.0 (100%)** — 3-card warm-up (020, 049, 059), confirming Session 16's 77% dip was catch-up fatigue, not a real gap
- Next session: **R7 DEFAULT → LEARN new** (accuracy back above the 0.80 floor, no overdue, no open weak spots). Good candidate: continue Stage 02 with regular -IRE verbs (plain + the -isc- pattern), the next untaught topic.

**Prior state (end of Session 16, full):** 0 due/overdue, consolidation 89% (71/80), accuracy 77% (dragged down by a rough 9-card catch-up, 33%; the follow-up 17-card round was clean at 94%). Flagged R4 for Session 17 — resolved this session via the warm-up above.

**Prior state (end of Session 15):** 9 overdue (2026-07-25 batch not reached), consolidation 73% (58/80), accuracy 72%.

Note: Stage 00 is NOT complete — 9 of 12 topics taught. Remaining: subject pronouns, essere, avere, c'è/ci sono + question words. Stage 01 started in parallel with -ARE verbs. Two stages still technically "in_progress" simultaneously. **Standing pedagogy change from learner feedback (2026-07-22):** lessons must teach ALL known triggers/exceptions for a rule upfront in the EXPLAIN step — longer sections are fine, learner does not want to discover missing pieces later via generalization. Applied successfully in Session 10 to indefinite articles (un/uno/una/un', full trigger set taught in one pass). Apply the same standard to subject pronouns and essere/avere next, though those topics have less trigger-based structure than articles.
