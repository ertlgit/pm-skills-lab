# pm-skills-lab

A growing collection of Claude Code skills for product managers.

Each skill is a self-contained folder with a `SKILL.md` that Claude Code
activates automatically when it detects the right context in your request.

---

## Skills

| Skill | What it does | Status |
|-------|-------------|--------|
| [decision-log](./decision-log/) | Turns product decisions into structured, searchable markdown records committed to git | Available |
| [decision-check](./decision-check/) | Validates PRDs, OKRs, and proposals against existing decision records | Planned |

---

## Roadmap

`pm-skills-lab` is a growing collection. Skills are added when a real PM
problem is validated and a skill can solve it reliably without adding
process overhead.

Planned skills:

- **decision-check** — validate a PRD, OKR, proposal, or email draft
  against your existing decision records. Surfaces conflicts, dependencies,
  and constraints before you commit to a direction.
- **decision-review** — scan your decisions folder for records with a
  `review-date` approaching or past. Prompts you to confirm, update, or
  supersede.
- **decision-search** — query your decisions folder by topic, owner,
  status, date range, or regulatory flag.

Contributions welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md).

---

## How to install a skill

Copy the skill's `SKILL.md` into your Claude Code skills folder:

```bash
cp decision-log/SKILL.md .claude/skills/decision-log.md
```

Repeat for each skill you want to activate. Claude Code will pick it up
automatically.

---

## Contributing

Contributions welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md) for
guidelines on adding skills, reporting issues, and the skill quality
checklist.

Known issues and planned improvements are tracked in [BACKLOG.md](./BACKLOG.md).

---

## License

MIT. Use it, adapt it, contribute back if you improve it.
