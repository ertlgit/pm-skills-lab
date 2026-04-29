---
name: decision-query
description: "Work with existing decision records in the /decisions/ folder. Check a PRD, proposal, OKR, or email for conflicts with prior decisions. Search records by topic, owner, or status. Surface decisions due for review. Status: planned — not yet implemented."
status: planned
license: "MIT — see LICENSE in pm-skills-lab repo"
---

# decision-query Skill for Claude Code

## Status

**Planned — not yet implemented.**

This skill is on the pm-skills-lab roadmap. It will be built after
`decision-log` has been validated in production use by real PM teams.

If you want to contribute to building this skill, open an issue in
[pm-skills-lab](https://github.com/ertlgit/pm-skills-lab) with your
proposed approach.

---

## What this skill will do

Work with existing decision records in the `/decisions/` folder across
three modes detected automatically from the invocation:

- **Check** — validate a PRD, OKR, proposal, or email draft against
  existing records. Surfaces conflicts, dependencies, and constraints.
- **Search** — query records by topic, owner, status, date range, or
  regulatory flag. Returns matching records with one-line summaries.
- **Review** — scan for records with a `review-date` approaching or
  past. Prompts you to confirm, update, or supersede.

Designed for use when:
- Writing a PRD or spec
- Crafting OKR themes or strategic proposals
- Reviewing roadmap items before committing to a sprint
- Onboarding a new team member to existing product constraints

---

## Planned behavior

**Invocation patterns:**

```
check decisions: [paste PRD, OKR, proposal, or email]
search decisions: [topic, owner name, status, or keyword]
review decisions
```

**Check mode output:** conflicts, dependencies, constraints, and clear
areas as a structured scannable report.

**Search mode output:** matching decision records with decision-id,
date, decision-statement, and status per result.

**Review mode output:** records where review-date is past or within
30 days, with a prompt to confirm, update, or supersede each.

**Check mode example:**

```
Checking against 12 decision records in /decisions/

CONFLICT
DL-2026-04-002 — Adopt Sentry for error monitoring (accepted)
Your PRD mentions custom error logging. This contradicts the decision
to standardize on Sentry.

DEPENDENCY
DL-2026-04-001 — Use Notion for internal wiki (accepted)
Your proposal references a shared knowledge base. Notion is the
confirmed platform for this.

CLEAR
No conflicts found for: pricing model, release cadence, API design.
```

---

## Design principles (for contributors)

- Never fabricate conflicts. Only surface genuine contradictions between
  the input content and the decision record field values.
- Flag dependencies separately from conflicts. A dependency is not a
  blocker, a conflict is.
- Keep output scannable. One conflict per block, clear label, one-line
  explanation.
- Do not require the user to specify which decisions to check against.
  Scan all records in /decisions/ automatically.
- Mark [NEEDS REVIEW] on any match where the conflict is ambiguous
  rather than stating it as definitive.
