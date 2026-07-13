# Changelog

All notable changes to `comprehend-first` are recorded here.

## [1.1.0] — 2026-07-14

### Changed
- The dossier now ends with a checkpoint digest instead of a free-form
  closing line: horizontal rule, bold header, the real ask phrased
  against the literal ask, up to three "says X — actually asks Y" trap
  callouts, at most three numbered questions, and the closing gate line,
  with nothing printed after it. Rationale: in a terminal the closing
  screen is all the user sees at rest, and confirming a reading requires
  the reading to be visible — a checkpoint that only asks questions
  invites rubber-stamping.

## [1.0.1] — 2026-07-13

### Changed
- SKILL.md and README reworded agent-agnostically ("the agent" instead
  of "Claude") so the skill reads correctly in Cursor, Codex CLI, and
  other host agents alongside Claude Code. No behavioral change.
- README integration tip generalized from CLAUDE.md-only to all
  supported agents' project instructions files.

## [1.0.0] — 2026-06-19

Initial release.

- First skill: a comprehension-and-confirmation gate for working from a document. Claude
  treats the source document as the only authority, atomises it, translates each unit's real
  intent against its literal wording on a ten-field schema, runs a nine-point comprehension
  gate and the function tests, and stops for the user to confirm the reading before any
  downstream work.
- `SKILL.md` controller with a trigger scoped to depth-critical, intent-heavy document work and
  explicitly de-scoped from quick lookups and summaries.
- `references/comprehension-method.md`: the specification-literalism doctrine, the per-unit
  schema, three domain-neutral worked exemplars (the depth bar), and the four layered jobs.
- `references/gate-and-tests-quickref.md`: the comprehension gate, the function tests, the six
  failure modes, and the `[V]`/`[I]`/`[?]` evidence-tag legend.
- `examples/intent-dossier-illustrative.md`: one worked dossier in a neutral domain, labelled
  illustrative and deliberately unsourced (comprehension identifies what a document asks and what
  inputs the work would need; it makes no sourced factual claims).

### Provenance and scope

Derived and abstracted from an internal comprehension instrument (the comprehension-gate stage of
a larger reasoning framework, v1.1). The instrument's domain-specific content, worked examples, and
coupled pattern names were removed; only the universal machinery, the doctrine, the schema, the
gate, the tests, and the stop-for-confirmation discipline, was kept and generalised so the skill
runs on any document in any field.

This skill ships the comprehension stage **only**, as its own skill, rather than packaging the full
multi-stage framework as a single skill. That is a deliberate deviation from the original build
specification, which assumed one combined skill with the framework files shipped verbatim. The
reasons: the comprehension stage is one coherent, broadly reusable job with a clean trigger, while a
combined four-stage workflow would fire rarely and carry idle machinery; and the published skill must
be domain-neutral and free of the originating case, which a verbatim ship could not satisfy. A separate
downstream skill for the prioritisation-and-production stages may follow if this one earns adoption.
