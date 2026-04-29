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

### BL-001 — Output format inconsistency: YAML frontmatter vs bold field syntax
**Finding:** Agent mode output uses YAML frontmatter with `---` delimiters.
Manual mode output uses bold field syntax. Template uses bold field syntax.
All three should be consistent.
**Decision needed:** Pick one format and enforce it in SKILL.md.
**Recommendation:** Bold field syntax. Matches the template, more readable
for non-technical PMs, no YAML parsing required.

### BL-002 — Source block position inconsistent
**Finding:** Source block landed after follow-up actions instead of after
rationale as specified in the template.
**Fix:** Strengthen the output order instruction in SKILL.md. Specify the
exact section sequence explicitly.

### BL-019 — Context field fabrication in agent and manual modes
**Finding:** Skill invented context content not present in source
material without marking it [NEEDS REVIEW]. No-fabrication rule
in SKILL.md covers rationale and options but not context.
**Action:** Add explicit no-fabrication rule for context field.
Mark [NEEDS REVIEW - context inferred] when context is thin.

---

## P2 — Decide before publishing

### BL-004 — decisions.md index table — keep or suppress
**Finding:** Skill generated a decisions.md index table linking to
individual decision files. This was not specified in SKILL.md but is
potentially useful.
**Decision needed:** Keep it as designed behavior or suppress it.
**Options:**
- Keep: add explicit instruction to SKILL.md to maintain a decisions.md
  index, update template with index format
- Suppress: add explicit instruction to never create or modify a
  decisions.md file

---

## P3 — Nice to have for v1.1

### BL-007 — Supersession behavior not yet tested
**Finding:** No test has been run on a superseded decision.
**Action:** Run supersession test before publishing or document as
known untested behavior in README.

### BL-008 — Multi-decision extraction not yet tested
**Finding:** No test has been run on a source containing multiple
decisions to confirm sequential NNN file creation.
**Action:** Test or document as known untested.

### BL-018 — Workflow section not yet added to README
**Finding:** PMs working across multiple projects face friction from the
`cd` into project folder requirement. No workflow guidance exists in the
README to help PMs set up a repeatable decision logging routine.
**Action:** Add a Workflows section to decision-log/README.md covering
three patterns: project-anchored, centralized decisions folder, and
shell alias shortcut. Draft agreed, not yet committed.
**Status:** open

---

## Decisions made during testing

<!-- v1.0.0 — 2026-04-28 -->
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