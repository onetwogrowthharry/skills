# Claude Fable 5

as_of: 2026-07-27
model_id: claude-fable-5
sources: [models-overview, pricing, migration-guide, Fable 5 announcement (2026-06-09), system-card values via cross-reported aggregators — verify against system card PDF next pass, Artificial Analysis]

## Cost & speed

- $10 / $50 per million tokens in/out
- Plain-English anchor: **twice the cost of Opus 5, ~3× Sonnet 5** — the premium tier, priced like one
- Context: 1M tokens. Max output: 128K.
- **Slow by design:** single requests on hard tasks can run many minutes (a 15-minute turn is normal at higher effort). Thinking is always on and cannot be disabled — effort sets its depth.
- Same tokenizer as Opus 4.8 — token counts carry over when comparing against Opus-family baselines.
- Artificial Analysis Intelligence Index: **60 (max effort, with fallback)** — effectively tied with Opus 5 (61) on exam-style intelligence.

## Scorecard

| Benchmark | Fable 5 | For scale | Measures |
|---|---|---|---|
| SWE-bench Verified | **95%** | Opus 5: 96.0% · Sonnet 5: 85.2% | Real GitHub bug-fixing |
| SWE-bench Pro | **80.0%** | Opus 5: 79.2% · Sonnet 5: 63.2% | Harder, contamination-resistant coding |
| Terminal-Bench 2.1 | **84.3%** | Sonnet 5: 80.4% | Agentic terminal work |
| OSWorld-Verified | **85.0%** | Sonnet 5: 81.2% | Computer use |
| Frontier-Bench v0.1 | **33.7%** | Opus 5: 43.3% | Frontier-difficulty engineering |
| FrontierCode (Cognition) | Highest of frontier models, *even at medium effort* | — | Frontier-hard coding |
| Core Analytics Benchmark | **>90%**, first model to break it (+10 pts over Opus 4.8) | — | Analytics work |
| ViBench | Highest-performing model tested — builds apps in less time with *fewer tokens* | — | App-building efficiency |

*Provenance: system-card/announcement values cross-reported by aggregators. Note Opus 5 shipped after Fable 5 (weeks, not months) and overtook it on several headline scores — see "the honest comparison" below.*

## Benchmark story, translated

- **The honest comparison (July 2026): Opus 5 now matches or beats Fable on most published coding benchmarks at half the price** (SWE-bench Verified 96.0 vs 95; Frontier-Bench 43.3 vs 33.7). Fable's measured edges are narrow: SWE-bench Pro (80.0 vs 79.2), Terminal-Bench 2.1, OSWorld-Verified. Practical consequence: **Fable is no longer the default answer to "hardest coding task" — Opus 5 is.** Fable earns its premium on a specific slice, below.
- **Where Fable still stands alone:** very-long-horizon autonomy and research-grade work. Documented: near-GPT-5.5 frontier-physics performance in 36 hours vs 4 days at a third the reasoning tokens; molecular-biology hypotheses preferred ~80% in blind tests; Hebbia's finance benchmark highest of any model on senior-level document reasoning.
  - *Caveat:* these are vendor and partner results in specific domains — the pattern (sustained multi-hour coherence, token-efficient depth) is the signal, not any single number.
- **FrontierCode: highest even at medium effort** — the documented basis for "specialist at any effort": the migration guide states Fable's lower effort settings "often exceed the xhigh or even max performance of previous models."

## Sweet spot

- Very-long-horizon autonomous work: multi-hour and overnight runs, codebase-wide migrations
- Research-grade analysis: scientific work, senior-level financial/document reasoning
- Terminal-native agent sessions at maximum capability (its Terminal-Bench 2.1 lead)
- Dense or degraded visual inputs: charts, scientific figures, screenshots-to-code

## Falls short

- Most hard coding tasks — Opus 5 now delivers equal-or-better scores at half the price
- Routine work of any kind — specialist rates for generalist output
- Latency-sensitive interactive loops — turns are long; the human waits
- Cybersecurity and research-biology tasks: safety classifiers may decline these outright (benign adjacent work occasionally trips them)

## Effort behavior (this model)

- Ladder: low / medium / high / xhigh / max. Thinking always on — effort controls depth, never zero.
- Low effort still often exceeds prior models' maximum — start lower than instinct suggests for anything short of the hardest work
- At high+ on routine tasks it over-gathers and over-deliberates; match effort to actual difficulty
