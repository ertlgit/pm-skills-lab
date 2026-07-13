# comprehend-first

An agent skill that makes your coding agent understand a document before acting on it. It translates what each part of a brief, spec, or RFP is actually asking, surfaces the traps a shallow reading hits, and stops for your confirmation before any work begins. Works with Claude Code, Cursor, Codex CLI, and other agents that support the skills format.

> This skill ends at understanding. It does not prioritise, decide what to build, or
> produce the deliverable. Acting on the document is a separate step that starts only
> after you confirm the reading.

![comprehend-first reads an exec brief, translates its real intent, and stops at a checkpoint before any work begins](../assets/demo.gif)

*The skill on an exec brief: the real ask vs. the literal ask, the traps a
shallow reading would hit, and a checkpoint — no work begins until you
confirm the reading.*

---

## Why this exists

You hand your agent a brief, a spec, or an RFP and ask it to work from it. It reads the surface, acts on the literal wording, and produces something that satisfies the words while missing what the document was actually asking for. "Justification must reference the three criteria" becomes "name the three criteria." The gap is invisible until someone who knows the brief pushes on it.

This skill forces a different first move. Before any work, the agent treats the document as the only authority, translates what each part is actually asking, surfaces where a shallow reading would fail, and stops for you to confirm it understood the document before building anything on top of it. Caught at the reading stage, a misreading is cheap to fix. Left uncaught, it compounds, because every later pass polishes the form and never repairs the missing function.

---

## Where it fits in the PM workflow

1. **A document arrives** — a brief, RFP, PRD, case study, or strategy ask
2. **Work is about to begin** on top of it — a plan, an analysis, a deck, a build
3. **This skill reads it first** — atomises it, translates each part's real intent, names the traps, and stops for your confirmation
4. **You confirm or correct the reading** — then the real work begins on a shared, accurate understanding instead of a guess

The skill operates between step 1 and step 2. It is not a summariser, a research tool, or a deliverable generator. It establishes that you and your agent are reading the document the same way before anything depends on it.

---

## How it fits into the agentic PM toolchain

```
brief / spec / RFP / PRD / case study / strategy doc
        ↓  (handed to the agent, or pasted)
coding agent · comprehend-first skill
        ↓
intent-translation dossier   →   you confirm or correct
        ↓
the real work (PRD, plan, analysis, deck, ...) begins
```

The dossier is the checkpoint. Nothing downstream is produced until you confirm it.

---

## How it works

One job, one move. Hand your agent a document and ask it to work from it. On depth-critical or intent-heavy documents the skill activates on its own. You can also invoke it directly:

```
comprehend first: [paste the document, or point the agent at the file]
```

The agent treats the document as the only authority, breaks it into units, and translates each one before doing anything with it. The criteria and structure come from the document in front of you; the skill imposes no fixed rubric or template.

---

## What gets produced

A short intent-translation dossier. For each meaningful unit of the document:

- **Verbatim quote** — copied exactly from the document, never paraphrased
- **Literal reading** — what it says on its face
- **Real intent** — what it is actually asking, at the altitude the document assigns
- **Work that satisfies it** — the analysis or decision that meets the function, not the form
- **Inputs needed** — what the work would require, with unknowns marked honestly
- **The trap** — how a shallow answer satisfies the wording and misses the point
- **Stop condition** — the signal that the unit was read literally and must be reworked

Plus the four layered jobs per section (explicit task, evaluation, altitude, defence), the
document's overall ask stated in one line, and a self-audit that flags what is still unknown
rather than inventing it.

### What to expect on thin or under-specified documents:

The dossier scales to the document: a one or two line directive gets a short reading, not a full table. And when a document does not contain enough to produce what it asks for, comprehend-first names what is missing and stops, rather than filling the gap with invented content. 

Example: Asked to write a letter that "describes your tasks" with no tasks supplied, it returns the real intent and the information the letter needs, not a template with invented ones.

---

## The comprehension gate

Before presenting, the reading is self-checked against nine standing checks and a set of function tests. The point is to catch six failure modes at the reading stage, where they are cheap, rather than on stage in front of whoever judges the work:

- **Bias** — the reading bent toward a preferred answer instead of the document's own terms
- **Shallowness** — labels and one-liners where the document demands analysis
- **Fabrication** — invented specifics passed off as grounded
- **Unexplained labels** — a verdict or stance with no reasoning a reader can reconstruct
- **Logical errors** — a conclusion the document does not support
- **Brief-drift** — deep work that answers a different question than the one asked

When evidence is missing, the skill states the unknown and what would resolve it rather than generating plausible-sounding but unreliable content. This is intentional.

---

## When to use it

Use it when reading the document correctly is the hard part and a misreading would be costly: a brief, an RFP, a PRD or spec, a requirements set, a case study, a board or exec ask, a research paper, a strategy document or simply a longer email from a customer, colleague or stakeholder.

It is deliberately not for quick factual lookups, simple summaries, or trivial extraction ("what does this paragraph say," "pull the dates out of this"). Running the full gate on a trivial read wastes effort. The gate is for work where understanding the document's intent is what matters.

---

## Project integration tip

Reference this skill in your project's instructions file — `CLAUDE.md` (Claude Code), `AGENTS.md` (Codex CLI), or a rule in `.cursor/rules` (Cursor) — so the agent runs the comprehension gate before acting on any document you hand it:

```
## Working from documents
Before producing a PRD, plan, analysis, or deck from any brief, spec, or RFP in this project, first comprehend it: translate each part's real intent, surface the traps a shallow reading would hit, and confirm the reading with me before doing the work.
```

This makes accurate comprehension the default first step of any document-driven task, without you needing to invoke the skill by hand each time.

---

## Installation

### Quick install (recommended)

```bash
npx skills add ertlgit/pm-skills-lab
```

Select the skills you want to install from the interactive prompt. The installer places each skill where your agent expects it — Claude Code, Cursor, Codex CLI, and 20+ other agents are supported. Your agent activates installed skills automatically when it detects the right context in your request.

### Manual install (Claude Code)

This skill loads its method and gate from `references/`, so copy the whole folder, not just `SKILL.md`:

```bash
mkdir -p ~/.claude/skills/comprehend-first
cp -r comprehend-first/SKILL.md comprehend-first/references comprehend-first/examples \
  ~/.claude/skills/comprehend-first/
```

### Verify installation

In Claude Code, open any project folder and run `/skills` — the installed skills appear under available skills. On other agents, the `npx skills add` output lists where each skill was installed.

### Update to latest version

```bash
npx skills add ertlgit/pm-skills-lab
```

Re-running the install command updates all skills to the latest version.

---

## Usage example

Input:

```
comprehend first: our brief says "recommend a CI/CD platform. The recommendation must weigh cost, migration effort, and developer experience, and include rollout milestones."
```

Output:

```
Reading the document as the only authority. 2 meaningful units.

UNIT 1 — "recommendation must weigh cost, migration effort, and developer experience"
Literal: mention the three criteria.
Real intent: this is the scoring rubric stated in the open. Assess every candidate platform against each of the three with real content, then let the recommendation follow from the assessment rather than precede it.
Trap: naming the three criteria and attaching them to a platform already chosen.
Stop condition: the criteria appear as labels, or the order is produced by averaging scores
rather than by the decisive criterion.

UNIT 2 — "include rollout milestones"
Literal: list some milestones.
Real intent: a sequenced rollout whose milestones actually de-risk the migration, each tied to the recommended platform.
Inputs needed: current toolchain and team capacity [?].
Trap: generic milestones disconnected from the specific migration.

OVERALL ASK: choose a CI/CD platform on a defended assessment against three named criteria, and show a rollout that de-risks the switch.

──────────────────────────────────────────────
CHECKPOINT — confirm before any work begins

Real ask: a platform choice that follows from the assessment, not a
choice with three criteria attached to it afterward.

- Says "must weigh cost, migration effort, and developer experience" —
  actually asks for a defended assessment against each, not three name-checks.
- Says "include rollout milestones" — actually asks for a sequence that
  de-risks this specific migration.

1. What platforms are in the candidate set? [not in the brief]
2. What is the current toolchain and team capacity? [not in the brief]

No work begins until you confirm or correct this reading.
```

---

## Skill structure

```
comprehend-first/
├── SKILL.md
├── README.md
├── CHANGELOG.md
├── references/
│   ├── comprehension-method.md
│   └── gate-and-tests-quickref.md
└── examples/
    └── intent-dossier-illustrative.md
```

---

## Where it sits among the pm-skills

comprehend-first is the front door for document-driven work: understand the brief before you act on it. Once you have understood and acted, the decision skills capture and check what results, [decision-log](../decision-log/) records the decisions the work produces, and [decision-query](../decision-query/) checks new work against them.

```
comprehend first: [paste a brief, spec, or RFP]
```
