---
name: decision-check
description: Validate a PRD, proposal, OKR, or email draft against existing decision records in the /decisions/ folder. Use this skill when the user wants to check whether a piece of content conflicts with or depends on prior product decisions. Status: planned — not yet implemented.
status: planned
license: MIT — see LICENSE in pm-skills-lab repo
---

# decision-check Skill for Claude Code

## Status

**Planned — not yet implemented.**

This skill is on the pm-skills-lab roadmap. It will be built after
`decision-log` has been validated in production use by real PM teams.

If you want to contribute to building this skill, open an issue in
[pm-skills-lab](https://github.com/ertlgit/pm-skills-lab) with your
proposed approach.

---

## What this skill will do

Scan the `/decisions/` folder and check a piece of PM content against
existing decision records. Surfaces conflicts, dependencies, and
constraints the PM should be aware of before committing to a direction.

Designed for use when:
- Writing a PRD or spec
- Crafting OKR themes or strategic proposals
- Drafting an email or proposal that involves product direction
- Reviewing a roadmap item before committing it to a sprint

---

## Planned behavior

**Input:** A PRD section, OKR draft, proposal, or email. Plus the path
to the decisions folder.

**Output:** A structured report covering:
- Conflicts: content that directly contradicts an accepted decision
- Dependencies: content that builds on or assumes a prior decision
- Constraints: accepted decisions that limit the scope of the proposal
- Clear: areas where no relevant decisions were found

**Example output format:**

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
