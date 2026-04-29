<!-- CHANGELOG NOTE
When preparing a release, check all items marked (done) in the
"Decisions made during testing" section below. Any item that changed
user-visible behavior (output format, field rules, activation logic,
file naming, installation) belongs in the CHANGELOG as a Fixed or
Added entry. Documentation-only changes (README edits, invocation
examples, workflow guidance) do not need a CHANGELOG entry.
Last release: v1.0.0 — 2026-04-28
Update "Last release" line each time a new version is tagged and pushed.
-->

# decision-log backlog

Findings from v1 testing (2026-04-28). Items ordered by priority.

---

## P1 — Fix before publishing

No open items.

---

## P2 — Decide before publishing

No open items.

---

## P3 — Nice to have for v1.1

### BL-018 — Workflow section not yet added to README
**Finding:** PMs working across multiple projects face friction from the
`cd` into project folder requirement. No workflow guidance exists in the
README to help PMs set up a repeatable decision logging routine.
**Action:** Add a Workflows section to decision-log/README.md covering
three patterns: project-anchored, centralized decisions folder, and
shell alias shortcut. Draft agreed, not yet committed.
**Status:** open

### BL-021 — Workflow section missing: global decisions folder setup
**Finding:** No guidance on setting up a global decisions folder with
a shell alias to remove cd friction from daily use.
**Action:** Add to README workflow section. Draft agreed in session.
**Priority:** P3

### BL-022 — CLAUDE.md project integration not documented
**Finding:** PMs working in Claude Code projects can use CLAUDE.md to
set a default decisions folder path, removing cd friction entirely.
**Action:** Document in README as power user tip.
**Priority:** P3

### BL-023 — New skill: decision-check
**Finding:** No way to validate a PRD, email, or proposal against
existing decision records. High-value use case for daily PM work.
**Action:** Scope and build decision-check as the second skill in
pm-skills-lab after v1.0 ships.
**Priority:** P3 — v1.1 roadmap item

### BL-026 — Skill positioned as workflow tool but is discovery only
**Finding:** README framing partially implies delivery integration.
Honest positioning is discovery and alignment layer only. Delivery
integration requires Jira/Linear connection which does not exist in v1.
**Action:** Review README for delivery-implying language and adjust
to reflect discovery positioning accurately.
**Priority:** P3 — refinement, not a blocker.

---

## Decisions made during testing

<!-- v1.0.0 — 2026-04-28 -->

- BL-024 — README missing: what to do with your decisions folder (done)
- BL-001 — Output format inconsistency: YAML frontmatter vs bold field syntax (done)
- BL-002 — Source block position inconsistent (done)
- BL-020 — Owner [NEEDS REVIEW] flag applied inconsistently across runs (done)
- BL-025 — Toolchain diagram implies automated Jira/Linear integration (done)
- BL-004 — decisions.md index table — keep or suppress (done)
- BL-019 — Context field fabrication in agent and manual modes (done)
- BL-006 — Significance gate behavior redesigned (done)
- BL-003 — File creation instruction too weak (done)
- BL-005 — Installation instruction incorrect in README (done)
- BL-009 — YAML frontmatter added to SKILL.md to fix activation (done)
- BL-010 — Section headers normalized to lowercase (done)
- BL-011 — Template optional block headers normalized to lowercase (done)
- BL-012 — [NEEDS REVIEW] wording normalized (done)
- BL-013 — Installation path corrected from flat file to subfolder (done)
- BL-014 — Recommended invocation section added to README (done)
- BL-015 — [NEEDS REVIEW] intent clarified in README (done)
- BL-016 — mode detection section added to SKILL.md (done)
- BL-017 — quick install curl command added to README (done)