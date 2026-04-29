## [1.0.0] — 2026-04-29

### Added
- `decision-log` skill: turns product decisions into structured, searchable
  markdown records committed to git
- Manual and agent extraction modes with automatic mode detection
- Eight mandatory fields: decision-id, decision-statement, status, context,
  options-considered, chosen-option, rationale, owner
- Significance gate scoped to agent mode: prevents low-value entries from
  filling the decisions folder without blocking deliberate manual logging
- Agent mode with honest `[NEEDS REVIEW]` flagging on uncertain fields
- Source traceability block for agent-extracted records
- Supersession rule for decisions that are replaced over time
- Optional extension block with nine fields ordered by downstream PM value
- Two worked examples: manual mode and agent mode Slack extraction
- Quick install via curl, no repo clone required
- `decision-query` skill stub: planned companion skill for checking PRDs,
  searching records, and reviewing decisions due for revisit
- Roadmap section documenting planned skills
- MIT license

### Fixed
- Output format normalized to bold field syntax throughout, YAML
  frontmatter suppressed from output
- Section sequence enforced explicitly in correct order
- Owner `[NEEDS REVIEW]` flag mandatory when ownership is implied
  but not explicitly confirmed
- Context no-fabrication rule added, thin context marked `[NEEDS REVIEW]`
- File creation never appends to or overwrites existing files
- decisions.md index table suppressed, individual files only
- Installation path corrected to subfolder structure required by
  Claude Code