# pm-skills-lab

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Skills](https://img.shields.io/badge/skills-3-brightgreen)
![Works with](https://img.shields.io/badge/works%20with-Claude%20Code%20·%20Cursor%20·%20Codex-8A2BE2)
![Last commit](https://img.shields.io/github/last-commit/ertlgit/pm-skills-lab)

Agent skills for product managers. Works with Claude Code, Cursor, Codex
CLI, and any other agent that supports the skills format.

You hand an AI agent a brief and it acts on the literal wording, missing
what the document was actually asking. Your team's decisions get made in
Slack and re-litigated six months later because nobody remembers the
rationale. These skills fix both: comprehension before action, and
decisions as searchable records committed to git.

![comprehend-first reads an exec brief, translates its real intent, and stops at a checkpoint before any work begins](./assets/demo.gif)

*comprehend-first on an exec brief: the real ask vs. the literal ask, the
traps a shallow reading would hit, and a checkpoint — no work begins until
you confirm the reading.*

---

## Install

```bash
npx skills add ertlgit/pm-skills-lab
```

Select which skills to install from the interactive prompt. The installer
places each skill where your agent expects it — Claude Code, Cursor, Codex
CLI, and 20+ other agents are supported. Re-run the same command to update
to the latest version.

---

## Skills

In workflow order — understand the brief, do the work, record what was
decided, check new work against it:

| Skill | What it does | Status |
|-------|-------------|--------|
| [comprehend-first](./comprehend-first/) | Understand a document before acting on it. Translates each part's real intent, names the traps a shallow reading hits, and stops for your confirmation. | Available |
| [decision-log](./decision-log/) | Turns product decisions into structured, searchable markdown records committed to git | Available |
| [decision-query](./decision-query/) | Check PRDs and proposals against existing decisions, search records, and surface decisions due for review | Available |

### comprehend-first, in one example

Agents fail on briefs through specification literalism: satisfying the
visible form of a requirement while missing its function. "The
recommendation must weigh cost, migration effort, and developer
experience" becomes "name the three criteria" — and every later pass
polishes the form without repairing the missing function. comprehend-first
catches this at the reading stage, where it is cheap to fix:

```
comprehend first: [paste the brief, spec, or RFP]
```

The agent translates what each part is actually asking, flags what is
missing rather than inventing it, and stops for you to confirm the
reading before any work begins.

---

## How the skills work together

```
brief / spec / RFP / PRD / strategy doc
        ↓
comprehend-first · intent-translation dossier → you confirm the reading
        ↓
the real work (PRD, plan, analysis, deck, ...)
        ↓
decision-log · decisions preserved in DECISIONS.md or /decisions/
        ↓
decision-query · new PRDs, OKRs, and proposals checked against them
```

Each skill also works standalone. comprehend-first is the front door for
document-driven work; the two decision skills turn what results into a
durable, queryable record.

---

## Per-agent notes

The skills are plain markdown and agent-agnostic. Two things differ per
agent:

| Agent | Project instructions file | Verify install |
|-------|---------------------------|----------------|
| Claude Code | `CLAUDE.md` | run `/skills` |
| Codex CLI | `AGENTS.md` | check the `npx skills add` output |
| Cursor | `.cursor/rules` | check the `npx skills add` output |

Where a skill README shows a project integration tip (loading
`DECISIONS.md` as context, running the comprehension gate by default),
put the same text in your agent's instructions file from the table above.

---

## Roadmap

`pm-skills-lab` is a growing collection. Skills are added when a real PM
problem is validated and a skill can solve it reliably without adding
process overhead.

Planned skills:
- **MCP integration** — connect decision-log to Slack and Linear
  via MCP for fully automated capture and ticketing. Planned after
  adoption signal from real PM teams.

---

## Contributing

Contributions welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md) for
guidelines on adding skills, reporting issues, and the skill quality
checklist.

Known issues and planned improvements are tracked in [BACKLOG.md](./BACKLOG.md).

---

## License

MIT. Use it, adapt it, contribute back if you improve it.
