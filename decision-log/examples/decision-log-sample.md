# Decision Log

**decision-id:** DL-2026-04-001-feature-flags-third-party
**date:** 2026-04-14
**status:** accepted
**owner:** Head of Product

---

## Decision

Adopt a third-party feature flag service for gradual rollouts and
experimentation instead of extending the internal configuration system.

---

## Context

The engineering team has been using a homegrown configuration system to
manage feature toggles since the product launched. As the customer base
grew to multiple enterprise segments with different release risk tolerance,
the configuration system became a bottleneck: releases required full
deploys, rollbacks were manual and slow, and there was no way to target
flags by customer segment or cohort. Two incidents in the past quarter
involved all customers being exposed to a partially ready feature because
staged rollout was not possible. The team evaluated whether to extend the
internal system or adopt a dedicated solution before the next major release
cycle.

---

## Options Considered

**Option A: Extend the internal configuration system**
Build targeting, percentage rollouts, and audit logging into the existing
homegrown toggle system using internal engineering capacity.

**Option B: Adopt a third-party feature flag service**
Integrate a dedicated feature flag platform via SDK, offloading rollout
logic, targeting rules, and audit trails to the external service.

**Option C: Introduce a feature branch and environment promotion model**
Replace toggle-based releases with a structured branching strategy and
additional staging environments to reduce exposure risk.

---

## Chosen Option

Option B: Adopt a third-party feature flag service

---

## Rationale

Option A was ruled out because the internal system would require an
estimated three to four months of engineering work to reach feature parity
with available third-party solutions, and the core capability is not a
differentiator for the product. Maintaining it long-term would create
ongoing engineering overhead with no customer-facing value.

Option C was ruled out because environment promotion does not solve the
customer segmentation requirement. Enterprise customers need the ability
to receive features ahead of or behind other segments based on contractual
commitments, which branching models cannot address without significant
operational complexity.

Option B was selected because dedicated feature flag services provide
targeting by customer attribute, percentage rollout, instant kill switch,
and audit logging out of the box. Integration risk is low given available
SDKs for the current stack. Cost is predictable and within the approved
tooling budget. The team can ship the first instrumented release within
two weeks of integration, directly unblocking the Q2 release plan.

---

<!--
OPTIONAL EXTENSION BLOCK

## Follow-up Actions
- [ ] Evaluate two to three vendors against security and data residency
      requirements — Engineering Lead — 2026-04-21
- [ ] Review vendor data processing agreement with Legal before
      contract sign — Legal + Engineering Lead — 2026-04-28
- [ ] Define internal conventions for flag naming, ownership, and
      retirement — Product + Engineering — 2026-05-05
- [ ] Instrument first feature with new service and validate targeting
      behavior in staging — Engineering — 2026-05-12

## Assumptions
- Selected vendor meets GDPR data residency requirements for EU customers.
- SDK integration does not require changes to the core data model.
- Operational cost remains within the approved annual tooling budget
  at current scale.

## Risks
- Vendor lock-in on flag targeting logic if migration is needed later —
  Mitigate by keeping business logic out of flag conditions and using
  simple boolean or percentage rules only.
- Flag proliferation and technical debt if retirement process is not
  enforced — Mitigate by establishing a quarterly flag audit routine.

## Linked Artifacts
- Q2 Release Plan (internal)
- Vendor security review checklist (internal)
- Incident report 2026-Q1-002 (internal)

## Review Date
2026-10-01 — Review vendor performance, cost at scale, and flag
debt accumulation after two release cycles.

## Regulatory Flag
true — Vendor data processing agreement required before contract
signature. EU customer data must remain within EU region.
-->