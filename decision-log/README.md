# decision-log

A Claude Code skill that turns product decisions into structured, searchable
markdown records committed to git.

> This skill is used when a team discussion reaches a decision and that
> decision needs to be preserved in a durable, searchable format before it
> is turned into tickets, specs, roadmap changes, or governance artifacts.

---

## Why this exists

Product decisions get made in Slack threads, meetings, and working sessions.
The rationale disappears. Six months later the team re-litigates the same
trade-off, or ships something that contradicts an earlier commitment nobody
remembered.

This skill captures the decision, the options that were rejected, and the
reasoning, in a format that lives in git alongside the code and specs it
informs.

---

## Where it fits in the PM workflow

1. **Discussion** happens in Slack, a meeting, or a working doc
2. **A decision is reached** between named alternatives
3. **This skill preserves it** as a structured markdown record in `/decisions/`
4. **The record is linked** from Jira or Linear tickets, PRDs, roadmap
   entries, or governance artifacts

The skill operates between step 2 and step 4. It is not a meeting summary
tool, a brainstorming aid, or a PRD generator. It captures the moment a
choice was made and why.

---

## How it fits into the agentic PM toolchain

```
Slack / docs / meeting notes / transcripts
        ↓  (via MCP-connected tools or direct paste)
Claude Code · decision-log skill
        ↓
/decisions/DL-YYYY-MM-NNN-slug.md  (committed to git)
        ↓  (linked manually)
Jira · Linear · Notion · PRDs · roadmap tools · governance docs
```

For teams using Claude Code with MCP, source material is passed to the
skill as context for extraction. MCP handles context ingestion only. The
git-committed markdown file is the system of record, not the MCP layer.

---

## Two modes

**Manual** — PM provides the decision details directly. Claude structures
the output and writes the file.

**Agent** — PM pastes unstructured input (Slack thread, meeting notes, PRD
draft). Claude extracts the decision, populates all fields it can confirm,
marks uncertain fields `[NEEDS REVIEW]`, and writes the file.

When source material is thin, the skill marks uncertain fields
`[NEEDS REVIEW]` rather than generating plausible-sounding but
unreliable content. This is intentional.

---

## Output modes

**DECISIONS.md (default)** — appends each decision as a new section to
a single `DECISIONS.md` file in the project root. Simpler to scan,
easier to share, and works as an automatic context file when referenced
in `CLAUDE.md`.

**Individual files** — creates one `DL-YYYY-MM-NNN-slug.md` file per
decision in a `/decisions/` subfolder. Better for teams using git who
want per-decision diff history and stable URLs for linking from PRDs
or tickets.

Default invocation uses DECISIONS.md:

```
log decision: [input]
log decision from slack: [input]
```

Invoke individual file mode explicitly:

```
log decision (new file): [input]
```

---

## Claude Code integration tip

Reference `DECISIONS.md` in your project's `CLAUDE.md` to load all
decisions as context at the start of every Claude Code session:

```
## Decision log
All product decisions for this project are in DECISIONS.md.
Before generating any PRD content, roadmap suggestion, or technical
recommendation, read DECISIONS.md and flag any conflicts with existing
decisions.
```

This turns your decision log into an active constraint layer. Claude
Code will automatically surface conflicts between new work and prior
decisions without you needing to invoke decision-query manually.

---

## Recommended invocation

For consistent activation, use one of these phrases when calling the skill:

**Manual mode:**

```
log decision: [your decision details here]
```

**Agent mode:**

```
log decision from [source]: [paste your input here]
```

Examples:

```
log decision: we chose Stripe over Paddle for payments, main reason was
developer documentation quality, owner is CTO
```

```
log decision from slack: [paste thread]
```

```
log decision from meeting notes: [paste notes]
```

Using a consistent phrase helps Claude activate the skill reliably and
signals clearly to teammates what invocation pattern to follow.

---

## What gets logged

Eight mandatory fields per record: decision-id, decision-statement, status,
context, options-considered, chosen-option, rationale, and owner.

An optional extension block covers follow-up actions, assumptions, risks,
linked artifacts, regulatory flags, and AI decision mode. Uncomment what
your team needs.

---

## Significance gate

Not every decision warrants a log entry. The skill checks whether the
decision is hard to reverse, cross-functional, involves a real trade-off,
or will likely be revisited. For borderline cases it asks before generating.
This keeps `/decisions/` signal-rich rather than a dump of every minor call.

---

## What to do with your decisions folder

Over time your `/decisions/` folder becomes a searchable record of why
your product is the way it is. Here is how PM teams use it in practice.

**Before a planning meeting**
Pull up decisions related to the topic on the agenda. Paste relevant
records into the meeting doc as constraints. Stop re-litigating settled
ground before the meeting starts.

**When writing a PRD or spec**
Reference relevant decision records as the rationale for constraints and
scope boundaries. Link from the PRD to the decision file. Future readers
will understand why, not just what.

**When onboarding a new team member**
Point them to the decisions folder before their first sprint. Context
that took months to accumulate transfers in an afternoon.

**When a decision needs to change**
Use the supersession workflow: find the original record, set status to
`superseded`, link the new decision record that replaces it. The history
stays intact.

**When something feels wrong**
Before committing to a direction, scan the decisions folder manually or
paste your proposal into Claude Code and ask: "Does anything in
/decisions/ conflict with this?" That is the fastest way to catch
contradictions before they ship.

**What this folder is not**
It is not a meeting notes archive. It is not a task list. It is not a
PRD. It captures the moment a choice was made between named alternatives
and why. Keep it signal-rich by using the significance gate and only
logging decisions that will matter later.

---

## Installation

### Quick install (recommended)

Install the skill directly from GitHub without cloning the repo:

```bash
mkdir -p ~/.claude/skills/decision-log && \
curl -o ~/.claude/skills/decision-log/SKILL.md \
https://raw.githubusercontent.com/ertlgit/pm-skills-lab/main/decision-log/SKILL.md
```

Claude Code will activate the skill automatically when it detects
decision-bound language in your request.

### Manual install

If you have cloned the repo locally:

```bash
mkdir -p ~/.claude/skills/decision-log
cp decision-log/SKILL.md ~/.claude/skills/decision-log/SKILL.md
```

### Verify installation

Open Claude Code in any project folder and run:

```
/skills
```

You should see `decision-log` listed under available skills.

### Update to latest version

To update the skill after changes are published:

```bash
curl -o ~/.claude/skills/decision-log/SKILL.md \
https://raw.githubusercontent.com/ertlgit/pm-skills-lab/main/decision-log/SKILL.md
```

---

## Usage examples

### Manual mode

```
Log this decision: we chose to use a third-party feature flag service
instead of extending our internal config system. Main reason was build
cost and maintenance overhead. Owner is the Head of Product.
```

### Agent mode — Slack thread extraction

Input:

```
#product-eng, 2026-04-14

Luca: options are: optimize the current batch job, or move to streaming.
      Batch is cheaper to maintain, streaming gives us near-realtime
      which sales keeps asking for.
Maya: three enterprise deals mentioned realtime dashboards last month.
      Let's go with streaming. Luca owns it.
```

Claude extracts the decision, identifies both options, derives rationale
from context, assigns owner, and produces:

`DL-2026-04-002-analytics-pipeline-streaming.md`

Fields with thin source coverage are marked `[NEEDS REVIEW]` rather than
fabricated.

---

## Skill structure

```
decision-log/
├── SKILL.md
├── decision-log.md
└── examples/
    ├── decision-log-sample.md
    └── decision-log-agent-sample.md
```
