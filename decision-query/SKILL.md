---
name: decision-query
description: "Work with existing decision records. Use this skill to check a PRD, OKR, proposal, or email for conflicts with prior decisions, search decision records by topic or owner, or surface decisions due for review. Invocation patterns: 'check decisions:', 'search decisions:', 'review decisions'."
license: "MIT — see LICENSE in pm-skills-lab repo"
---

# decision-query skill

## What this skill does

Reads existing decision records and helps PMs work with them in three modes:

- **Check** — validate a PRD, OKR, proposal, or email draft against
  existing records. Surfaces conflicts, dependencies, and constraints
  before the PM commits to a direction.
- **Search** — query records by topic, owner, status, date range, or
  keyword. Returns matching records with one-line summaries.
- **Review** — scan for records with a `review-date` approaching or
  past. Prompts the PM to confirm, update, or supersede each.

This skill is read-only. It never modifies decision records.
Use the decision-log skill to create or update records.

---

## When to activate this skill

Activate when the input contains one of these invocation patterns:

Check mode signals:
- "check decisions:", "check this against my decisions"
- "does this conflict with any decisions"
- "check my PRD / OKR / proposal / email against decisions"
- "any conflicts with existing decisions"

Search mode signals:
- "search decisions:", "find decisions about [topic]"
- "what decisions have we made about [topic]"
- "show decisions owned by [name]"
- "find accepted / proposed / superseded decisions"

Review mode signals:
- "review decisions", "what decisions are due for review"
- "show decisions past their review date"
- "which decisions need revisiting"

Do not activate for:
- Requests to log or create a new decision (use decision-log)
- General questions not referencing existing decision records
- PRD writing assistance without a check request

---

## Where to find decision records

Always scan both locations. Check DECISIONS.md first, then /decisions/.

1. `DECISIONS.md` in the current working directory or project root
2. `/decisions/` subfolder — individual DL-YYYY-MM-NNN-slug.md files

If neither exists, respond:
"No decision records found in this project. Use the decision-log skill
to start logging decisions."

If only one location exists, use it without mentioning the other.

---

## Check mode

### Input
A piece of PM content: PRD section, OKR draft, proposal, roadmap item,
or email. Pasted directly or referenced by filename.

### Behavior
1. Read all decision records from both locations
2. Identify records relevant to the input content
3. For each relevant record, classify the relationship:
   - CONFLICT: input directly contradicts an accepted decision
   - DEPENDENCY: input builds on or assumes a prior decision
   - CONSTRAINT: an accepted decision limits the scope of the proposal
   - CLEAR: no relevant decisions found for this area

4. Produce a structured report

### Output format

```
Checking against [N] decision records

CONFLICT
[decision-id] — [decision-statement] ([status])
[One sentence explaining the specific contradiction]
Recommended action: [one sentence on how to resolve]

DEPENDENCY
[decision-id] — [decision-statement] ([status])
[One sentence explaining the dependency]

CONSTRAINT
[decision-id] — [decision-statement] ([status])
[One sentence explaining the constraint on the proposal]

CLEAR
No conflicts found for: [list of topics checked that had no matches]
```

### Rules for check mode
- Never fabricate conflicts. Only surface genuine contradictions between
  the input content and the decision record field values.
- Flag DEPENDENCY separately from CONFLICT. A dependency is not a
  blocker, a conflict is.
- Flag CONSTRAINT separately from CONFLICT. A constraint limits scope
  but does not contradict the proposal.
- Keep output scannable. One block per finding, clear label, two
  sentences maximum per finding.
- Mark [NEEDS REVIEW] on any match where the conflict is ambiguous
  rather than stating it as definitive.
- If no relevant decisions are found for any area, state CLEAR with
  the topics checked.
- Always end with a recommendation if a CONFLICT was found.

---

## Search mode

### Input
A topic, keyword, owner name, status value, or date range.

### Behavior
Scan all decision records and return matches. Match against:
- decision-statement text
- owner field
- status field
- rationale and context text
- tags in optional extension block if present

### Output format

```
Found [N] decisions matching "[query]"

[decision-id] — [decision-statement]
Status: [status] | Date: [date] | Owner: [owner]

[decision-id] — [decision-statement]
Status: [status] | Date: [date] | Owner: [owner]
```

If no matches: "No decisions found matching [query]."

### Rules for search mode
- Return the full list of matches without truncating
- Do not summarize or paraphrase decision-statement
- Sort by date, most recent first
- If the query matches partial text, include the match and note which
  field it matched in

---

## Review mode

### Input
No additional input required. "review decisions" is sufficient.

### Behavior
Scan all decision records for:
- Records where `review-date` is today or in the past
- Records where `review-date` is within the next 30 days

### Output format

```
Decision review — [current date]

OVERDUE
[decision-id] — [decision-statement]
Review date: [date] ([N] days overdue)
Owner: [owner]
Action: confirm still valid / update / supersede

DUE SOON
[decision-id] — [decision-statement]
Review date: [date] ([N] days remaining)
Owner: [owner]

NO REVIEW DATE SET
[N] decisions have no review-date. Consider adding one if they involve
time-sensitive assumptions or regulatory implications.
```

If no records have review dates set: state that and suggest setting
review-date on decisions that involve time-sensitive assumptions.

### Rules for review mode
- Never modify decision records during review mode
- Prompt the PM to act, do not act on their behalf
- If a decision is overdue, flag it clearly without alarm language

---

## General rules

- This skill is read-only. Never write to, modify, or delete any
  decision record.
- Never fabricate decision content. Only surface what exists in the
  records.
- If a decision record is malformed or missing mandatory fields, note
  it as [INCOMPLETE RECORD] and include what is available.
- If the PM asks to update or supersede a decision after a check or
  review, tell them to use the decision-log skill for that action.

---

## Output quality check before responding

Verify:
- All decision records in both locations were scanned
- Conflicts are genuine contradictions, not superficial topic matches
- Dependencies and constraints are classified separately from conflicts
- No decision content was fabricated or paraphrased inaccurately
- Read-only rule was not violated
- If no records found, the PM was told to use decision-log to start