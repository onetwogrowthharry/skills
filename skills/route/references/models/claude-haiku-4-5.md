# Claude Haiku 4.5

as_of: 2026-07-27
model_id: claude-haiku-4-5
sources: [models-overview, pricing]

## Cost & speed

- $1 / $5 per million tokens in/out
- Plain-English anchor: **a third the cost of Sonnet, a tenth of Fable** — and the fastest to answer by a wide margin
- Context: 200K tokens (a fifth of the 5-family's 1M). Max output: 64K.

## Scorecard

| Benchmark | Haiku 4.5 | For scale | Measures |
|---|---|---|---|
| SWE-bench Verified | **73.3%** | Sonnet 5: 85.2% · Opus 5: 96.0% | Real GitHub bug-fixing |
| Terminal-Bench 1.0 | **40.2%** (41.8% w/ extended thinking) | Not comparable to 2.1 scores — different benchmark version | Agentic terminal work |
| Speed (Anthropic, at launch) | Similar coding performance to Sonnet 4 at **1/3 the cost and >2× the speed**; ~90% of Sonnet 4.5's agentic-coding performance at a fraction of its cost | — | Latency/throughput |

*Provenance: Anthropic launch announcement (2025-10). Note comparisons are against Sonnet 4/4.5, one Sonnet generation back — the gap to Sonnet 5 is wider than these launch claims suggest.*

## Benchmark story, translated

- **SWE-bench Verified 73.3%:** solves roughly 3 of 4 scoped real-repo bugs — genuinely capable, but a full tier below Sonnet 5 (85.2%) and Opus 5 (96.0%). Practical consequence: fine for small scoped fixes; wrong tool for anything multi-step.
- **The speed claim is the point:** more than twice Sonnet 4's speed at a third of its cost per the launch post. Practical consequence: when a task is genuinely simple, the bigger models produce the *same answer* slower and at 3–10× the price — Haiku is the anti-overkill answer, not a compromise.
  - *Caveat:* "simple" means simple for a strong model — classification, extraction, formatting, short drafts. Multi-step reasoning is where its answers diverge from the bigger tiers, and its launch comparisons predate the current 5-family.

## Sweet spot

- Classification, tagging, sentiment, yes/no triage at volume
- Extraction and reformatting: pull fields, convert formats, clean data
- Short, low-stakes drafting: subject lines, summaries of single documents
- Speed-critical steps inside a bigger pipeline (the cheap worker in a fan-out)

## Falls short

- Multi-step reasoning of any depth — this is where the tier gap is real, not cosmetic
- Long inputs: 200K context vs the 5-family's 1M — big codebases and document sets don't fit
- Agentic sessions: tool-use judgment and error recovery trail the bigger tiers
- Anything you'd hesitate to ship without review

## Effort behavior (this model)

- **The effort dial does not apply** — Haiku 4.5 does not support the effort parameter. It has one speed: fast.
- Routing consequence: if a task needs "Haiku but more careful," the answer is Sonnet at low effort, not Haiku tuned up.
