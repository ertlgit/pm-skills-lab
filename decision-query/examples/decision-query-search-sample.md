# decision-query: Search Mode Example

This example shows the output of `search decisions:` across three
realistic queries. Each query demonstrates a different search dimension:
by topic, by owner, and by status.

---

## Example 1: Search by topic

**Invocation:**

```
search decisions: onboarding
```

**Output:**

```
Found 1 decision matching "onboarding"

DL-2026-06-001 — Use Appcues for user onboarding instead of building
an in-house onboarding flow
Status: accepted | Date: 2026-06-28 | Owner: Head of Product
Matched in: decision-statement, context
```

---

## Example 2: Search by owner

**Invocation:**

```
search decisions: owner Engineering Lead
```

**Output:**

```
Found 2 decisions matching "owner: Engineering Lead"

DL-2026-05-002 — Use Linear for issue tracking instead of Jira
Status: accepted | Date: 2026-05-05 | Owner: Engineering Lead

DL-2026-06-004 — Use Postgres as primary database instead of MongoDB
Status: accepted | Date: 2026-06-29 | Owner: Engineering Lead
```

---

## Example 3: Search by status

**Invocation:**

```
search decisions: status superseded
```

**Output:**

```
Found 1 decision matching "status: superseded"

DL-2026-03-001 — Use Segment as CDP instead of a custom integration
Status: superseded | Date: 2026-03-12 | Owner: Head of Product
Superseded by: DL-2026-06-003
```

---

## Example 4: Search with no matches

**Invocation:**

```
search decisions: pricing model
```

**Output:**

```
No decisions found matching "pricing model".

4 decisions were scanned across DECISIONS.md and /decisions/.
If a pricing decision exists elsewhere, it has not been logged yet.
Use the decision-log skill to capture it.
```

---

## Notes on this example

**Match field reporting:**
When a query matches content in the rationale or context rather than
the decision-statement, the skill notes which field matched. This helps
the PM understand why a record was returned and whether it is genuinely
relevant.

**Owner search format:**
Searching by owner works with or without the "owner:" prefix. Both
`search decisions: Engineering Lead` and `search decisions: owner
Engineering Lead` return the same results.

**Status search:**
Status values are: proposed, accepted, superseded, deprecated. Searching
by status is useful for auditing superseded decisions or finding all
open proposed decisions before a planning cycle.

**No match behavior:**
When no records match, the skill confirms how many records were scanned
and suggests logging the decision if it exists but has not been captured
yet. It does not fabricate results.