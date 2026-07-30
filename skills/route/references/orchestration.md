# Orchestration — when one agent isn't the right shape

as_of: 2026-07-27
sources: [Anthropic engineering blog (multi-agent research system), Claude Code docs]

Orchestration is a *shape* decision, made after the model/effort call. Default is always **one agent, one session** — every step up adds real overhead (each extra agent re-establishes context, explores, reports back, and the coordinator re-reads the report). Step up only when the task's shape forces it.

## The ladder

| Shape | Use when | Overhead |
|---|---|---|
| **One session** (default) | Task fits one context window and one thread of attention | None — start here |
| **One session + subagents** | A few genuinely independent chunks (read 5 unrelated modules, check 3 hypotheses in parallel) | Low — each subagent re-derives context |
| **Agent team / workflow** | Many-item fan-out (audit 40 files, migrate 100 call sites) or work that needs independent verification passes | High — worth it only at scale or when confidence must be earned adversarially |
| **Split into sequential sessions** | Work exceeds one context even with delegation; natural phase boundaries (understand → design → build → verify) | Human carries state between phases via written handoffs |

## The two honest reasons to orchestrate

1. **Too big for one context.** The working set (files, documents, findings) can't fit or can't stay coherent in one window. Delegating reads to subagents keeps the main thread clean.
2. **Confidence needs independence.** One agent checking its own work shares its own blind spots. A separate verifier with fresh context catches what self-review misses — Anthropic's own guidance: fresh-context verifier subagents outperform self-critique.

## Anti-patterns (the router should catch these)

- **Orchestrating for ceremony.** "It's a big important task" is not a reason — a hard-but-connected problem wants a bigger model in one session, not a committee.
- **Splitting one modest job into pieces.** Parallel agents on a task one agent finishes in a handful of steps multiplies cost for nothing.
- **Delegating the verification you could just do.** A second pass in the same session is often enough; reserve independent verifiers for high-stakes output.

## Model pairing for orchestrated work

- Coordinator: the biggest model the task deserves (it makes the judgment calls)
- Fan-out workers: Sonnet at low–medium effort (mechanical, parallel, cheap)
- Verifiers: Opus at low effort (accurate reviewer at reviewer prices)

## Surface availability

**The session's own tool declarations (SKILL.md step 1) are authoritative — this table is only the typical picture.** If the environment declares an Agent or Workflow tool, that rung exists regardless of what this table says.

| Surface | Typical menu |
|---|---|
| Claude Code | Subagents, agent teams, workflows, background tasks — the full ladder |
| Cowork | Claude Code harness underneath — subagents and background tasks usually available; check the session's declared tools |
| claude.ai chat | One conversation; "orchestration" = the user splitting work across chats with written handoffs |

If the task genuinely wants a rung the user's surface doesn't have, recommend the best in-surface route and name the upgrade path in one sentence.
