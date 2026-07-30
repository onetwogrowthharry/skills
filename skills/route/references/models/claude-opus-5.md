# Claude Opus 5

as_of: 2026-07-27
model_id: claude-opus-5
sources: [models-overview, pricing, migration-guide, Opus 5 announcement (2026-07, benchmark table ships as image) via cross-reported aggregators — verify against system card PDF next pass, Artificial Analysis]

## Cost & speed

- $5 / $25 per million tokens in/out
- Plain-English anchor: **half the cost of Fable 5; ~1.7× Sonnet 5** — frontier results at workhorse pricing
- Context: 1M tokens. Max output: 128K.
- Thinking on by default; slower to first answer than Sonnet, far faster than Fable's minutes-long turns.
- No tokenizer change from Opus 4.8 — token counts carry over when comparing against Opus-family baselines.
- Artificial Analysis Intelligence Index: **61 (max effort), 60 (xhigh), 59 (high)** — the highest-scoring model measured, effectively tied with Fable 5 (60).

## Scorecard

| Benchmark | Opus 5 | For scale | Measures |
|---|---|---|---|
| SWE-bench Verified | **96.0%** | Fable 5: 95% · Sonnet 5: 85.2% | Real GitHub bug-fixing |
| SWE-bench Pro | **79.2%** | Fable 5: 80.0% · Sonnet 5: 63.2% | Harder, contamination-resistant coding |
| Frontier-Bench v0.1 | **43.3%** | Fable 5: 33.7% | Frontier-difficulty engineering |
| ARC-AGI-3 | **30.2%** | Next-best model: 7.8% | Novel abstract reasoning |
| OSWorld 2.0 | **70.57%** | Best cost-adjusted result of any model | Computer use (2.0 ≠ OSWorld-Verified — don't cross-compare) |
| Zapier AutomationBench | **26.0%** | ~1.5× next-best pass rate | Real-world automation building |
| SWE-bench Multimodal | **59.4%** | — | Coding from visual specs |
| CursorBench 3.2 | Within **0.5%** of Fable 5's peak, at half the cost | — | In-editor agentic coding |
| GDPval-AA v2 | **Elo 1,861** | — | Economically valuable knowledge work |

*Provenance: announcement/system-card values cross-reported by multiple independent aggregators; verify against primary next regeneration pass.*

## Benchmark story, translated

- **SWE-bench Verified 96.0% — the highest published score of any Claude model, one point above Fable 5 at half the price.** Practical consequence: for coding, including genuinely hard coding, Opus 5 is the definitive call — you no longer pay the Fable premium for coding ability.
  - *Caveat:* at 95-96%, this benchmark is saturating; the differentiating signal now lives in SWE-bench Pro and Frontier-Bench, where Fable and Opus trade blows (80.0 vs 79.2; 33.7 vs 43.3).
- **ARC-AGI-3 30.2% vs next-best 7.8% (≈4×):** an outlier margin on novel-problem reasoning. Practical consequence: for problems unlike anything in the training data — puzzle-shaped, structure-finding work — Opus 5 currently stands alone.
  - *Caveat:* ARC-AGI is deliberately adversarial and abstract; its transfer to business tasks is indirect.
- **CursorBench 3.2: within 0.5% of Fable 5's peak at half the cost** (announcement claim). Practical consequence: in-editor agentic coding is effectively tied with the premium tier.
- **Migration guide (effort):** `low` and `medium` "punch well above their weight"; code review "stays accurate at lower effort." Practical consequence: this is the "five minutes with an expert" model — a low-effort Opus pass is a legitimate quality check, not a compromise.

## Sweet spot

- Hard engineering of every kind: multi-file features, refactors, real debugging — the default for difficult coding
- Novel, puzzle-shaped problems with no template (the ARC-AGI signal)
- Work where judgment quality matters and there's no downstream reviewer
- Code review and verification passes; coordinating multi-agent work

## Falls short

- Very-long-horizon autonomy and frontier research domains — Fable 5's remaining territory (SWE-bench Pro edge, Terminal-Bench 84.3, plus its documented physics/bio results)
- Security and pentest work: Opus 5 ships with elevated cybersecurity safeguards — classifiers can decline requests, and benign security-adjacent work occasionally trips them (declined cyber requests route to Opus 4.8 via fallback)
- High-volume routine work — Sonnet delivers the same outcome at 60% of the price, faster
- Latency-critical simple tasks — Haiku-class jobs don't benefit from expert judgment

## Effort behavior (this model)

- Full ladder: low / medium / high / xhigh / max. Default: high.
- Measured on Artificial Analysis: max=61, xhigh=60, high=59 — the top three effort settings are within 2 points, so xhigh/max buy little on exam-style intelligence; they matter on long agentic runs
- Start high (xhigh for hardest coding/agentic), then sweep *down* — low/medium are unusually strong here
- Delegates to subagents readily — in orchestrated setups, cap spawn counts rather than encouraging delegation
