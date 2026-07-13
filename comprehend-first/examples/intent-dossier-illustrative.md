# Illustrative intent-translation dossier

**This is an illustrative example, not a real, sourced case.** It shows the shape and depth a comprehension dossier reaches when this skill is run on a document. The domain (a B2B product brief) is fictional and generic on purpose. Because comprehension identifies what a document is asking and what inputs the work would need, it makes no sourced factual claims, that is why this example carries no citations and is safe to read as a pattern, not a source of facts.

The source brief is reproduced first so the example is self-contained.

---

## The source brief (fictional)

> **Internal brief — Improve first-week activation for our B2B analytics product.**
>
> Background: New workspaces reach the "first dashboard shared" milestone at a low rate within seven days. Activation is defined as a workspace sharing its first dashboard within seven days of signup. We serve mid-market data teams. Onboarding today is a generic product tour.
>
> Your task:
> - Propose a minimum of three initiatives to improve seven-day activation. Initiatives may be
>   product changes or non-product changes (content, lifecycle messaging, onboarding services).
> - Prioritise them. Your prioritisation must reference expected impact, implementation effort, and fit with our self-serve model.
> - For your top two initiatives, describe how success will be measured, with specific metrics.
> - Present a 30-day plan for the first initiative.
>
> Note: pricing and packaging changes are out of scope; assume the current plan structure.

---

## Part 0 — How I am reading this brief (method)

Before translating units, I state the method I am holding to, because the brief tests whether I reconstruct the full task or just satisfy clauses.

1. I read "your prioritisation must reference [three criteria]" as a scoring rubric stated in the open. "Reference" means "assess against," not "name."
2. I read "propose a minimum of three initiatives" as develop-then-explain, not "list three."
3. I read the precise definition of activation (first dashboard shared within seven days) as a hard constraint on every initiative and every metric: anything that moves a different number is off-target.
4. I treat "fit with our self-serve model" as a real criterion and a quiet constraint, not decoration, an onboarding-services initiative has to be read against it honestly.
5. I respect the scope boundary: pricing and packaging are out of scope, and I will flag any reading that drifts there.

---

## Part 1 — Per-unit intent translation

Schema: (1) verbatim quote (2) literal reading (3) real intent (4) work that satisfies it (5) inputs/evidence needed (6) output and where it appears (7) shallow trap (8) strong reading (9) likely evaluator concern (10) stop condition. High-risk units are at full depth; mechanical units are concise.

### Unit 1 — The activation definition (governs everything)

1. **Quote:** "Activation is defined as a workspace sharing its first dashboard within seven days of signup."
2. **Literal:** a definition to acknowledge.
3. **Real intent:** this is the single target every initiative and metric must move. It fixes the actor (the workspace, not the individual), the event (first dashboard *shared*, not created), and the window (seven days).
4. **Work:** hold every later initiative and metric against this exact event and window; reject anything that improves a near-neighbour (logins, dashboards created, day-30 retention) without moving seven-day shared-dashboard rate.
5. **Inputs:** current seven-day activation rate and its distribution by segment `[?]`; where in the funnel workspaces stall before first share `[?]`.
6. **Output:** a stated target metric that anchors the whole answer.
7. **Trap:** treating "activation" loosely and proposing initiatives that lift engagement in general.
8. **Strong:** every initiative traces explicitly to "more workspaces share a first dashboard within seven days."
9. **Evaluator concern:** does this person optimise the defined metric or a vanity proxy?
10. **Stop if:** an initiative or metric targets an event other than the defined one.

### Unit 2 — Propose at least three initiatives (develop-then-explain)

1. **Quote:** "Propose a minimum of three initiatives to improve seven-day activation. Initiatives may be product changes or non-product changes..."
2. **Literal (corrected):** not "list three." The literal floor per initiative is: what it is (concrete, not a label), how it moves seven-day activation, what "done" looks like, whether it is a product or non-product move and why, and its read against the brief's three criteria.
3. **Real intent:** the "product or non-product" line tests whether I see that activation is not only a product problem; content, lifecycle messaging, and onboarding services can move it too.
4. **Work:** construct each initiative from evidence about where workspaces actually stall, not from generic onboarding talking points; explain each on its own terms.
5. **Inputs:** the funnel-stall analysis from Unit 1 `[?]`; what mid-market data teams need in place before a first dashboard is shareable (data connected, a teammate invited) `[?]`.
6. **Output:** a developed set of at least three initiatives, each explained.
7. **Trap:** three named initiatives with no what, no definition of done, no product/non-product reasoning.
8. **Strong:** a coherent set mixing product and non-product moves, each built from the stall evidence and ready to prioritise.
9. **Evaluator concern:** are these grounded in our actual funnel, or stock onboarding ideas?
10. **Stop if:** any initiative is a label with no developed body.

### Unit 3 — Prioritisation referencing three criteria (central graded unit)

1. **Quote:** "Prioritise them. Your prioritisation must reference expected impact, implementation effort, and fit with our self-serve model."
2. **Literal:** the prioritisation must mention the three criteria.
3. **Real intent:** "must reference" is the rubric stated openly. Assess every initiative against each of the three with real content, then let the order follow.
   - *Expected impact:* how much seven-day activation could move, and by what mechanism, bounded rather than asserted.
   - *Implementation effort:* what it actually takes to ship, given the current product and team.
   - *Self-serve fit:* does it strengthen a model where users succeed without hand-holding, or does it lean on services that do not scale? This criterion can demote an otherwise high-impact, services-heavy initiative.
4. **Work:** assess each initiative on all three, state which criterion is decisive and why, defend each close call, and say what evidence would change the order. The order is decided by the decisive criterion, never by averaging the three.
5. **Inputs:** impact mechanism per initiative `[?]`; rough effort sizing `[?]`; an honest read of each initiative against self-serve.
6. **Output:** a defended ranking with the trade-offs visible, not three labels.
7. **Trap:** "I ranked these on impact, effort, and self-serve fit," with the order asserted and the criteria attached afterward.
8. **Strong:** a ranking the analysis produces, where "why this above that" has an answer.
9. **Evaluator concern:** is the order reasoned, or decorated with the criteria after the fact?
10. **Stop if:** the criteria appear as labels, or the order is produced by averaging scores.

### Unit 4 — How success will be measured, top two (measurement, not vanity)

1. **Quote:** "For your top two initiatives, describe how success will be measured, with specific metrics."
2. **Literal:** write success language and some metrics for the top two.
3. **Real intent:** for each of the top two, a qualitative picture of what good looks like, plus specific metrics each with a unit and a direction, tied to the activation definition, honest about attribution.
4. **Work:** define metrics that move the defined event, with a unit and direction, and label each by when its value lands; avoid readiness phrases and vanity numbers.
5. **Inputs:** baseline activation rate to measure against `[?]`; instrumentation for the seven-day shared-dashboard event `[?]`.
6. **Output:** qualitative criteria plus specific metrics, for the top two only.
7. **Trap:** "activation improves," "users engaged," or metrics with no unit, direction, or baseline.
8. **Strong:** countable metrics at the brief's altitude, each tied to seven-day activation.
9. **Evaluator concern:** can this person tell a real metric from a readiness signal?
10. **Stop if:** a metric has no unit and direction, or measures an event other than the defined one.

### Unit 5 — 30-day plan for the first initiative (mechanical, concise)

1. **Quote:** "Present a 30-day plan for the first initiative."
2. **Literal:** a plan covering 30 days.
3. **Real intent:** a sequenced plan whose steps actually begin delivering the top initiative, each step tied to it, not generic onboarding tasks.
4. **Work:** sequence concrete first steps to a first measurable signal within 30 days.
5. **Inputs:** what can realistically ship in 30 days given the team `[?]`.
6. **Output:** a 30-day plan, every step tied to the first initiative.
7. **Trap:** a generic month of "research and align" disconnected from the initiative.
8. **Strong:** steps that start moving the defined metric and produce an early reading.
9. **Evaluator concern:** does this begin delivering, or just describe activity?
10. **Stop if:** any milestone does not advance the first initiative.

### Unit 6 — Scope boundary (between-the-lines, enforced)

1. **Quote:** "pricing and packaging changes are out of scope; assume the current plan structure."
2. **Literal:** do not propose pricing changes.
3. **Real intent:** stay inside the activation mandate; do not solve the problem by changing commercial terms, even if pricing looks like a lever.
4. **Work:** keep every initiative within product, content, lifecycle, and onboarding; flag any drift toward pricing.
5. **Inputs:** none beyond the boundary itself.
6. **Output:** an answer that respects the boundary.
7. **Trap:** slipping a "introduce a free tier" or "discount onboarding" idea into the set.
8. **Strong:** the boundary is honoured and named where relevant.
9. **Evaluator concern:** does this person stay in the lane they were given?
10. **Stop if:** any initiative depends on a pricing or packaging change.

---

## Part 2 — The four layered jobs

- **Explicit task job:** at least three developed initiatives, a prioritisation against three criteria, success metrics for the top two, and a 30-day plan for the first.
- **Evaluation job:** can this person turn a fuzzy activation problem into a grounded, prioritised, measurable plan that respects how the product is actually sold and used.
- **Altitude job:** answer as the person who owns activation, making the prioritisation call with trade-offs, not listing options for someone else to choose.
- **Defence job:** survives a product lens (are these grounded in the funnel), a delivery lens (is the effort honest), and a go-to-market lens (does this fit self-serve). Honest unknowns about the current funnel are better than invented numbers.

---

## Part 3 — The document's overall ask, in one line

Turn a precisely-defined activation problem into a small set of developed, prioritised, and measurable initiatives that move seven-day shared-dashboard rate without leaving the self-serve model or touching pricing, and show how the first one starts in 30 days.

---

## Part 4 — Self-audit against the comprehension gate (gaps flagged)

- **Function over form:** pass. The three-criteria unit and the measurement unit are translated to the work, not the labels.
- **Unknown over invention:** pass. Every evidence-dependent field is marked `[?]`; no funnel numbers are invented.
- **Depth over labels:** pass on the high-risk units (2, 3, 4).
- **Completeness:** pass. All six meaningful units have rows, including the between-the-lines scope boundary.
- **Connected reading:** pass. Each unit traces to the activation definition and the overall ask.
- **On its own terms:** pass. The brief is read before any preferred solution is mapped onto it.
- **Evidence honesty:** pass. The load-bearing facts (current rate, stall point) are flagged for verification, not assumed.
- **Scope fidelity:** pass, and actively enforced in Unit 6.
- **Stop for confirmation:** this dossier ends at the checkpoint below.

**Gaps I am flagging:** the whole reading rests on two unknowns I cannot resolve from the brief alone, the current seven-day activation rate and its segment distribution, and where workspaces
actually stall before a first share. Both are `[?]`. Until they are supplied, any initiative is a hypothesis about a stall point I have not confirmed, and the prioritisation's impact assessments are directional at best. I would resolve these before proposing the set.

---

## Part 5 — Checkpoint

The dossier's final block, printed last so the closing screen carries the reading in miniature:

---

**Checkpoint — confirm before any work begins**

Literal ask: three initiatives, a ranking, metrics, a 30-day plan. Real ask: a small set of developed, prioritised, measurable initiatives that move one exact event — first dashboard shared within seven days — inside the self-serve model.

- Says "prioritisation must reference impact, effort, and self-serve fit" — actually the open rubric: assess every initiative against all three and let the order follow.
- Says "propose a minimum of three initiatives" — actually asks for three developed initiatives, each with a mechanism and a definition of done, not three labels.
- Says "improve activation" — actually one defined event; anything that moves a neighbour metric (logins, dashboards created) is off-target.

1. What is the current seven-day activation rate, and its distribution by segment?
2. Where do workspaces actually stall before a first share?

No work begins until you confirm or correct this reading.
