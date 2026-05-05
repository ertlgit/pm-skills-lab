# decision-query

A Claude Code skill that helps product managers work with existing decision
records. Check PRDs and proposals for conflicts, search decisions by topic
or owner, and surface decisions due for review.

> This skill is read-only. It never modifies decision records. Use
> [decision-log](../decision-log/) to create or update records.

---

## Why this exists

Logging decisions is only half the value. The other half is using them.
Without a way to query existing records, the decisions folder becomes an
archive nobody consults. decision-query turns it into an active constraint
layer that surfaces relevant prior decisions exactly when they matter.

---

## Where it fits in the PM workflow

1. **Decisions accumulate** in `DECISIONS.md` or `/decisions/` via
   decision-log
2. **New work begins** — a PRD, OKR, roadmap item, or proposal
3. **This skill checks** whether the new work conflicts with, depends
   on, or is constrained by existing decisions
4. **The PM acts** — resolves conflicts, adds context, or updates
   outdated decisions before committing to a direction

---

## Three modes

**Check** — validate content against existing decisions.

```
check decisions: [paste PRD section, OKR, proposal, or email]
```

Surfaces conflicts, dependencies, and constraints. Ends with a CLEAR
summary of areas where no relevant decisions were found.

**Search** — find decisions by topic, owner, or status.

```
search decisions: [topic, owner name, keyword, or status]
```

Returns matching records with decision-id, statement, status, date,
and owner.

**Review** — surface decisions due for revisit.

```
review decisions
```

Lists records where `review-date` is past or within 30 days. Flags
records with no review date set.

---

## What gets scanned

The skill automatically scans both locations:

- `DECISIONS.md` in the project root
- `/decisions/` subfolder with individual `DL-YYYY-MM-NNN-slug.md` files

No configuration needed. If neither exists, the skill will tell you to
use decision-log to start logging decisions.

---

## Installation

### Quick install (recommended)

```bash
mkdir -p ~/.claude/skills/decision-query && \
curl -o ~/.claude/skills/decision-query/SKILL.md \
https://raw.githubusercontent.com/ertlgit/pm-skills-lab/main/decision-query/SKILL.md
```

### Manual install

```bash
mkdir -p ~/.claude/skills/decision-query
cp decision-query/SKILL.md ~/.claude/skills/decision-query/SKILL.md
```

### Verify installation

Open Claude Code in any project folder and run:

```
/skills
```

You should see `decision-query` listed under available skills.

### Update to latest version

```bash
curl -o ~/.claude/skills/decision-query/SKILL.md \
https://raw.githubusercontent.com/ertlgit/pm-skills-lab/main/decision-query/SKILL.md
```

---

## Usage examples

### Check mode

Input:

```
check decisions: our Q3 roadmap proposes migrating our data pipeline
to a streaming architecture and building a custom analytics dashboard
on top of it.
```

Output:

```
Checking against 8 decision records

CONFLICT
DL-2026-04-005 — Use RudderStack as CDP instead of Segment (accepted)
Your proposal builds a custom dashboard on top of the data pipeline.
RudderStack includes built-in reporting. Confirm this was evaluated
before committing to a custom build.
Recommended action: Add a section to the PRD explaining why RudderStack
dashboarding does not meet the requirement.

DEPENDENCY
DL-2026-04-004 — Use Postgres as primary database (accepted)
Your streaming pipeline will need to integrate with or replace the
existing Postgres data store. Confirm this was scoped.

CLEAR
No conflicts found for: release cadence, pricing model, team tooling.
```

### Search mode

Input:

```
search decisions: owner Engineering Lead
```

Output:

```
Found 2 decisions matching "owner: Engineering Lead"

DL-2026-05-002 — Use Linear for issue tracking instead of Jira
Status: accepted | Date: 2026-05-05 | Owner: Engineering Lead

DL-2026-04-004 — Use Postgres as primary database instead of MongoDB
Status: accepted | Date: 2026-04-29 | Owner: Engineering Lead
```

### Review mode

Input:

```
review decisions
```

Output:

```
Decision review — 2026-05-05

OVERDUE
DL-2026-03-001 — Use Segment for analytics (accepted)
Review date: 2026-04-01 (34 days overdue)
Owner: Head of Product
Action: confirm still valid / update / supersede

NO REVIEW DATE SET
6 decisions have no review-date. Consider adding one to decisions
that involve vendor lock-in, budget assumptions, or time-sensitive
tradeoffs.
```

---

## Skill structure

```
decision-query/
├── SKILL.md
├── README.md
└── examples/
    ├── decision-query-check-sample.md
    └── decision-query-search-sample.md
```

---

## Pair with decision-log

decision-query is read-only. To log new decisions or update existing
ones, use the [decision-log](../decision-log/) skill.

```
log decision: [your decision]            → appends to DECISIONS.md
log decision (new file): [your decision] → creates individual file
```