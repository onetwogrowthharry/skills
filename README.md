# OneTwo Growth Skills

Skills from [Harry Siggins'](https://onetwogrowth.com) AI enablement practice. These are the tools I install with the teams I work with, published so they keep working after the workshop ends.

Currently one skill: **/route**.

## /route

Most people run every task on the biggest model at the highest effort, or they never change the defaults at all. Both cost you: one burns tokens and time on work a cheaper setting handles fine, the other quietly caps the quality of your hardest work.

`/route` fixes the decision, not just the output. Describe a task and it returns:

1. A read-back of your task and its assumptions
2. The call: model, effort level, and setup, with the reasoning
3. Two grounded alternatives, one lighter and one heavier, with the real tradeoff
4. The principle behind the call, so you need the skill a little less each time
5. A handoff prompt you can paste into a fresh session and run

Every capability claim traces to bundled reference files built from Anthropic's documentation, model cards, and published benchmarks. No invented numbers.

## Install (Claude Code)

Add the marketplace, then install the plugin:

```
/plugin marketplace add onetwogrowthharry/skills
```

```
/plugin install onetwo-skills@onetwo
```

Then use it:

```
/route I want to summarize 40 customer interviews into a themes report
```

Installed this way, the skill updates automatically when a new version ships. Model facts change often, so this is the recommended path.

### Manual install

Copy `skills/route/` into your project's `.claude/skills/` folder. You own the copy; it will not receive updates. Check the `as_of` dates in `skills/route/references/` before trusting the numbers.

## How it stays current

Model prices, benchmarks, and effort behavior change with every release. The bundled reference files are dated (`as_of`) and regenerated on a documented process; see [RUNBOOK.md](RUNBOOK.md) for how the numbers are sourced and verified. If a reference file predates a model release you care about, open an issue.

## License

MIT. Use it, adapt it, teach with it. Attribution appreciated.
