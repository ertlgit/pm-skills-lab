---
name: comprehend-first
description: "Use this skill whenever the user hands the agent a document (brief, spec, PRD, RFP, requirements, case study, board ask, strategy doc) and asks the agent to act on it. Translates what each part actually asks (its intent, not its literal wording), names the traps a shallow reading hits, and stops for the user to confirm understanding before work begins. For depth-critical or intent-heavy documents, not quick lookups or summaries. Invocation: 'comprehend first:', 'comprehend this brief:'."
license: "MIT — see LICENSE in pm-skills-lab repo"
---

# comprehend-first skill

## What this skill does

Makes the agent understand a document before acting on it. The agent atomises a brief, spec, RFP, or similar, translates what each part is actually asking (its intent, not its literal wording), surfaces the traps a shallow reading hits, runs a self-check, produces an intent-translation dossier, and stops for the user to confirm or correct the reading before any work begins.

It defeats one failure: **specification literalism, satisfying the visible form of a requirement while missing its function.** "Justification must reference the three criteria" becomes "name the three criteria"; "propose three initiatives" becomes "list three." Caught at the reading stage this is cheap to fix. Left uncaught it compounds, because every later pass polishes the form and never repairs the missing function.

This is a single-job skill. It ends at understanding. Prioritising, deciding what to build, and producing the deliverable are separate steps that begin only after the user confirms the reading.

---

## When to activate this skill

Activate when the user hands the agent a document and expects work built on it, and reading it correctly is the hard part.

Document-and-act signals (a document is present, plus a request to act on it):
- "work from this brief / spec / RFP / PRD / requirements / case study"
- "here is the brief, help me respond / plan / prioritise / build / prepare"
- "before you start, understand this document"
- "what is this brief actually asking"

Explicit invocation patterns:
- "comprehend first: [document]"
- "comprehend this brief: [document]"
- "comprehend this document: [document]"

Also activate, without an explicit phrase, when a substantial document will be the basis for a deliverable, when it carries intent beyond its literal wording, or when it will be judged by demanding readers.

Do not activate for:
- Quick factual lookups or single-fact questions
- Simple summaries, or "what does this paragraph say"
- Trivial extraction (pull the dates, names, or numbers out of a document)
- General questions not grounded in a document
- A document the user only wants quoted or excerpted, not acted upon

When it is unclear whether a document is depth-critical, run the comprehension pass if substantial work will be built on it, and skip it for clearly trivial reads.

---

## What the skill takes as authority

The document in front of the agent is the only authority. Nothing from prior work, the agent's assumptions, or a preferred answer is inherited as settled. Verified facts may re-enter later as marked evidence; no prior conclusion enters as truth.

The skill is brief-agnostic. Read whatever criteria the document states or implies, and let its own structure shape the dossier. Do not impose a fixed rubric, a fixed number of sections, or a template borrowed from another document. The schema and the gate are universal; the criteria, the structure, and the content come from the document at hand.

---

## Operating procedure

1. **Take the document as the only authority** and read it on its own terms before mapping it to any answer you already have in mind.
2. **Atomise it into units.** A unit is any clause, mandate, deliverable, evaluation signal, or constraint that carries obligation or intent, including between-the-lines signals (an emphasised word, a named audience, a phrase like "strategy *and* plan," a quiet standard).
3. **Translate each unit on the schema** in Output format below. High-risk units (the ones that decide the grade, or that a shallow reading would gut) get full depth. Load `references/comprehension-method.md` for the doctrine and the worked exemplars that set the depth bar, and read `examples/intent-dossier-illustrative.md` for the output shape.
4. **State the four layered jobs for each major section** (explicit task, evaluation, altitude, defence). See the method file.
5. **State the document's overall ask** in one or two sentences the user could repeat back.
6. **Run the comprehension gate** in `references/gate-and-tests-quickref.md` and apply the function tests. Any fail is reworked, not waved through. Flag every gap honestly.
7. **Present the dossier and stop.** Do not begin solving. Wait for the user to confirm or correct the reading.

---

## Output format

The output is an intent-translation dossier. Produce its sections in this order:

1. **Method** — one short paragraph on how the document is being read (rubric, not to-do list; develop-then-explain where a clause could collapse into a list; any scope boundary held).
2. **Per-unit translation** — one row per meaningful unit, on the ten-field schema below.
3. **Layered jobs** — the four jobs per major section.
4. **Overall ask** — the whole document's ask in one or two sentences.
5. **Self-audit** — the comprehension gate run on the dossier, with gaps flagged honestly.
6. **Stop for confirmation** — a closing line that presents the dossier as a checkpoint and asks the user to confirm or correct before any work proceeds.

Per-unit schema, all ten fields:

1. **Verbatim quote** — copied word for word from the document, or `[NOT IN SOURCE]`. Never paraphrase here. A row whose quote field is not a true quote is rejected.
2. **Literal reading** — what it says on its face. Where a literal reading would collapse a real deliverable into a list, state the true floor.
3. **Real intent** — what it is actually asking, at the altitude the document assigns.
4. **Work that satisfies it** — the analysis or decision that meets the function, concretely.
5. **Inputs / evidence needed** — what the work requires, with unknowns marked `[?]` and load-bearing claims marked for verification, not asserted.
6. **Output required, and where it appears** — the artefact or statement this produces, and where it must be visible, not buried in notes.
7. **Shallow-answer trap** — how this unit gets satisfied hollowly. Name the trap.
8. **Strong reading** — what doing the actual work produces.
9. **Likely evaluator concern** — who will press this unit and on what.
10. **Stop condition if shallow** — the signal the unit was read literally and must be reworked.

Match the dossier to the document. Scale length and depth to the document's size and the cost of misreading it. Do not expand a one or two sentence directive into a full per-unit table; cover a short document in a compact reading that still names the real intent, the critical gaps, and the central trap. Reserve the full ten-field treatment for units where a shallow reading would genuinely gut the result; for a low-risk unit a single line giving its real intent, and the trap if it has one, is enough. A short document gets a short dossier. 
When one gap is the blocker, the document cannot produce what it asks for without it, name it as the blocker, not as one unknown among several. Compactness applies to length, not to the risk hierarchy: the dominant gap stays foregrounded even in a short dossier.

---

## The comprehension gate

Before presenting, self-check the dossier against the comprehension gate and the function tests in `references/gate-and-tests-quickref.md`. The nine gate checks are: function over form, unknown over invention, depth over labels, completeness with no silent omissions, connected reading, on-its-own-terms (de-bias), evidence honesty, scope fidelity, and stop for confirmation. Any fail triggers rework, not progression.

The point is to catch six failure modes at the reading stage: bias, shallowness, fabrication, unexplained labels, logical errors, and brief-drift (answering a different question than the one asked).

When evidence is missing, state the unknown and what would resolve it rather than generating plausible-sounding but unreliable content. An admitted unknown beats invented specificity. This is intentional.

---

## Voice and stance

Answer at the altitude of the role the document assigns, as the operator in that seat, not as an analyst narrating options. Stay inside the scope the document sets, and flag, rather than cross, any boundary it draws. Where the task includes diagnosing a situation or a market, keep that diagnosis neutral and evidence-led; do not let it bend toward a conclusion preferred going in.

---

## Reference files

- `references/comprehension-method.md` — load when translating units. The specification-literalism doctrine, the full per-unit schema, the worked exemplars that set the depth bar, and the four layered jobs.
- `references/gate-and-tests-quickref.md` — load to self-check before presenting. The nine gate checks, the function tests, the six failure modes, and the `[V]`/`[I]`/`[?]` evidence legend on one screen.
- `examples/intent-dossier-illustrative.md` — read for the output shape. One worked dossier in a neutral domain, deliberately unsourced.

---

## Output quality check before presenting

Verify:
- Every meaningful unit of the document has a translation row; nothing high-signal is silently skipped, and anything left out is a stated choice
- The verbatim-quote field is a true quote or `[NOT IN SOURCE]`, never paraphrased
- High-risk units meet the exemplar depth, not just the schema format
- Each unit's real intent is the function, not a restatement of the literal wording
- Inputs and evidence fields mark unknowns `[?]`; nothing is fabricated to fill a field
- The four layered jobs are stated for each major section
- The document's overall ask is stated in one or two sentences
- The comprehension gate and the function tests were applied, and any fail was reworked
- The dossier stops for the user; no downstream work was produced

---

## Where this stops

This skill ends at "document understood and confirmed." It does not prioritise, decide what to build, design the artefact, or produce the deliverable. Those are separate steps. Its only job is to make sure the agent and the user share an accurate reading of the document before the real work begins.
