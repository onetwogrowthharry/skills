# Effort — what it actually is

as_of: 2026-07-27
sources: [effort docs, migration-guide]

Effort is a dial on how much the model thinks and works per request — reasoning depth, tool-call thoroughness, verification, and preamble all scale with it. It is **not** a quality dial you always want at max: past the sweet spot you pay more tokens and wait longer for the same answer, and at the top settings models can overthink simple tasks.

## The ladder

| Level | What changes | Reach for it when |
|---|---|---|
| low | Fewest, most-consolidated tool calls; terse; does exactly what was asked | Small scoped tasks, latency-sensitive chat, subagent workers |
| medium | Balanced; often the cost/quality sweet spot for routine work | Everyday tasks where high feels slow |
| high | **The default.** Full reasoning on most work | Most intelligence-sensitive work — the safe starting point |
| xhigh | Deep multi-step reasoning, more tool use, more self-verification | The hardest coding and agentic tasks |
| max | Ceiling; correctness over cost; can overthink | Rare: correctness matters far more than time or tokens |

## Rules of thumb (durable across model generations)

1. **Effort scales with stakes and ambiguity, not with how impressive the task sounds.** A big-but-mechanical job (rename across 200 files) runs fine at low; a small-but-subtle one (why does this test flake?) deserves high+.
2. **Start at the default (high), sweep down.** On current models, low and medium punch above their weight — step down where quality holds, don't start at the bottom and get burned.
3. **At xhigh/max, give output headroom.** Thinking shares the output-token budget; a tight cap truncates the answer mid-thought.
4. **Effort is per-model.** The same level means different depths on different models — check the model's own file for its effort notes.
5. **Verification beats brute force.** If wrongness is the worry, a second checking pass at normal effort often beats one pass at max.
