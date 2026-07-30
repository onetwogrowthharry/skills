# Harry Siggins Skills

Agent skills from my AI enablement practice at [OneTwo Growth](https://onetwogrowth.com). These are the tools I install with the teams I work with, published so they keep working after the workshop ends.

They are built to be small, grounded, and checkable. Every capability claim traces to a dated reference file you can open and read for yourself. Nothing is invented, and nothing fetches numbers at runtime.

They follow the open [Agent Skills](https://agentskills.io) standard, so they run in Claude Code, Cowork, claude.ai, and any other agent that reads skills. What they recommend is Anthropic models. Where you run them is up to you.

Currently one skill: **route**.

## route

**The problem.** There are two easy defaults: run everything on the biggest model at the highest effort, or never touch the settings at all. The first pays frontier prices for work a cheaper setting handles. The second quietly caps the quality of your hardest work. Both are invisible from the inside, which is why they last.

**The fix.** Describe a task and `route` gives you back:

1. A read-back of your task and the assumptions it is working from
2. The call: model, effort level, and setup, with the reasoning
3. Two grounded alternatives, one lighter and one heavier, with the real tradeoff
4. The principle behind the call, so you need the skill a little less each time
5. A handoff prompt you can paste into a fresh session and run

It works on the decision, not just the output. Step 4 is the point. The goal is that you stop reaching for it.

## Install

Three ways in. They differ in one thing: who owns the copy.

The **plugin** is a managed bundle. It updates when I ship a new version, so you subscribe rather than fork. Model facts go stale quickly, so this is the path I would suggest wherever it is available.

The **installer** and the **zip** hand you a copy you own and can edit. Nothing changes behind your back, and nothing updates in front of you either. Check the `as_of` dates in the reference files before trusting the numbers, because nothing will refresh them for you.

<details>
<summary><strong>Claude Code</strong> (plugin, updates when I ship)</summary>

Add the marketplace, then install:

```
/plugin marketplace add onetwogrowthharry/skills
```

```
/plugin install harry-siggins-skills@onetwo
```

Then use it:

```
/harry-siggins-skills:route I want to summarize 40 customer interviews into a themes report
```

Plugin skills are namespaced, so the `harry-siggins-skills:` prefix is part of the command rather than something you can drop.

If you would rather own the files, copy `skills/route/` into your project's `.claude/skills/` folder and run it as `/route`. Do one or the other. Doing both leaves you with the same skill under two names.

</details>

<details>
<summary><strong>Cursor, Copilot, Zed, and other agents</strong> (editable copy)</summary>

```bash
npx skills@latest add onetwogrowthharry/skills
```

Choose which agents to install to. It writes the skill into your project as ordinary files you own and can edit; run `npx skills update` when you want my later changes.

One thing to know first: `route` recommends Anthropic models and nothing else. That is coherent if you run Claude inside your agent, which Cursor, Windsurf, Zed, and Copilot all support. It has little to offer in an agent wired to a different provider.

The installer is [vercel-labs/skills](https://github.com/vercel-labs/skills), which I do not maintain.

</details>

<details>
<summary><strong>Cowork and claude.ai</strong> (zip upload)</summary>

1. Download `route.zip` from the [latest release](https://github.com/onetwogrowthharry/skills/releases/latest).
2. In Claude, open **Customize → Skills**, click **+**, then **Create skill**, and upload the zip.
3. Enable the skill.

**Code execution has to be turned on** for this to work, under Settings → Capabilities. `route` reads its reference files at runtime, so without code execution it cannot reach its own evidence base, and an answer it gives you under those conditions is not grounded in anything.

Cowork also has plugin support in research preview, so the plugin path above may reach it directly before long. That is moving quickly, so the zip is the route I can vouch for today.

</details>

## How it stays current

Model prices, benchmarks, and effort behavior change with every release. The bundled reference files are dated (`as_of`) and regenerated through a documented process; see [RUNBOOK.md](RUNBOOK.md) for how the numbers are sourced and verified. If a reference file predates a model release you care about, open an issue.

## License

MIT. Use it, adapt it, teach with it. Attribution appreciated.
