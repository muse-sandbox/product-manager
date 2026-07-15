---
plan_slug: official-tabs-version-block
status: in_progress
stage: Discovery + Delivery
updated_at: 2026-07-16T00:13:00+09:00
source: official-tabs-version-block.json
---

# Official Tabs always-on version block — population validation and test spec

## Goal

Validate the experiment population for the approved always-on Official Tabs block, then produce a test-ready Pitch, Control/Treatment solution specification, and analytics/measurement contract.

## Decision state

**Stage:** Discovery + Delivery

**Already fixed**

- The always-on Official Tabs block in the regular version-selection screen is the approved product direction (confirmed by the user this session).
- The mechanism is tested against the current selector as an A/B (Control = current selector; Treatment = always-on block, free Community versions still visible below).
- Deliverable set: Pitch, Control/Treatment solution specification, and analytics specification.
- The paywall opens only after an explicit block CTA; no automatic or repeating paywall; the free Community path stays visible and selectable.

**Still open**

- Whether the intended rollout population (new + existing eligible free users) is correctly estimated by the proposed test population — the stakeholder proposed testing through first-session users to neutralize novelty, but the claimed value is on existing-user volume.
- Estimand details: assignment unit, first-vs-repeat eligible exposure, and whether the decision concerns the initial response, the stabilized response, or both.
- Eligible reach and whether the eligibility predicate can be measured cleanly in every arm (SRM feasibility, overlap with the live #7622 first-session cohort).
- Non-inferiority margins for guardrails and sizing inputs (baseline, MDE, alpha, power) — required before sizing, out of scope for this deliverable set.
- Named decision owner / DRI and explicit confirmation that Branch B (forced off-tab tutorial) is closed.

## Approval needed

- Confirm the intended rollout population is new + existing eligible free users, so Discovery validates the test population against that estimand rather than a first-session-only read.
- Confirm platform scope is iOS-only for v1 (all cited efficacy evidence is iOS; Android was an underpowered null in #7622).
- Confirm a decision owner / DRI and that Branch B (forced off-tab tutorial) is closed, or tell me it is still open.

## Current work

No task is running.

## Product work

| ID | Phase | Business task | Why it matters | Owner | Done when | Status | Finding |
|---|---|---|---|---|---|---|---|
| D1 | Discovery | Validate the experiment population and estimand | The claimed value is on existing-user volume, but the proposed test runs through first-session users; a mis-specified population estimates the wrong effect for the rollout decision. | analytics | The analyst supports or rejects the proposed population and exposure design against the new+existing rollout estimand, provides the new-vs-existing eligible split, and states the assignment unit and first-vs-repeat exposure handling. | blocked | Reject first-session-only population for this decision: it estimates initial-exposure response in the first-session cohort, not repeated always-on exposure on existing-user volume where the value is claimed (Slack 1784111065.472719). Novelty is a time-varying treatment-effect component handled by a fixed stabilized-window read vs concurrent control, not by population choice. Recommended estimand: randomize all eligible free users at unified_id, assign at first eligible selector render, read initial+stabilized windows, pre-specify new-vs-existing segment split. BLOCKED numeric part: eligible reach and new-vs-existing split need a live #7622 read; ug-analytics UG_COOKIE not configured; live Confluence read also unavailable (alice.mu.se DNS). |
| D2 | Discovery | Confirm eligible reach and clean measurability | The experiment can only be read if the eligibility predicate fires identically in both arms and does not collide with the live #7622 cohort; unclean measurement invalidates any result. | analytics | Eligible reach is quantified, the eligibility/activation event is confirmed measurable in every arm with an SRM plan, and no cohort/surface/window overlap with #7622 is confirmed or flagged. | pending | — |
| L1 | Delivery | Write the Pitch | The decision owner needs one business-readable recommendation-to-test that states scope, hypothesis, evidence with its caveats, and the decision rule. | product-manager | The Pitch records the approved direction, the falsifiable hypothesis, treatment-level (not component-level) evidence, the validated population, and a single go/no-go rule — consistent with the Discovery findings. | pending | — |
| L2 | Delivery | Write the Control and Treatment solution specification | Engineering and design need one unambiguous implementation contract for the two arms. | product-manager | Every eligible state, transition, edge/empty state, paywall behavior, and the deterministic eligibility predicate are specified for Control and Treatment, sent identically in both arms. | pending | — |
| L3 | Delivery | Write the analytics / measurement specification | The result is only trustworthy if the primary metric, events, denominators, guardrails, and cannibalization measurement are fixed before launch. | product-manager | The metric contract defines the randomized unit/denominator, net-ARPU primary metric and window, maturity gate, competing-access (cannibalization) outcomes, guardrails with margin placeholders, event/SRM plan, and multiplicity policy — with unavailable inputs (margins, sizing) left explicit. | pending | — |
| R1 | Review | Independent Codex review of the draft set | A durable product artifact must pass an independent evidence-and-analytics audit before it is accepted. | reviewer | Codex returns a review; every BLOCKER and MAJOR finding is resolved or rejected with a source-backed reason, and the accepted version is saved to workspace/final/. | pending | — |

## Assumptions

- No cannibalization of other paid accesses is the stakeholder's own explicit assumption, not a fact — it is the primary risk the experiment must resolve.
- The effect is larger on existing-user volume than in the first session — a stakeholder claim to be tested via a pre-specified new-vs-existing segment read, not assumed.
- Reusing the Variation C Official card is a low-cost implementation candidate; neither the card nor its hierarchy was isolated in #7622, so it is not a validated causal mechanism.
- Confluence and ug-analytics reads may require live authentication; population validation depends on the operator's own authenticated sessions being available.

## Deliverable

One approved-plan-linked draft set: (1) Pitch, (2) Control/Treatment solution specification, (3) analytics/measurement contract — saved to workspace/drafts/claude/, independently reviewed by Codex, findings resolved, accepted version saved to workspace/final/. No Confluence publish without explicit user approval of the exact page operation.

## Intervention rule

Pause and request re-approval if Discovery changes the fixed decision, target population, primary metric, experiment design, or promised deliverable.
