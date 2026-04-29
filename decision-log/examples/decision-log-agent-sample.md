# Decision Log

**decision-id:** DL-2026-04-002-analytics-pipeline-streaming
**date:** 2026-04-14
**status:** accepted
**owner:** Luca

---

## Decision

Migrate the analytics pipeline from batch processing to a streaming
architecture to support near-realtime data delivery.

---

## Context

The team was evaluating two approaches for the analytics pipeline ahead
of an enterprise growth phase. Sales had flagged near-realtime dashboards
as a requirement in three active enterprise deals within the previous
month. The existing batch job was stable and cost-effective but could not
meet the latency expectations of enterprise customers without a fundamental
change to the pipeline design.

---

## Options Considered

**Option A: Optimize the existing batch pipeline**
Retain the current batch job and invest in performance tuning to reduce
latency and improve throughput within the existing architecture.

**Option B: Migrate to a streaming architecture**
Replace the batch pipeline with a streaming approach using available
infrastructure, delivering near-realtime data to downstream consumers.

---

## Chosen Option

Option B: Migrate to a streaming architecture

---

## Rationale

Near-realtime dashboard capability was cited as a requirement in three
recent enterprise sales conversations, creating a direct commercial
signal for the migration. Option A was not ruled out on technical grounds
but was implicitly set aside because performance tuning of the batch
pipeline would not close the latency gap to a level acceptable for
enterprise use cases. Option B was selected with Luca assigned as owner
and an implicit constraint that the decision would only be revisited if
migration cost exceeded expectations.

[NEEDS REVIEW - rationale partially inferred from context. Source
material does not explicitly state why Option A was rejected beyond
the latency gap.]

---

## Source

- **source-type:** slack-thread
- **source-date:** 2026-04-14
- **source-reference:** #product-eng channel, 2026-04-14
- **extraction-mode:** agent

---

<!--
OPTIONAL EXTENSION BLOCK

## Follow-up Actions
- [ ] Scope the streaming migration — Luca — [NEEDS REVIEW - no due
      date stated in source]
- [ ] Revisit decision if migration cost exceeds expectations — Owner
      TBD — ongoing

## Assumptions
- Available infrastructure supports a streaming architecture without
  significant additional provisioning.
- Enterprise customers require near-realtime latency, not true realtime.
- Migration cost will remain within acceptable bounds.

## Risks
- Migration cost overrun triggers a decision reversal — flagged
  explicitly in source as the only stated condition for revisiting.
- Streaming architecture introduces new operational complexity not
  present in the batch model — mitigation not discussed in source.

## Linked Artifacts
- [NEEDS REVIEW - no linked artifacts referenced in source material]

## Regulatory Flag
false
-->