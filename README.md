# pm-skills-lab

A growing collection of Claude Code skills for product managers.

Each skill is a self-contained folder with a `SKILL.md` that Claude Code
activates automatically when it detects the right context in your request.

---

## Skills

| Skill | What it does | Status |
|-------|-------------|--------|
| [decision-log](./decision-log/) | Turns product decisions into structured, searchable markdown records committed to git | Available |
| [decision-query](./decision-query/) | Check PRDs and proposals against existing decisions, search records, and surface decisions due for review | Available |

---

## Roadmap

`pm-skills-lab` is a growing collection. Skills are added when a real PM
problem is validated and a skill can solve it reliably without adding
process overhead.

Planned skills:
- **MCP integration** — connect decision-log to Slack and Linear
  via MCP for fully automated capture and ticketing. Planned after
  adoption signal from real PM teams.

Contributions welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md).

---

## How to install a skill

```bash
npx skills add ertlgit/pm-skills-lab
```

Select which skills to install from the interactive prompt. Claude Code
activates them automatically when it detects the right context in your
request. Re-run the same command to update to the latest version.

---

## Contributing

Contributions welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md) for
guidelines on adding skills, reporting issues, and the skill quality
checklist.

Known issues and planned improvements are tracked in [BACKLOG.md](./BACKLOG.md).

---

## License

MIT. Use it, adapt it, contribute back if you improve it.
