# Changelog

All notable changes to pm-skills-lab are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [1.0.0] — 2026-04-28

### Added
- `decision-log` skill: turns product decisions into structured, searchable
  markdown records committed to git
- Supports manual input and agent extraction from unstructured sources
  (Slack threads, meeting notes, PRD drafts)
- Eight mandatory fields: decision-id, decision-statement, status, context,
  options-considered, chosen-option, rationale, owner
- Significance gate: prevents low-value entries from filling the decisions
  folder
- Agent mode with honest `[NEEDS REVIEW]` flagging on uncertain fields
- Source traceability block for agent-extracted records
- Supersession rule for decisions that are replaced over time
- Optional extension block with nine fields ordered by downstream PM value,
  including follow-up-actions, assumptions, risks, and AI decision mode
- Two worked examples: manual mode (feature flag build vs buy) and agent
  mode (analytics pipeline Slack thread extraction)
- MIT license