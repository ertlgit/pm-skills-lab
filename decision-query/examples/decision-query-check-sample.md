# decision-query: Check Mode Example

This example shows the output of `check decisions:` against a realistic
set of product decision records. The input is a PRD section proposing a
new onboarding initiative. The skill identifies a conflict, a dependency,
and a constraint, and returns a CLEAR summary for areas with no matches.

---

## Input

**Invocation:**

```
check decisions: our Q3 initiative proposes building a custom in-app
onboarding flow using an internal engineering team. The goal is to
reduce time-to-first-value for new enterprise customers. We plan to
use our existing Postgres database to store onboarding state and
progress tracking.
```

**Decision records present:**

- DL-2026-04-001 — Use Appcues for user onboarding instead of building
  an in-house onboarding flow (accepted)
- DL-2026-04-002 — Use Figma for design instead of Sketch (accepted)
- DL-2026-04-003 — Use RudderStack as CDP instead of Segment (accepted)
- DL-2026-04-004 — Use Postgres as primary database instead of MongoDB
  (accepted)
- DL-2026-04-005 — Use Linear for issue tracking instead of Jira
  (accepted)

---

## Output

```
Checking against 5 decision records

CONFLICT
DL-2026-04-001 — Use Appcues for user onboarding instead of building
an in-house onboarding flow (accepted)
Your proposal to build a custom in-house onboarding flow directly
contradicts this decision. The team previously evaluated this trade-off
and chose Appcues to avoid engineering overhead.
Recommended action: Add a section to the PRD explaining what has changed
since DL-2026-04-001 — new requirements, changed constraints, or a
re-evaluation of Appcues — before proceeding with the in-house build.

DEPENDENCY
DL-2026-04-004 — Use Postgres as primary database instead of MongoDB
(accepted)
Your proposal stores onboarding state in Postgres. This is consistent
with the existing decision. Confirm the onboarding schema has been
reviewed against current Postgres capacity and indexing constraints.

CLEAR
No conflicts found for: design tooling, CDP and analytics pipeline,
issue tracking workflow.
```

---

## Notes on this example

**Why CONFLICT appears here:**
The proposal to build in-house directly contradicts DL-2026-04-001,
which explicitly chose Appcues over an in-house build. The skill
surfaces this because the decision-statement and rationale in
DL-2026-04-001 directly address the same trade-off.

**Why DEPENDENCY appears instead of CONFLICT for Postgres:**
The proposal is consistent with DL-2026-04-004, not contradicting it.
Using Postgres for onboarding state is aligned with the prior decision.
The skill flags it as a dependency because the proposal builds on the
prior decision rather than conflicting with it.

**Why the other records return CLEAR:**
Design tooling (Figma), CDP choice (RudderStack), and issue tracking
(Linear) are unrelated to an onboarding flow proposal. The skill checks
them and confirms no overlap rather than silently ignoring them.

**What the PM should do next:**
Address the CONFLICT in the PRD before proceeding. Either document why
the Appcues decision is being reconsidered, or revise the proposal to
work within the existing Appcues commitment.