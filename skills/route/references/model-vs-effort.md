# Model vs Effort — the two dials

as_of: 2026-07-27
sources: [effort docs, migration-guide, model announcements]

Every route turns two independent dials.

**Effort = how thoroughly Claude works the problem.** More reasoning steps, more tool calls, more self-verification, more time and tokens. Raise it when you want the *same* mind to be more careful.

**Model = the ceiling on what Claude can see.** A harder problem doesn't need more care — it needs more capability. Switch models when the problem is beyond what thoroughness can fix.

## The intuition (and the facts behind it)

- **Sonnet at high effort is an afternoon with a strong generalist.** Plenty of time, real diligence, excellent results on anything within reach.
  - *Fact:* Anthropic positions Sonnet 5 as reaching previously-Opus-tier quality on many coding and agentic tasks; its migration guide states Sonnet 5 at `medium` matches Sonnet 4.6 at `high`.
- **Opus at low effort is five minutes with an expert.** Less deliberation, but the judgment in the room is simply better.
  - *Fact:* Anthropic's migration guide notes Opus 5's `low` and `medium` "punch well above their weight" — strong quality at a fraction of the tokens — and its code review "stays accurate at lower effort."
- **Fable at any effort is a specialist who spots what everyone else misses.** The ceiling moves; effort just decides how long the specialist stays.
  - *Fact:* the migration guide states Fable 5's lower effort settings "often exceed the xhigh or even max performance of previous models," and Cognition's FrontierCode benchmark showed Fable 5 scoring highest among frontier models *even at medium effort*. (Fable's thinking is always on — effort sets its depth, never zero.)

## The decision rule

1. **Diagnose which dial the problem is asking for.** Symptoms of an effort problem: the model rushes, misses steps, skips verification — it *could* get there with more care. Symptoms of a model problem: even careful runs miss the insight, lose the thread on long-horizon work, or can't hold the whole problem — no amount of care closes the gap.
2. **Effort is the cheap dial — try it first** when the current model is plausibly capable. Same model at higher effort costs extra tokens; a bigger model costs more on *every* token.
3. **Model is the honest dial when the ceiling is the issue.** A bigger model at *lower* effort frequently beats a smaller model at max effort — and can cost less, because it doesn't burn tokens flailing. Don't max out effort to avoid admitting the task needs a better model.
4. **Watch for the overkill diagonal.** Big model + max effort on a routine task buys deliberation the task can't use — and on top-tier models can tip into overthinking (Anthropic's own docs flag `max` as "prone to overthinking" on simpler tasks).

## Quick pairing heuristics

| Situation | Pairing |
|---|---|
| Routine, scoped, low stakes | Small/mid model, low–medium effort |
| Routine but wrongness is costly | Mid model, high effort (or add a verification pass) |
| Hard problem, well specified | Big model, medium–high effort |
| Hard problem, ambiguous, long-horizon | Biggest model, high+ effort, full spec up front |
| "It keeps almost getting there" | Raise effort one step first |
| "It never quite sees it" | Raise the model, keep effort moderate |
