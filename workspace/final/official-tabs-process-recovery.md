---
authoring_agent: claude-code
reviewed_by: codex
review: workspace/reviews/codex/official-tabs-process-recovery-review.md
status: final
created: 2026-07-15
doc_type: decision-record / process-recovery
relates_to: workspace/final/official-tabs-banner-shaping.md
source_confluence_pages: [815603200, 813827551, 777817235, 788614610]
source_slack: workspace/sources/slack/official-tabs-scope-threads.md
source_experiments: [7622, 7577, 7256]
review_verdict: READY WITH CHANGES (0 blockers, 1 major, 3 minor — all resolved; see Resolution log)
thread_evidence: Exact Slack thread text read via the connected Slack app and stored locally (see source_slack). The message wording, authors, and timestamps are in evidence. The two attached images (F0BH2AH8524, F0BJ9NMQQ0Y), the five prototype visuals, and the Figma frames were NOT inspected — only the textual prototype descriptions are in evidence.
publication: not published — no Confluence write or message send without explicit user approval
---

# Official Tabs: decision record and process recovery

> **Three evidence classes, kept apart throughout.**
> **Confluence-verified** (read 2026-07-15): 815603200 v5, 813827551 v3, 777817235 v144, 788614610 v17.
> **Slack-thread-verified — text only** (read 2026-07-15 via the connected Slack app; stored at `workspace/sources/slack/official-tabs-scope-threads.md`): the 2026-07-09 and 2026-07-15 exchanges. Exact wording and authorship are in evidence.
> **Not inspected**: the five prototype visuals, the two attached Slack images, the Figma frames, any durable decision-owner record, and the intent behind ambiguous phrasing. These remain open and must be confirmed with the colleague before they drive a decision, a message, or a publication.

## Executive answer

The disagreement can now be read from the exact thread, and the evidence settles the research-claim dispute while clarifying what remains open. Read the four buckets in order.

**A. Verified.**
- *From Slack:* on 2026-07-09 the colleague raised **two branches "for discussion, independent of rollout"** — (A) always show a large Official block in the version selector with a CTA straight to the paywall, like Variation 3; (B) **extend the off-tab onboarding into a forced feature tutorial before the paywall**. He asked to add questions/hypotheses to a research plan and to wait for the retention sample. On 2026-07-15 he corrected the sequence — *"я думал, мы просто заменим экран версий, не будем менять путь до него… давай определимся сначала с этой логикой, потом расчеты, а потом уже макеты"* — and challenged the research claim. In the retrieved threads **neither branch is approved for build**, and the retrieved thread contains **no reply agreeing to remove the free Community versions**.
- *From Confluence:* pitch 815603200 (v5) keeps the free versions visible, opens the paywall only after an explicit CTA, forbids any automatic/repeating paywall, is scoped to the selector, and **explicitly excludes a mandatory tutorial and first-session-flow changes**. Its own decision line: *proceed to sizing; do not roll out without evidence.* Research page 813827551 (DSGN-6894) is a plan with **no findings**. On the current 2026-07-10 cut (777817235 v144), Variation C shows exploratory Official-specific lifts, **no** significant total-ARPU lift, a **statistically significant** engagement decline, and preliminary revenue; the **always-on selector placement is untested**.

**B. Supported retraction.** The claim *"я сделала рисерч, поняла что так не сработает"* is **not supported and should be withdrawn.** No completed research and no always-on selector test exists — the colleague's *"где исследование?"* is factually fair. What the evidence supports is narrower: the mechanism is *untested in this placement*.

**C. Where a content gap, not only a process gap, remains.** Branch A is represented in 815603200. Branch B, as worded (a *forced* tutorial on the off-tab before the paywall), is **not** represented — the draft offers a *voluntary* selector preview instead, which is a different mechanism. So a residual content question is open, on top of the sequencing issue.

**D. Proposed next decision.** Do not ratify a solution. Confirm the decision record with the colleague — the literal ask, the problem, which branches are still live, and who owns the decision — then choose among materially different mechanisms before any sizing or mockups.

---

## 1. Decision record — verified against the Slack thread

Source: `workspace/sources/slack/official-tabs-scope-threads.md` (channel `ug-monetization-pvt`, threads `1783595323.736059` and `1784050824.694299`). The wording is in evidence; the prototype visuals and the two attached images are **not**. No item is recorded as "requested" without a quotable ask; where the thread shows no answer, the status is "no answer in thread."

| # | Item | Status (Slack thread text) | Confluence cross-check |
|---|---|---|---|
| 1 | Wait for the retention sample (Android disabled, "там все плоско") and read 14d longer conversions for Variation 3 | **Explicit ask** — Thread A, 2026-07-09 | Consistent with 777817235 v144 labeling Android an underpowered null |
| 2 | Add questions/hypotheses to the research plan; colleague supplied the correct link (813827551) | **Explicit ask** — Thread A | 813827551 v3 holds four hypotheses and four key questions — carried out |
| 3 | **Branch A** — always show the large Official block in the version selector, with a CTA straight to the paywall, "как в 3й вариации" | **Raised for discussion, independent of rollout** ("хотел обсудить две ветки… давай тут в треде дообсудим") | Represented as the spine of 815603200 |
| 4 | **Branch B** — extend the off-tab onboarding: not 5s→paywall, but **"заставить прокликать фичи (прям туториалом)"**, then paywall, then the prior scenario | **Raised for discussion, independent of rollout** | **Not represented, and partly excluded** — 815603200 forbids a mandatory tutorial and first-session-flow changes (see §3) |
| 5 | Feature selection for a demo | Author proposed "топ-5 фич которые конвертят в покупку"; colleague **did not agree** — "это сложно, оффтаб же весь закрыт… давай посмотрим, чем чаще всего пользуются купившие и зависимость от аккордов/табов" | 815603200 D-arm feature is "No data yet" (candidate: Backing Track); the colleague's redirect is the unmet analysis input |
| 6 | Remove the free Community versions and show a single Official banner | Author asked: "то есть ты хочешь убрать бесплатные версии, и поставить как 1 баннер…?" — **no answer in the retrieved thread** | 815603200 keeps the free versions visible and additive |
| 7 | Five prototypes presented | **Verified as presented** (2026-07-15); **text descriptions only — visuals/Figma not inspected** | Not applicable |
| 8 | Sequence: settle the logic, then calculations, then mockups | **Explicit ask** — Thread B, 2026-07-15 ("давай определимся сначала с этой логикой, потом расчеты, а потом уже макеты") | Reasonable process rule |
| 9 | Research challenge | Author: "я сделала рисерч, поняла что так не сработает" → colleague: "как?" and "где исследование? вижу результаты прошлых запусков, но не аргументов что сработает" | 813827551 has no findings; the retraction in §2 follows |

**Exact prototype descriptions (text in evidence; visuals not inspected):**
1. A version-selection screen, identical to the tabs/chords selection.
2. The Variation C screen, shown right after choosing chords/tabs.
3. A big banner after tabs/chords, with the free choice "сильно ниже или под скроллом."
4. After the off-tab demo, **before** the paywall — a screen about quality and features.
5. After the off-tab demo, **merged** with the paywall — a screen about quality and features.

Prototypes 1–3 sit on the selector screen; **3 pushes the free path below the fold** — the nearest thing in evidence to the unanswered "single banner" question, and it is the author's own exploration, not an agreed direction. Prototypes 4–5 sit on the off-tab path **before** the selector, i.e. branch-B territory and outside 815603200's scope.

**Still open (needs the colleague, not inferable from the text):** what the two attached images and the five visuals actually show; whether branch B is still a live hypothesis or is satisfied by a selector preview; and who owns the logic decision. The thread names **no** DRI.

---

## 2. The claim to retract, and what the data supports

**Claim under audit:** "я сделала рисерч, поняла что так не сработает."

**Verdict: not supported. Withdraw "не сработает." The supported statement is "untested in the always-on placement, and not yet decision-ready."**

Evidence on the closest mechanism, from the **current 2026-07-10 snapshot** (777817235 v144). All Official-specific cuts are **exploratory**: the page records no pre-registered secondary-metric plan and no multiplicity policy. The figures describe the **whole Variation C treatment**, which differs from control in more than the highlighted card; no source isolates the card or its hierarchy as the cause.

| Evidence (Variation C treatment, iOS, 2026-07-10) | Value | Reading |
|---|---|---|
| members→total accesses (goal metric) | +6.90% (p=0.047) | Does not clear a two-comparison Bonferroni threshold of 0.025 (a reviewer-applied check, not the experiment's rule) |
| Total ARPU | +9.47% (p=0.09) | **No significant total-revenue lift** |
| Official Tabs ARPU *(exploratory)* | +34.94% (p=0.003) | Official-specific monetization moved |
| Official Tabs charge CR *(exploratory)* | +28.65% (p=0.006) | More charges on the Official-specific cut |
| Retention 7d / 14d | −2.15% (p=0.09) / −2.09% (p=0.07) | Directionally negative, non-significant — not evidence of safety |
| **Tab-view engagement 60s** | **−1.88% (p=0.001)** | **Statistically significant engagement decline**; no non-inferiority margin exists to judge practical materiality |
| Later ordinary (`other`) visits: C vs control access | 3.26% vs 3.41% (point estimates) | **No p-value, interval, or unit-of-analysis** on this cut; a difference is *not* established, and repeat users/visits may be double-counted |
| Version-chooser funnel | 9,125 / 10,311 ≈ 88% of C chooser-viewers click a **free** version | Descriptive funnel observation; do not infer motivation |
| Placement of all the above | Contextual only — shown **after** a first-session Official preview + paywall dismiss | The **always-on selector placement is untested** (815603200 "Evidence limitation") |
| Maturity | Pending trials 9.9% / 11.6% / 12.6% > the page's 5% gate; ~25% of charges older than 14 days | **All revenue results preliminary** |

*(The 2026-07-05 values on 815603200 v5 — Official ARPU +35.39%, total ARPU +6.61% p=0.27 — are an earlier cut, superseded by the read above.)*

**Defensible statement:** Variation C's multi-part treatment raised exploratory Official-specific metrics at the reported snapshots, produced no significant total-ARPU lift, carries a statistically significant engagement decline with no defined practical margin, and was measured only in a contextual placement. Whether an *always-on* selector block works is **untested** — a reason to run a controlled test, not a conclusion that it fails.

**"Где исследование?" — the challenge is correct.** 813827551 (DSGN-6894) is a plan with no findings; what exists is quantitative *results* from prior iterations plus a *planned* discovery study to distinguish value from confusion/entrapment. Neither yet argues that a specific new design will or will not work. The honest framing is "the argument is an evidence gap, and here is the plan to close it."

---

## 3. Branch mapping — three scopes, kept distinct

Three scopes must not be collapsed: the **discussion scope** (the two branches raised in the thread), the **815603200 test scope** (the regular-selector A/B/C/D experiment), and the **prototype exploration scope** (the five screens).

**Branch A** — always-on Official block in the selector with a CTA to the paywall — **is represented**: it is the spine of 815603200.

**Branch B** — "заставить прокликать фичи (прям туториалом)" on the off-tab, *then* the paywall — **is not represented, and is partly the opposite of what the draft allows.** 815603200 offers *voluntary, non-blocking* preview/micro-demo arms **inside the selector** and explicitly excludes a mandatory tutorial and first-session-flow changes. A forced off-tab tutorial and a voluntary selector preview differ in placement, timing, compulsion, and target behavior. Prototypes 4–5 are the screens that actually match branch B, and they sit outside 815603200's scope.

**This deviation is a defensible precaution — but it should have been flagged, not presented as coverage.** Declining to build a *forced* tutorial is reasonable because forced flows have shown risk in adjacent first-session contexts: *"Forcing tab display worsens results — verified in experiment 7256, iteration 1"* (788614610 v17), and 777817235 v144 reports that forcing actions *"destroys best segments"* on a minimum-song-selection result. Neither precedent directly tests a forced feature tutorial. Separately, **Variation B's multi-part treatment — which includes the repeating `Official Tabs Recently Viewed` loop — caused significant retention declines** (1d −7.76%, 7d −4.81%, 14d −4.91%, all p<0.001; 777817235 v144); the loop is a plausible contributor but was **not isolated** from B's other path, routing, and exposure changes. Converting a forced tutorial into a voluntary preview is therefore a **precautionary** product choice consistent with those risks — not a proven remedy for B's retention mechanism. The process miss is that the change of mechanism was not surfaced to the colleague as a deviation from his branch B.

**Consequence:** do not tell the colleague both branches are covered. Ask whether a voluntary selector preview is an acceptable substitute for the forced off-tab tutorial, or whether branch B should be tested on its own surface.

---

## 4. What the design does and does not satisfy

**Satisfied — three interaction constraints, verified on 815603200:**
1. The free Community path stays visible and selectable.
2. The paywall opens only after an explicit CTA; dismiss returns to the same selector.
3. No automatic or repeating paywall — deliberately excluding the `Official Tabs Recently Viewed` loop (reach 6.4% → 43.5% in Variation B), which the source treats as a confound on B's headline lift (777817235 v144).

The instrumentation spec is also careful (strict activation event `Tab Official Version Block Eligible`, mandatory SRM check, a distinct paywall source). **These are pre-launch specification choices, not evidence that tracking has shipped correctly or that the design is experiment-ready.**

**Not yet satisfied — unresolved guardrails, from the same page and the current data:**
- Platform, baseline, target lift, MDE, power, alpha, four-arm sample size, duration: **"No data yet."**
- Non-inferiority margins for Retention 7d and for users with 3+ tabs/scores weekly: **"No data yet."**
- Eligibility rules (trial-ineligible, former subscribers, referrals, platform-specific): **"Not defined."**
- The micro-demo feature: **"No data yet"** — and the colleague's redirect ("чем чаще всего пользуются купившие… зависимость от аккордов/табов") is the unmet input for choosing it.
- A **statistically significant** 60-second engagement decline in the current read, with no margin to judge it (777817235 v144).

The design is a well-constrained *concept*, not a launch-ready or experiment-ready one. The three interaction constraints are not a full guardrail set.

---

## 5. Minimal next step — confirm the record before choosing a solution

**The cheapest reliable step is to confirm the decision record**, not to ratify a mechanism; ratifying now would repeat the sequencing error this document addresses.

**Step 1 — confirm with the colleague (owner: not named in the record; do not assign one until confirmed):**
- the literal ask and the problem it solves;
- whether removing free versions was ever intended (no answer in the retrieved thread);
- whether **branch B** (a forced off-tab tutorial before the paywall) is still live, or is satisfied by a voluntary selector preview;
- the feature-selection approach for any demo, given the redirect to buyer-usage/chords-tabs analysis;
- who owns the logic decision and the sequence.

**Step 2 — only then, the confirmed owner chooses among materially different options** (not variants of one idea):

| Option | Mechanism | Causal question |
|---|---|---|
| Selector A/B (static Official block) | Choice architecture at version choice | Does visibility/packaging alone move total ARPU? |
| Selector A/B/C/D (add voluntary preview/micro-demo) | Choice architecture + experienced value in the selector | Does proving value in the selector add lift over packaging? |
| First-session feature tutorial (branch B on its own surface) | Experienced value before the paywall, in the tour | Does experiencing features before the ask change conversion — and at what retention cost, given forced flows have shown risk? |
| No-build: complete DSGN-6894 and/or mature #7622 | Diagnosis | *Why* do users convert — value or confusion/entrapment? Are the revenue reads valid once mature? |

**Step 3 — only after a mechanism is chosen** do the calculations (four-arm MDE, sample size, duration, baseline, non-inferiority margins) and final mockups, preserving the requested **logic → calculations → mockups** order.

**Until Step 1 is done, all five screens are "exploration," not decisions.**

---

## 6. Draft reply to the colleague (RU) — review only, do NOT send until the record is confirmed

*Personal message to a named colleague. Hold until the record is confirmed with them; never publish to Confluence. It acknowledges and asks to confirm; it does not assert intent the thread does not show.*

> Артём, давай сверимся по логике — часть расхождения из-за порядка работы с моей стороны.
>
> Формулировку «я сделала рисерч, поняла что так не сработает» беру назад — сказала слишком сильно. Завершённого исследования нет: DSGN-6894 в статусе «в работе», там гипотезы и вопросы, но не метод и не результаты. У меня есть результаты прошлых итераций, а не доказательство, что конкретный дизайн не сработает. Ты прав, что аргумента «что сработает» пока нет.
>
> Что данные реально позволяют сказать по вариации C (срез 2026-07-10, с ограничениями):
> 1. Official-разрезы выросли (Official ARPU +34.94%, p=0.003; charge CR +28.65%, p=0.006), но это exploratory-метрики без поправки на множественность и эффект всей вариации, а не доказанно «блока».
> 2. Total ARPU незначим (+9.47%, p=0.09); все revenue-числа ещё preliminary.
> 3. Значимо просела вовлечённость: Tab View 60s −1.88% (p=0.001); границы non-inferiority нигде не заданы.
> 4. Always-on размещение в обычном селекторе мы не тестировали. Поэтому честно — «не проверено», а не «не сработает».
>
> Пять экранов — это разведочные наброски, не план. По ветке B (прокликать фичи туториалом до пейвола): в текущем драфте я сделала превью в селекторе **добровольным**, а не форсированным — как предосторожность. Форсированные сценарии в соседних контекстах давали риск (7256: «форсирование показа таба ухудшает результаты»), а вся вариация B (в ней есть повторяющийся paywall-цикл) значимо роняет ретеншен — но отдельный вклад именно цикла не изолирован. Это осторожный выбор, а не доказанное решение проблемы B. И это другая механика — я должна была проговорить это как отклонение, а не подать как «ветку закрыли». Хочу свериться: держишь ветку B как отдельную живую гипотезу на офф-табе, или добровольное превью в селекторе её заменяет?
>
> Про выбор фичи — ок, беру твой ориентир: смотрим, чем чаще пользуются купившие и зависимость от аккордов/табов, вместо «топ-5».
>
> Предлагаю по твоему порядку: сначала зафиксируем логику и скоуп (какую механику проверяем, сохраняем ли бесплатный путь, трогаем ли путь до селектора, кто владелец решения), потом расчёты, потом макеты. Сверим — и я приношу расчёт по четырём аркам и макеты уже по согласованной логике.

---

## 7. How to safeguard the process going forward

The exchange went sideways because an *exploration* was read as a *proposal*, a *discussion item* risked being read as an *agreed build*, and a *mechanism deviation* (forced → voluntary) was not surfaced. A one-line decision record per item prevents that. Fill it before any mockup or calculation:

| Field | What it captures | Failure it prevents |
|---|---|---|
| **Ask** | The literal request, verbatim, with who and when | Recording "you asked for X" when they didn't |
| **Mechanism** | The single causal lever, incl. forced vs voluntary, placement, timing | Silently swapping one mechanism for another |
| **Decision status** | requested / proposed-to-discuss / agreed / no-answer / exploration | Explorations read as plans |
| **Scope line** | What is explicitly IN and OUT | Silent scope creep (e.g. path-before-selector) |
| **Evidence** | Fact / calculation / assumption / gap, with source | "Research shows…" with no findings |
| **Owner** | Who decides, who executes | Decisions no one is accountable to close |

**Three standing rules:**
1. Label any screen "exploration" until its mechanism and scope have an "agreed" status. A mockup is never a decision.
2. Never write "requested by <person>" without a quotable ask; where the thread has no answer, the status is "no answer."
3. Do not name a decision owner in a shared record until that ownership is confirmed. When you deviate from a stakeholder's stated mechanism (e.g. forced → voluntary), flag the deviation explicitly.

---

## Source ledger

| Source | Class | Version / status | Used for |
|---|---|---|---|
| `workspace/sources/slack/official-tabs-scope-threads.md` | **Slack-thread — text verified; visuals not inspected** | read 2026-07-15 | The exact asks, answers, no-answers, branch wording, prototype descriptions, and sequence request in §1 |
| 815603200 (CRO, UMN-12370) | Primary Confluence | v5, read 2026-07-15 | Pitch contents: free-path, explicit-CTA, no-loop, no-mandatory-tutorial constraints; selector scope; "do not roll out without evidence"; instrumentation spec; superseded 2026-07-05 figures |
| 813827551 (DSGN-6894) | Primary Confluence | v3, read 2026-07-15 | Research is a plan in progress; no findings |
| 777817235 | Primary Confluence | v144, read 2026-07-15 | Current 2026-07-10 Variation C figures, Variation B retention declines, engagement decline, `other`-funnel point estimates, 88% chooser leak, repeating-paywall confound, "forcing destroys best segments" (min-song), maturity gate |
| 788614610 | Primary Confluence | v17 | Instrumentation limits (registry-scoped attribution); "Forcing tab display worsens results — verified in experiment 7256, iteration 1" |
| `workspace/final/official-tabs-banner-shaping.md` | **Secondary reviewed synthesis** | accepted 2026-07-15 | Cross-checking and source routing only — consequential facts cite the primary pages above |
| Prototype visuals; Slack images F0BH2AH8524, F0BJ9NMQQ0Y; Figma frames | **Not inspected** | — | Excluded from evidence; confirm with the colleague before use |

**Unresolved identity (not asserted):** 815603200 attributes the tracking-string failure to "experiment 7577 (First Session Flow, iteration 3)," while 777817235 v144 and the accepted synthesis identify iteration 3 as **#7622**. The event-string lesson (a spec value shipped two ways, splitting one funnel) is a claim made *by 815603200* and a good implementation caution; the experiment identity is **unverifiable** here until an authoritative spec or analytics record resolves 7577 vs 7622.

---

## Resolution log — Codex review (READY WITH CHANGES; 0 blockers, 1 major, 3 minor)

Review: [`workspace/reviews/codex/official-tabs-process-recovery-review.md`](../reviews/codex/official-tabs-process-recovery-review.md). This is the second Codex pass; the first (NOT READY) was resolved by adding the exact Slack source and rebuilding §1. All findings from this pass are accepted; no source-backed disagreements.

| Finding | Resolution |
|---|---|
| **MAJOR 1** — component-level causal claim that Variation B's repeating loop harms retention | **Accepted.** §3 and the RU reply now state that Variation B's **whole multi-part treatment** caused the significant retention declines (1d/7d/14d, p<0.001) and that the repeating loop is a **plausible but unisolated** contributor. The voluntary selector preview is reframed as a **precaution** consistent with adjacent forcing risks, not a proven remedy for B's retention mechanism. |
| **MINOR 1** — forcing evidence miscited and over-generalized | **Accepted.** The exact "Forcing tab display worsens results — verified in experiment 7256, iteration 1" sentence is now cited to **788614610 v17**; the "forcing destroys best segments" / minimum-song evidence to **777817235 v144**. Conclusion narrowed to "forced flows have shown risk in adjacent first-session contexts," with a note that neither precedent directly tests a forced feature tutorial. Source ledger updated. |
| **MINOR 2** — unbounded absence claims | **Accepted.** The executive answer now reads "neither branch is approved for build **in the retrieved threads**" and "the **retrieved thread** contains no reply agreeing to remove the free Community versions." Item 6 in §1 similarly bounded. |
| **MINOR 3** — "the evidence settles the one substantive question" contradicts the open content question | **Accepted.** Replaced with "the evidence settles the research-claim dispute while clarifying what remains open." |
