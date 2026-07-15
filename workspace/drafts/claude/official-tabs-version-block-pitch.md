---
authoring_agent: claude-code
status: ready-for-review
created: 2026-07-15
doc_type: experiment-pitch (rewrite of Confluence 815603200)
page_target: 815603200
page_title: "[2026-07-09] UG App: Official Tabs block in version selection"
addresses_review: workspace/reviews/codex/official-tabs-version-block-pitch-review.md
source_confluence_pages: [815603200, 813827551, 777817235, 788614610]
source_slack: workspace/sources/slack/official-tabs-scope-threads.md
source_experiments: [7622, 7256]
relates_to: workspace/final/official-tabs-process-recovery.md
publication: not published — no Confluence write without explicit user approval of the exact page operation
---

# UG App: Official Tabs block in the version-selection screen

## Scope & recommendation

**Recommended mechanism: an always-on Official Tabs block in the regular version-selection screen, for eligible free users, tested against the current selector.** This is Branch A from the scope discussion. It is a **recommendation to test, pending decision-owner sign-off** — the stakeholder proposed it as a hypothesis (Slack, 2026-07-15) but did not record a formal build approval, and no durable decision owner is named in the thread.

**Branch B** (a forced off-tab feature tutorial before the paywall) is **deprioritized** in favor of the always-on block. The stakeholder's latest message did not reaffirm Branch B; treat its closure as **the team's proposal, to be confirmed at the sync**, not an established fact.

### Option comparison (why Branch A)

| Option | Mechanism | Current evidence | Main risk | Cheapest discriminator |
|---|---|---|---|---|
| **A — always-on Official block (recommended)** | Choice-architecture / packaging at a high-intent point | Contextual Variation C (whole treatment) lifted exploratory Official-specific metrics; total ARPU not significant; engagement down. Always-on placement **untested**. | Cannibalizes free/other accesses → no net gain; engagement cost | The A/B in this pitch: randomized net ARPU + competing-access outcomes |
| **B — forced off-tab feature tutorial** | Experienced value before the ask, in the tour | None direct. Forcing has shown risk in adjacent contexts (recorded on 788614610 v17; #7256 iter 1). | Retention/engagement harm from compulsion | A separate first-session test (not this pitch) |
| **No-build — mature & diagnose** | Diagnosis | #7622 is preliminary; DSGN-6894 research is planned, no findings | Ships nothing this cycle | Mature #7622 to the 5% gate; run the value-vs-confusion study |

Branch A is the cheapest mechanism to test cleanly and the only one with a directly reusable component. The no-build diagnosis (mature #7622, run DSGN-6894) remains a parallel dependency, not a competitor.

---

## Pitch — context & idea

**Context.** Variation C of the First Session Flow experiment (#7622) contains a `Choose your version` screen: a prominent Official card (artwork, rating, Official badge, accuracy proof, 7-day trial CTA) above the free Community versions. It is **contextual** — shown only to users who just previewed the Official version in the guided tour. The **always-on placement in the regular version selector has never been tested.**

**Idea.** Reuse the existing Variation C Official card in the **regular version selector**, shown to every eligible free user whenever an Official version exists. The free Community versions stay visible and selectable below. The paywall opens only after an explicit CTA. There is no automatic or repeating paywall.

**Goal.** Increase **net 14-day ARPU per randomized eligible user** at the version selector, **without** reducing retention or tab engagement below a set margin, **and without a net decrement in total paid accesses** (the cannibalization guard). Exact metric definitions are in the metric contract below.

---

## Hypothesis

**Stakeholder hypothesis** (Slack, requester, 2026-07-15 `1784111065.472719` — recorded verbatim as the source of this pitch):

> If, on the version-selection screen, we highlight the Official Tabs block as in Variation C (artwork, accuracy proof, "Start 7-day free trial" button), then conversion from the internal paywalls will increase, because more users will take access from the new block (as we saw in Variation C) and will not cannibalize the other accesses (this is an assumption).
>
> The main rationale is that on the volume of existing users this produces a larger effect than in the first session alone.
>
> But test it through first-session users, to neutralize the novelty effect.

**Structured form.** *If* we place the Official card at the top of the regular version selector for eligible free users, *then* net ARPU increases, *because* premium value becomes visible at a high-intent decision point and more users take Official access from the block, *without* a net loss from cannibalized free or other accesses.

**Assumptions carried from the stakeholder — to be tested, not assumed:**
- **No cannibalization** of other accesses (the requester's own explicit assumption). This is the primary risk and is why the goal is randomized **net** ARPU plus a competing-access decrement check, not block-only conversion.
- **The effect is larger on the existing-user volume.** This is now read directly via a pre-specified new-vs-existing segment split (see Estimand), not assumed and not deferred to a separate cohort.
- **Novelty note.** Novelty is a time-varying part of the treatment effect, not a confound that a randomized control comparison removes. It is handled by a fixed stabilized-window read (see Estimand), not by restricting the test to new users.

---

## Design deltas from Variation C (the design work)

Reusing the C card is a **low-cost implementation candidate**, not a validated mechanism — the card and hierarchy were never isolated in #7622. Four design changes are required; each is currently `No data yet` on 815603200.

| # | Delta | Why | Owner |
|---|---|---|---|
| 1 | **Rewrite the lead copy.** Current C text — *"You've seen the official version…"* — assumes a prior Official preview. | In the always-on selector, most users have **not** previewed the Official version, so the line is false. | Design |
| 2 | **Layout of the free Community list.** | The Community header or first free version must stay **above the fold** so the free path is genuinely available. | Design |
| 3 | **Empty/edge states.** | No Official version → no block. Pro user → no block (decided rule). Trial-ineligible / former subscriber / referral → excluded from v1 eligibility (see predicate). | Design + PM |
| 4 | **Always-on entry condition.** | Block renders on the regular selector for eligible users, independent of the tour. | PM + Eng |

## Treatment dimensions (what is held constant vs changed)

To avoid calling this "the same screen," the bundled treatment changes several dimensions at once:

- **Held constant from C:** the card component (artwork, rating, Official badge, accuracy proof, 7-day CTA) and the card-above-free-list hierarchy.
- **Intentionally changed (part of the treatment):** placement (regular selector, not the tour), exposure frequency (every eligible render, not once), preceding context (no prior Official preview), lead copy, layout of the free list, and eligibility population.

The experiment measures this **bundle** vs control. It does not isolate any single dimension.

---

## Evidence & confidence

All figures re-verified against 777817235 v144 (iOS, **2026-07-10 cut**). The current 815603200 page still quotes the older 2026-07-05 cut and should be refreshed.

The closest evidence is the **whole contextual Variation C treatment** — a multi-part first-session treatment. **No comparison isolates the card, its hierarchy, or the engagement effect**, and the Official-specific cuts are exploratory (no pre-registered secondary-metric plan, no multiplicity policy):

- **Official Tabs ARPU +34.94% (p=0.003)**, **Official charge CR +28.65% (p=0.006)** — exploratory, treatment-level.
- **Total ARPU +9.47% (p=0.09)** — not significant, and preliminary.
- **Tab-view 60s engagement −1.88% (p=0.001)** — significant decline (whole-treatment).
- Retention 7d/14d −2.15% (p=0.09) / −2.09% (p=0.07) — directionally negative, non-significant; not evidence of safety.
- **Descriptive, hypothesis-generating only:** 9,125 / 10,311 ≈ 88% of chooser-viewers clicked a free version; later ordinary-visit access point estimate 3.26% (C) vs 3.41% (control), with **no reported uncertainty or unit of analysis**. Neither establishes cannibalization — control users may also pick free content; these observations motivate the competing-access guard, they do not prove a decrement.
- All revenue results are **preliminary** — pending trials 9.9% / 11.6% / 12.6% exceed the source's 5% gate in every iOS branch.

**Reading for this pitch:** the treatment moves exploratory Official-specific conversion but has **not** shown a net total-ARPU gain and carries an engagement cost. Whether the always-on placement **adds** revenue or merely **shifts** it is exactly what this experiment must resolve.

**Placement limitation:** the C evidence is contextual (post-preview/post-paywall). It shows the component is feasible and reusable; it does **not** validate the always-on regular-selector placement.

---

## Estimand & population

**Target estimand:** the effect of the always-on block on **net 14-day ARPU per randomized eligible free user** in the regular version selector, on the **intended rollout population (new + existing eligible users)**, over a fixed post-exposure window.

- **Population / assignment:** all eligible free users (predicate below), randomized at the **user** level (`unified_id`).
- **First eligible exposure:** assignment is fixed at the **first** eligible selector render; the block then shows on all subsequent eligible renders. Multiple opens/sessions roll up to the one assigned user.
- **New vs existing:** read as a **pre-specified segment split** (new/first-session vs existing users), not as separate experiments. This directly tests the "bigger on existing volume" claim instead of assuming it.
- **Novelty:** handled by reading a **fixed stabilized window** (effect over days N–M after first exposure, N/M to be set at sizing) alongside the initial-response read — not by restricting to new users. Report both initial and stabilized effects.
- **Overlap:** verify no cohort/surface/window collision with the live #7622 first-session flow before launch; do not assume contamination.

This replaces the earlier new-users-first phasing, which measured a different population than the rollout decision needs.

---

## Experiment design

### Variations (core A/B)

| Arm | Experience | Paywall behavior |
|---|---|---|
| **A — Control** | Current version selector, no Official block | Current production |
| **B — Official block (always-on)** | Reuse the C card at the top of the regular selector; free Community versions visible below | Paywall opens only after the block CTA; dismiss returns to the selector; no automatic/repeat |

Optional depth arms (voluntary content preview, voluntary one-feature micro-demo) test a **different** question — does experiencing value add lift over packaging — and are **out of scope** for this test. Add only if sized for a multi-arm design; the micro-demo feature must be chosen from the requester's input ("what buyers use most + chords/tabs dependency"), not a guessed top-5.

### Metric contract (must be fixed before sizing)

- **Randomized unit / denominator:** user (`unified_id`) / eligible free users who fire `Tab Official Version Block Eligible`.
- **Primary metric:** **net 14-day ARPU per randomized eligible user.** Net = charges − refunds/chargebacks; a trial is counted at **charge**, not trial start. Currency and gross/net conversion per the standard revenue pipeline.
- **Observation window:** 14 days post-first-eligible-exposure, **equal across arms**.
- **Maturity gate:** read only when pending trials < **5%** in every arm (carried from #7622); ~14-day charge maturity.
- **Competing-access outcomes (cannibalization guard):** total paid-access starts per user, any-tab open rate, Community-version open rate — same 14-day window. **Cannibalization = a significant randomized decrement** in total paid accesses or net revenue vs control (not the 88% free-choice rate).
- **Guardrails:** Retention D1 / D7 / D14; **Tab-view 60s engagement** (share of tab views with ≥60s dwell); users with 3+ tabs/scores weekly. **Non-inferiority margins: No data yet — must be set before launch.**
- **Multiplicity:** one primary (net 14d ARPU) drives go/no-go; guardrails read as non-inferiority; new-vs-existing segment reads are pre-specified secondary with a stated correction; optional arms excluded.
- **Go/no-go:** ship **iff** net 14d ARPU is significantly positive **AND** every guardrail clears its non-inferiority margin **AND** no significant decrement in total paid accesses; otherwise iterate or stop.
- **Sizing inputs** (baseline, MDE, alpha, power, per-arm sample, duration): **No data yet.** Size for two arms; single-arm sizing is not valid.

### Eligibility predicate (deterministic, sent identically in both arms)

Render the block **iff all** hold:
- `pro_rights = free` (no active Pro);
- an **Official version exists** for the song;
- **trial-eligible** (v1 excludes trial-ineligible users, former subscribers, and referrals — flag for confirmation);
- **platform = iOS** (all efficacy evidence is iOS; Android was an underpowered null in #7622 and is out of scope unless separately sized);
- render on the regular selector (first and subsequent eligible renders).

Existing Pro users: **no block (decided rule).** Validate assignment-to-activation rates by platform and eligibility reason (SRM).

---

## Solution (engineering-facing)

No new interaction pattern — the Official card and paywall already exist; this places the card in a new surface and adds the tracking to read it.

1. **Surface & trigger.** The regular song **version-selection screen** (`choose_version`), on open — not the first-session tour step.
2. **Eligibility.** Render the block **iff** the eligibility predicate above holds; otherwise render the current selector unchanged.
3. **What renders.** Reuse the **existing Variation C Official card** as the first element (artwork+title, rating+reviews, Official badge, accuracy proof, "Start 7-Day Free Trial" CTA). Below it, the **existing** free Community list with current behavior; Community header/first free version **above the fold**. Lead copy is **configurable** and replaced from the C default.
4. **Interaction.** Block CTA → open the **existing paywall** with source **`Official Tabs Version Block`** (the only path from block to paywall). Paywall dismiss → return to the **same** selector; **no auto-reopen, no repeat.** Free version tap → existing `Version List Tab Click`. **Hard constraints:** no autoplay, no required preview, no mandatory tutorial, no timer-triggered or repeating paywall.
5. **Flagging.** Arm read from `experiments.variation` on the activation row; do **not** duplicate a variant flag into every event.
6. **Events.** `Tab Official Version Block Eligible` (all arms, on eligible render) → `... Block View` (treatment) → `... Block CTA Click` (treatment). Reuse downstream paywall/purchase events. Value strings ship **character-for-character** (see the instrumentation lesson).

### Behavior by scenario

| Scenario | Expected behavior | Status |
|---|---|---|
| Eligible free user, Official version exists | Show Official block + Community versions | Defined |
| Block CTA click | Open paywall (only entry) | Defined |
| Paywall dismiss | Return to selector; no repeat | Defined |
| Community version click | Open the selected free version | Defined |
| No Official version | Block not shown | Defined |
| Existing Pro user | No block | **Defined (decided rule)** |
| Trial-ineligible / former subscriber / referral | Excluded from v1 eligibility | Defined (confirm at sync) |

---

## Analytics

The event/instrumentation spec on 815603200 v5 carries forward. Essentials:

- **Activation (STRICT):** `experiment_event_start` = **`Tab Official Version Block Eligible`**, fired in **every** arm (incl. Control) on eligible selector render, before any visual difference. Because activation is downstream of app start, an **SRM check is mandatory** before trusting any per-arm read.
- **Distinct paywall source:** `Official Tabs Version Block` — must not merge with the existing `Official Tabs Tab Versions`.
- **Cannibalization measurement:** per-placement purchase attribution is unreliable (788614610 v17: within the First Session Health registry, the paywall a purchase came through is not visible). The causal read is therefore the **randomized net-ARPU and total-paid-access** comparison between arms, not block-only conversion.
- **Instrumentation lesson (recorded on 815603200 v5):** a spec string (`Choose Version` vs shipped `Official Tabs Chose Version`) split one funnel across two values, and a declared `from_tour=1` was never sent. Event names and value strings must ship **character-for-character**, verified in production in the first days before results are read. *(The page attributes this to "experiment 7577, iteration 3," while 777817235 identifies iteration 3 as #7622; the identity is unresolved, so the lesson is kept as a source-page warning without an experiment number.)*

---

## Guardrails

- **Goal:** net 14-day ARPU per randomized eligible user.
- **Anti-cannibalization:** total paid-access starts; any-tab open rate; Community opens (14-day window).
- **Engagement:** Tab-view 60s engagement (Variation C showed a significant −1.88% decline — the guardrail most at risk).
- **Retention:** D1 / D7 / D14.
- **Non-inferiority margins** for Retention 7d and Tab-view 60s engagement **do not exist yet and must be set before launch.** A non-significant guardrail result is **not** evidence of safety.

---

## Decision & next steps

**Decision status:** recommendation pending owner sign-off. Do not roll out without experiment evidence. Keep the free Community path visible. Do not combine with a mandatory tutorial or first-session-flow changes.

1. **Confirm at the sync:** owner/DRI; that Branch B is deprioritized; the target problem; and that Branch A is approved for design.
2. **Set the metric contract inputs** (margins, sizing) and confirm the v1 eligibility exclusions (trial-ineligible / former subscribers / referrals).
3. **Design deltas 1–4** (copy, layout, edge states, entry condition).
4. **Verify no overlap** with the live #7622 cohort/surfaces.
5. **Size** the A/B; set non-inferiority margins and the stabilized-window bounds.
6. **Finalize mockups** only after 1–5. (Preserves the requester's logic → calculations → mockups order.)

## Open questions

- Owner/DRI, and explicit confirmation that Branch B is closed.
- v1 handling of trial-ineligible / former-subscriber / referral users.
- Non-inferiority margins and the stabilized-window bounds (N–M days).
- Resolution of the #7577 vs #7622 experiment-identity mismatch before quoting the tracking lesson as history.

---

## Source ledger

| Source | Class | Version / status | Used for |
|---|---|---|---|
| 815603200 (CRO, UMN-12370) | Primary Confluence — **rewrite target** | v5, read 2026-07-15 | Existing pitch: placement idea, constraints, instrumentation spec, decision; stale 2026-07-05 figures to refresh |
| 777817235 | Primary Confluence | v144, 2026-07-10 cut | Whole-treatment Variation C figures, engagement decline, descriptive competing-path observations, maturity gate |
| 813827551 (DSGN-6894) | Primary Confluence | v3 | Research plan (no findings) — the value-vs-confusion question |
| 788614610 | Primary Confluence | v17 | Registry attribution limits; forcing-risk precedent (#7256) |
| `workspace/sources/slack/official-tabs-scope-threads.md` | Slack — text verified | re-read 2026-07-15 (incl. Artyom `1784111065.472719`) | Stakeholder hypothesis, the "this is an assumption" caveat, existing-user-volume rationale, test-cohort proposal; **no build approval and no DRI in the thread**; Branch B not reaffirmed |
| `workspace/final/official-tabs-process-recovery.md` | Secondary reviewed synthesis | accepted 2026-07-15 | Decision-record context and source routing |

---

## Resolution log — Codex review (NOT READY; 2 blockers, 4 major, 3 minor)

Review: [`workspace/reviews/codex/official-tabs-version-block-pitch-review.md`](../../reviews/codex/official-tabs-version-block-pitch-review.md). All findings accepted; no source-backed disagreements. Two decisions were taken with the user this session: **close Branch B** (recorded as a proposal to confirm, since the stakeholder did not explicitly close it) and **design for the target population** (not new-users-first).

| Finding | Resolution |
|---|---|
| **BLOCKER 1** — Branch A ratified though the record leaves the decision open | **Accepted.** Reframed from "decides/lock" to **recommendation pending owner sign-off**; added an A/B/no-build option comparison; recorded that no DRI and no build approval exist in the thread and that Branch-B closure is a team proposal to confirm. |
| **BLOCKER 2** — new-user-first plan unsourced + wrong estimand | **Accepted.** Slack source updated with Artyom's actual hypothesis message (sourcing the assumptions). Replaced the phasing with a named **estimand**: target population (new+existing), user-level randomization, first-exposure assignment, pre-specified new-vs-existing segment reads, and novelty handled by a fixed stabilized-window read. Removed "novelty is a confound." |
| **MAJOR 1** — over-attribution to the block | **Accepted.** Evidence section now attributes results to the **whole contextual Variation C treatment**; card/hierarchy explicitly not isolated; "reliably" and "validates" removed. |
| **MAJOR 2** — cannibalization over-claim | **Accepted.** The 88% free-choice rate and 3.26/3.41 point estimates labeled descriptive/hypothesis-generating; cannibalization defined as a **significant randomized decrement** in a pre-specified competing outcome (total paid accesses / net revenue). |
| **MAJOR 3** — metric/decision rule undefined | **Accepted.** Added a metric contract: net 14d ARPU, unit/denominator, fixed window, maturity gate, competing outcomes, guardrail metrics+units, multiplicity, and a single go/no-go rule. |
| **MAJOR 4** — "eligible" undefined at activation | **Accepted.** Added a deterministic eligibility predicate (paid rights, Official availability, trial history, referrals, platform=iOS, first/subsequent render), sent identically in both arms, with SRM validation. |
| **MINOR 1** — treatment differences understated | **Accepted.** Added a "treatment dimensions" section (held constant vs intentionally changed). |
| **MINOR 2** — Pro-user contradiction | **Accepted.** "No block for Pro users" is now a decided rule in both prose and the scenario table. |
| **MINOR 3** — #7577 attribution | **Accepted.** Tracking lesson retitled as "recorded on 815603200 v5," experiment number removed pending identity resolution. |
