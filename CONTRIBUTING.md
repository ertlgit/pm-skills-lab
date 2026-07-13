# Contributing to pm-skills-lab

Thanks for your interest in contributing. This repo is a curated collection
of agent skills for product managers, usable from Claude Code, Cursor,
Codex CLI, and other agents that support the skills format. Contributions
are welcome if they meet the quality bar below.

---

## What makes a good contribution

A skill is worth adding if it:
- Solves a real, recurring PM problem that a coding agent can meaningfully help with
- Is not already covered by an existing skill in this repo
- Produces a concrete, usable output (a file, a record, or a structured
  checkpoint the PM acts on)
- Works reliably in both manual and agent modes where applicable
- Stays lightweight — no backends, no APIs, no complex dependencies

A skill is not worth adding if it:
- Duplicates existing skills with minor wording differences
- Produces output a PM would not actually commit or reuse
- Requires external services or credentials to function
- Is a general writing or summarization helper with no PM-specific structure

---

## How to suggest a new skill

Open an issue using the Feature Request template.

Include:
- The PM problem it solves
- Why existing skills do not cover it
- A one-paragraph description of the output it produces
- Whether you plan to build it or are suggesting it for others

---

## How to report a problem with an existing skill

Open an issue using the Bug Report template.

Include:
- Which skill is affected
- What input you provided
- What output you got
- What output you expected
- Which agent you use (Claude Code, Cursor, Codex CLI, ...) and its
  version if known

---

## How to submit a skill via PR

1. Fork the repo
2. Create a folder under the repo root named after your skill,
   using kebab-case: `my-skill-name/`
3. Your skill folder must contain at minimum:
   - `SKILL.md` — activation rules, output definition, output behavior
   - One worked example in an `examples/` subfolder
   - A template or reference files where the skill's output follows a
     fixed structure (see decision-log for a template-based skill and
     comprehend-first for a reference-based one)
4. Add a one-line entry to the skills table in the root `README.md`
5. Open a PR with a short description of what the skill does and
   why it is differentiated from existing skills

---

## Skill quality checklist before submitting a PR

- [ ] SKILL.md has a clear activation trigger that does not over-fire
- [ ] SKILL.md has a significance gate or equivalent scope boundary
- [ ] Output is a concrete, reusable artifact — a committed file or a
      structured checkpoint output — not free-form chat
- [ ] Templates or reference files match the definitions in SKILL.md exactly
- [ ] At least one worked example shows realistic output
- [ ] No invented metrics, fabricated outputs, or overclaimed scope
- [ ] No external dependencies required to use the skill

---

## What to expect after submitting

PRs are reviewed on a best-effort basis. Expect a response within two weeks.
If a PR is declined, the reason will be stated. The most common reasons are:
scope overlap with an existing skill, output that does not map to a real PM
workflow, or a template that does not match the SKILL.md definitions.

---

## Questions

Open an issue with the label `question`. No need for a formal template.