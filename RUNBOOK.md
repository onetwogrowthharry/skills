# Route Skill — Reference Regeneration Runbook

Maintainer doc (Harry-side). Not part of the skill's runtime behavior — this is how the bundled research stays honest. Excluded from what the skill reads at runtime.

## When to regenerate

- **A new Claude model ships** (announcement from Anthropic) → regenerate the new model's file, re-check comparative claims in every other model file that names it or its predecessor
- **Pricing changes** → update Cost & speed sections + any cost anchors ("half the cost of X")
- **Quarterly staleness check** (calendar reminder): if no release happened, verify `as_of` claims still hold against Rank 1 sources and bump the dates

## The regeneration pass (per model, ~half day for a full lineup refresh)

1. **Pull Rank 1 facts** — models overview + pricing + effort docs. These fill: model ID, context, output cap, $/MTok, effort ladder support, thinking defaults. Zero judgment, pure transcription.
2. **Pull the numbers — know where they actually live** (learned empirically 2026-07-27):
   - Anthropic **announcement pages embed benchmark tables as images** — text fetches get prose only. The exact scores are in the **system card PDF** linked from each announcement. Read the PDF directly.
   - **Primary leaderboards (swebench.com, tbench.ai, artificialanalysis.ai) are interactive JS tables** — crawlers return methodology, not rows. Use a browser session to read them, or SWE-bench's GitHub experiments repo for raw data.
   - **Secondary aggregators** (Vellum, MorphLLM, BenchLM) surface system-card numbers in plain text — usable as locators with 2+ converging, but every aggregator-sourced number carries a verify flag until checked against the system card.
   - Never mix benchmark versions in a comparison (OSWorld 2.0 vs -Verified, Terminal-Bench 1.0 vs 2.1).
3. **Run deep research for the benchmark story** — one deep-research pass per new model with this brief:
   > For [model], collect: (a) every named benchmark result from the Anthropic announcement and system card, with scores; (b) independent verification from SWE-bench and Terminal-Bench leaderboards; (c) Artificial Analysis speed/latency/cost-per-quality measurements; (d) the migration guide's behavioral-shift notes. For each benchmark, state in one plain-English sentence what the result means for a practical task, and one caveat about what the benchmark does not measure. Flag any claim you could not verify in two independent sources.
4. **Fill the fixed schema** (`references/models/<id>.md`): Cost & speed → **Scorecard** (exact numbers, comparison columns, provenance line) → Benchmark story translated → Sweet spot / Falls short → Effort behavior. The scorecard is the quantitative core the router prescribes from; the story translates it. Every claim: named source + practical consequence + one caveat line. No uncited numbers.
5. **Cross-file consistency sweep** — comparative anchors ("half the cost of", "near-Opus") appear in multiple files; grep for the old model's name across `references/` and update every hit.
6. **Stamp and ship** — bump `as_of` in every touched file, commit, push to the public repo. Plugin installs update automatically; chat/Cowork installs stay stale until reinstalled (the `as_of` stamp is their only staleness signal — never remove it).
7. **Smoke test** — run `/route` on the three canonical test requests (vague dashboard ask / well-specced migration / trivial one-liner) and check the alternatives cite the new data correctly.

## Schema (fixed — do not drift)

```
# <Model name>
as_of / model_id / sources
## Cost & speed        ($/MTok, plain-English cost anchor, context, output cap, tokenizer notes)
## Scorecard           (table: exact scores + comparison columns + what each measures; provenance line w/ verify flags)
## Benchmark story, translated   (reads off the scorecard: number → practical consequence → caveat, per claim)
## Sweet spot          (3-4 concrete task types)
## Falls short         (3-4 concrete task types)
## Effort behavior (this model)  (ladder support, defaults, model-specific quirks)
```

## Source discipline

Ranked list lives in `references/sources.md`. Higher rank wins conflicts. Uncited claims get deleted, not softened. Where the announcement page has no scores (common for Sonnet-tier), the system card and Rank 4 leaderboards fill the gap — if nothing does, the file says "no published scores; positioned as X" rather than inventing.
