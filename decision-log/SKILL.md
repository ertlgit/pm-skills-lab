# Decision Log Skill for Claude Code

## What this skill does

Turns product decisions into structured, searchable markdown records that
teams commit to git. Prevents decision churn by capturing what was decided,
what was rejected, and why, in a format that is retrievable and linkable
across the product org.

Works in two modes:
- Manual: PM provides decision details directly
- Agent: Claude extracts from unstructured input (meeting notes, Slack
  threads, PRD drafts, discussion summaries)

## When to activate this skill

Activate only when the input contains decision-bound language, meaning
explicit signals that a choice was made or must be made between named
alternatives. Required: at least one of the following must be present.

Explicit decision signals:
- "we decided", "we agreed to", "we chose", "we will go with"
- "the decision is", "going forward we", "we are not doing", "we ruled out"
- A direct request: "log this decision", "capture what we decided",
  "create a decision record", "preserve the rationale"
- A named trade-off request: "help me decide between X and Y and record it"

Do not activate for:
- Meeting summaries that contain no explicit decision statement
- Action item lists without a named choice between alternatives
- Preference discussions, brainstorming, or open exploration
- PRDs, specs, roadmap documents, retros, or postmortems
- Notes that describe a topic but not a resolution

If the input contains discussion that implies a decision but does not
state one explicitly, ask the user to confirm the decision statement
before generating a record.

## Significance gate

Before generating a record, check whether the decision meets at least
one of these criteria:
- Hard to reverse without meaningful cost or delay
- Cross-functional (affects more than one team or system)
- Involves a real trade-off between named alternatives
- Will likely be revisited or questioned later
- Has compliance, regulatory, or security implications

If none apply, ask the user: "This decision may not warrant a formal log
entry. Do you want to create one anyway?" Generate the record only after
explicit confirmation. Never generate silently for low-significance
decisions.

## Output format

Always produce a markdown file using the decision log template.
File naming convention: DL-YYYY-MM-NNN-short-slug.md
Example: DL-2026-04-001-build-vs-buy-auth.md

Place output in /decisions/ if the folder exists, otherwise in the
current working directory.

## Mandatory fields (populate all eight)

`decision-id`
Generate from date and a short slug derived from the decision statement.
Format: DL-YYYY-MM-NNN.

`decision-statement`
One sentence only. The decision itself, not the background. Start with
a verb. Example: "Use Auth0 for authentication instead of building
in-house."

`status`
One of: proposed / accepted / superseded / deprecated.
Default to accepted if the source clearly describes a past decision.
Use proposed if the decision is still open. Do not infer superseded or
deprecated unless the source explicitly states it.
When status is superseded, the superseded-by field becomes mandatory.

`context`
Two to five sentences. What forced this decision. The constraint, event,
or problem that made standing still not an option.

`options-considered`
A list with at least two entries. Each entry gets a short label and one
sentence description. If source material only surfaces one option, add
"Alternative not captured in source" as the second entry and mark
options-considered [NEEDS REVIEW].

`chosen-option`
The selected option by label. Informal or free-form labels from source
material are acceptable. One line.

`rationale`
Why the chosen option won over the others. Most important field. If
source material does not contain clear reasoning, populate what can be
inferred and mark the field [NEEDS REVIEW - rationale inferred from
context]. Never fabricate rationale to fill the field.

`owner`
The person accountable for this decision. Not the full stakeholder list.
If not stated in source material, mark [NEEDS REVIEW - owner not
identified].

## Agent mode additional rules

When extracting from unstructured input, add a source block after the
mandatory fields:

`source-type`: meeting-notes / slack-thread / prd-draft / email / other
`source-date`: date of the source document if identifiable
`source-reference`: link or filename if available
`extraction-mode`: agent

Decision signals to scan for: "we decided", "we will go with",
"the decision is", "we agreed to", "we are not doing", "we ruled out",
"going forward we", "we chose", "we rejected".

When multiple decisions appear in one source, produce one file per
decision with sequential NNN values.

## Supersession rule

When status is superseded, add:
`superseded-by`: link or ID of the record that replaces this one
`superseded-date`: date of supersession
`supersession-reason`: one sentence

## Handling ambiguity

- Populate what is explicit in source material first
- Infer only when the inference is unambiguous
- Mark uncertain fields [NEEDS REVIEW - reason]
- Never fabricate options or rationale
- If decision-statement cannot be derived with confidence, stop and ask
  the user to clarify before generating the record

## Optional extension block

The template contains a commented optional section. Fields listed in
order of downstream value for PM teams:

1. follow-up-actions — highest value: captures what must happen as a
   result of this decision, with owner and due date per action
2. assumptions — what must remain true for this decision to hold
3. risks — known risks at decision time with optional mitigation
4. linked-artifacts — links to PRD, ticket, ADR, Slack thread
5. review-date — when this decision should be revisited
6. stakeholders-informed — who was notified beyond the owner
7. regulatory-flag — boolean, marks compliance-relevant decisions
8. ai-decision-mode — human / ai-assisted / ai-recommended
9. ai-input-summary — one sentence on what AI contributed

Do not populate these unless the user requests them or source material
contains clear content for them.

## Output quality check before writing the file

Verify:
- decision-statement is one sentence and starts with a verb
- options-considered has at least two entries
- rationale is present and not a restatement of decision-statement
- status is one of the four allowed values
- owner is identified or marked [NEEDS REVIEW]
- all ambiguous fields are marked [NEEDS REVIEW], not left blank
  or fabricated
- significance gate was applied and confirmed before generating