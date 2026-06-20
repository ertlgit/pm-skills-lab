# pm-skills-lab backlog

Open improvements and known gaps. Items ordered by priority.

---

## P3 — Planned for v1.1

### BL-018 — Workflow guidance missing from README
**Finding:** No guidance exists for PMs on setting up a repeatable
decision logging routine across projects. Common patterns include
a global decisions folder with a shell alias and CLAUDE.md project
integration for automatic folder targeting.
**Action:** Add a Workflows section to decision-log/README.md covering:
project-anchored workflow, centralized decisions folder with shell
alias, and CLAUDE.md integration as a power user tip.

### BL-022 — CLAUDE.md project integration not documented
**Finding:** PMs using Claude Code projects can set a default decisions
folder path in CLAUDE.md, removing the need to cd into a specific
folder before logging decisions.
**Action:** Document in README as a power user tip, either standalone
or as part of the BL-018 workflow section.

### BL-029 — MCP server for structured decision querying
**Finding:** File-based querying works for v1 but limits programmatic
access from other tools. An MCP server would expose decisions as
structured data queryable by Cursor, CI pipelines, and other Claude
instances.
**Action:** Scope after adoption signal shows file-based approach
hitting limits. Validate query patterns from real usage first.
**Priority:** P3 — v2 roadmap item

---

## Decisions made during testing

- BL-030 — comprehend-first skill — SHIPPED v1.0.0 (maps to CHANGELOG 1.0.0) (done)
- BL-028 — decision-query skill shipped: check, search, and review modes (done)
- BL-027 — DECISIONS.md default output mode added, individual files as opt-in (done)
- BL-024 — What to do with your decisions folder section added (done)
- BL-025 — Toolchain diagram annotation added (done)
- BL-001 — Output format normalized to bold field syntax (done)
- BL-002 — Source block position and section sequence fixed (done)
- BL-020 — Owner [NEEDS REVIEW] flag rule strengthened (done)
- BL-004 — decisions.md index table suppressed (done)
- BL-019 — Context no-fabrication rule added (done)
- BL-006 — Significance gate scoped to agent mode only (done)
- BL-003 — File creation rule strengthened (done)
- BL-005 — Installation instruction corrected (done)
- BL-009 — YAML frontmatter added to SKILL.md (done)
- BL-010 — Section headers normalized to lowercase (done)
- BL-011 — Optional block headers normalized (done)
- BL-012 — [NEEDS REVIEW] wording normalized (done)
- BL-013 — Installation path corrected (done)
- BL-014 — Recommended invocation section added (done)
- BL-015 — [NEEDS REVIEW] intent clarified in README (done)
- BL-016 — Mode detection section added to SKILL.md (done)
- BL-017 — Quick install curl command added (done)