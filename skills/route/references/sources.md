# Sources of Truth

Ranked list of canonical sources. Every claim in `models/*.md` must trace to one of these. When sources conflict, the higher-ranked source wins. Anything uncited does not survive a regeneration pass — say "roughly comparable" instead of inventing a number.

## Rank 1 — Anthropic official documentation
**Authoritative for:** model lineup and IDs, pricing, context windows, output caps, effort mechanics, thinking behavior, feature availability.

| Source | URL | Use for |
|---|---|---|
| Models overview | https://platform.claude.com/docs/en/about-claude/models/overview | Lineup, IDs, context/output limits |
| Pricing | https://platform.claude.com/docs/en/pricing | $/MTok, caching and batch discounts |
| Effort parameter | https://platform.claude.com/docs/en/build-with-claude/effort | What effort levels do, per-model support |
| Adaptive thinking | https://platform.claude.com/docs/en/build-with-claude/adaptive-thinking | Thinking defaults per model |
| Migration guide | https://platform.claude.com/docs/en/about-claude/models/migration-guide | Behavioral shifts between generations — the richest source of "what it *feels* like" guidance |

**Caveat:** docs state capabilities, not comparisons. They will not tell you whether Sonnet is "good enough" for a task — that judgment comes from benchmarks plus the migration guide's behavioral notes.

## Rank 2 — Anthropic model announcements & system cards
**Authoritative for:** benchmark numbers as Anthropic reports them, headline capability claims, stated limitations.

- Announcement posts: `anthropic.com/news/<model>` (e.g. `/news/claude-fable-5-mythos-5`)
- System cards: linked from each announcement

**Caveats to carry into every model file:** (1) vendor-reported numbers are chosen to flatter — always name the benchmark so the claim is checkable; (2) announcement pages for mid-tier models (e.g. Sonnet) often omit scores entirely — the system card and third-party leaderboards fill that gap; (3) **announcement benchmark tables ship as images** — text fetches return the prose but not the numbers; exact scores must come from the system card PDF.

## Rank 3 — Anthropic engineering blog
**Authoritative for:** orchestration guidance — when subagents pay off, multi-agent patterns, context management.

- https://www.anthropic.com/engineering (esp. multi-agent research system posts)

**Caveat:** written for API builders; translate to Claude Code / Cowork surface terms before quoting to a router user.

## Rank 4 — Independent leaderboards
**Authoritative for:** third-party verification of coding claims.

| Source | URL | Use for |
|---|---|---|
| SWE-bench | https://www.swebench.com | Real-repo bug-fixing — the best single "can it code" check |
| Terminal-Bench | https://www.tbench.ai | Agentic terminal work — closest proxy for Claude Code sessions |

**Caveats:** (1) leaderboard entries vary by scaffold/harness; compare scores only within the same leaderboard configuration, and **never across benchmark versions** (OSWorld 2.0 ≠ OSWorld-Verified; Terminal-Bench 1.0 ≠ 2.1); (2) **the leaderboard pages are interactive JS tables** — text crawls return methodology, not score rows. Retrieve actual rows via a browser session, the leaderboards' published data (SWE-bench's GitHub experiments repo), or fall back to Rank 2 system cards.

## Rank 5 — Artificial Analysis
**Authoritative for:** measured speed, latency, tokens-per-second, cost-per-quality, and the Intelligence Index — which is citable because it is itself a composite of 9 named evals (v4.1: GDPval-AA v2, τ³-Banking, Terminal-Bench 2.1, SciCode, Humanity's Last Exam, GPQA Diamond, CritPt, AA-Omniscience, AA-LCR), measured independently and per effort setting. The best source for the *efficiency* half of every recommendation.

- https://artificialanalysis.ai

**Caveat:** speed/latency measure API serving performance, which shifts week to week; treat those as rough multiples ("~2× faster to first token"), never precise figures. Index scores are per model+effort configuration — always name which.

## Rank 6 — LMArena (directional only)
**Authoritative for:** nothing load-bearing. Human-preference vibes with selection bias.

- https://lmarena.ai

**Rule:** never cite an Arena Elo in a recommendation. At most: "users tend to prefer its writing style" — and only when it agrees with a higher-ranked source.

## Secondary aggregators (locators, not sources)
Benchmark-roundup sites (Vellum, MorphLLM, BenchLM, etc.) are useful for *locating* system-card numbers the primary pages hide in images — but a number sourced only from aggregators carries a **verify-against-primary flag** in the model file until confirmed against the system card. Two or more independent aggregators converging is the minimum bar for provisional inclusion.

## What is NOT a source
- Model priors / memory ("I recall Opus scores X") — this is where hallucinated benchmarks come from
- Twitter/X threads, YouTube reviews, blog hot-takes
- A benchmark number appearing in exactly one secondhand post
