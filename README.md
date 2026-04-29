# pm-skills-lab

A growing collection of Claude Code skills for product managers.

Each skill is a self-contained folder with a `SKILL.md` that Claude Code
activates automatically when it detects the right context in your request.

---

## Skills

| Skill | What it does |
|-------|-------------|
| [decision-log](./decision-log/) | Turns product decisions into structured, searchable markdown records committed to git |

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

Contributions welcome. Each skill lives in its own folder with a `SKILL.md`,
a template, and at least one example. Open a PR with your skill folder and
a one-line description for the table above.

---

## License

MIT. Use it, adapt it, contribute back if you improve it.