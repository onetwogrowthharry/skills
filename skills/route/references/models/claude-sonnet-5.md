# Claude Sonnet 5

as_of: 2026-07-27
model_id: claude-sonnet-5
sources: [models-overview, pricing, migration-guide, Sonnet 5 system card (2026-06-30) via cross-reported aggregators — verify against system card PDF next pass, Artificial Analysis]

## Cost & speed

- $3 / $15 per million tokens in/out (introductory $2 / $10 through 2026-08-31)
- Plain-English anchor: **60% the cost of Opus 5** ($5/$25), **~3× Haiku** ($1/$5); noticeably faster to first answer than Opus
- Context: 1M tokens. Max output: 128K.
- New tokenizer: ~30% more tokens for the same text vs Sonnet 4.6 — cost comparisons against older Sonnet baselines mislead.

## Scorecard

| Benchmark | Sonnet 5 | For scale | Measures |
|---|---|---|---|
| SWE-bench Verified | **85.2%** | Opus 5: 96.0% · Fable 5: 95% · Haiku 4.5: 73.3% | Real GitHub bug-fixing |
| SWE-bench Pro | **63.2%** | Opus 5: 79.2% · Fable 5: 80.0% | Harder, contamination-resistant coding |
| Terminal-Bench 2.1 | **80.4%** | Fable 5: 84.3% | Agentic terminal work (closest proxy for a Claude Code session) |
| OSWorld-Verified | **81.2%** | Fable 5: 85.0% | Computer use |

*Provenance: Anthropic system card values (announcement tables ship as images; numbers cross-reported by multiple independent aggregators). Do not compare across benchmark versions — OSWorld-Verified ≠ OSWorld 2.0.*

## Benchmark story, translated

- **SWE-bench Verified 85.2%:** resolves roughly 5 of every 6 real-repo bug tasks — genuinely strong, but the ~11-point gap to Opus 5 (96.0%) is real, not rounding. Practical consequence: on routine and moderately hard coding you won't feel the gap; on the hardest sixth of tasks — the ones Sonnet misses — Opus-tier is buying something measurable.
  - *Caveat:* SWE-bench tasks are scoped and verifiable; wide ambiguous project work is closer to SWE-bench Pro, where the gap widens (63.2% vs ~80% for the top tier).
- **Terminal-Bench 2.1 80.4%:** within ~4 points of Fable 5 on agentic terminal work. Practical consequence: for hands-on-keyboard agent sessions (run commands, edit, test, iterate), Sonnet is close to top-tier at a fraction of the price.
- **OSWorld-Verified 81.2%:** capable computer-use performance — browser/GUI automation is in range for supervised runs.

## Sweet spot

- Production coding workflows: features, refactors, test-writing in codebases with clear conventions
- Interactive agent sessions where speed matters — you're in the loop, iterating
- High-volume repeatable work: content pipelines, document generation, data extraction
- Subagent workhorse: the default model for fan-out workers in orchestrated jobs

## Falls short

- The hardest coding tier: the SWE-bench Pro gap (63.2% vs ~80%) is where "near-Opus" stops being true
- Long-horizon autonomous runs (hours unattended) — Opus/Fable hold coherence longer
- Wide-open ambiguous briefs where the model must define the task itself
- Anything where a wrong answer is expensive and nothing checks it afterward
- Deep security work: Sonnet 5's cybersecurity safeguards may decline requests that Sonnet 4.6 answered

## Effort behavior (this model)

- Full ladder: low / medium / high / xhigh / max. Default: high.
- **medium here ≈ Sonnet 4.6 at high** — a real cost step-down if migrating habits from the older model
- Respects effort strictly at the low end: at low it does what was asked and no more — good for latency, risky for multi-step reasoning
- xhigh is the setting for its hardest coding/agentic work; leave max_tokens headroom there (thinking shares the output budget)
