# PM Touchpoints in the Design Process

A phase-by-phase reference for where a PM adds measurable value to design work, where PMs commonly overstep or leave gaps, and the concrete artifact each is tied to.

---

## 1. Overview by Phase

| Phase | PM Contribution (Value-Add) | PM Failure Mode (Overstepping/Gaps) | Tied Artifact |
| :--- | :--- | :--- | :--- |
| **Discover** | Share raw user interviews and quantitative drop-off metrics to ground problem discovery. | Asking leading questions or pushing pet feature solutions during user research. | User Research Brief / Drop-off Analytics |
| **Define** | Frame clear, un-solutionized problem statements and business success metrics. | Supplying a solution-shaped brief (e.g., "add a tipping button") instead of defining the problem. | Problem Statement / Brief |
| **Architect** | Define business logic constraints, edge-case rules, and user role permissions early. | Prescribing specific screen navigation patterns (e.g., "put it in a hamburger menu") before IA is agreed. | System Rules / Spec |
| **Design** | Provide feedback anchored in user outcomes and trade-offs rather than aesthetic taste. | Giving directive visual feedback ("make this button persimmon") instead of asking goal-framed questions. | Critique Log |
| **Validate & Hand-off** | Align on acceptance criteria and success metrics for rollout and post-launch measurement. | Skipping edge-case validation and rushing directly from prototype to engineering build. | Acceptance Criteria / PRD |

**The throughline:** nearly every failure mode above is the same move — a PM collapsing a phase's artifact into something that already contains the answer, one phase too early. The fix at each stage is the same: write down the target and the bounds, not the solution.

---

## 2. Concrete Artifact Examples

Each example below is a fully worked artifact for a specific, real scenario — not a template with placeholders for "your problem here."

### 2.1 Discover — Discovery Brief

**Context:** Onboarding funnel drop-off, roadmap review in 3 weeks where a Q3 bet recommendation is due.

```
DISCOVERY BRIEF — Onboarding Drop-off
Owner: [PM name]
Date: [date]
Decision deadline: Q3 Roadmap Review, [date, 3 weeks out]

Decision this research must unblock:
Do we (a) redesign the full onboarding flow, (b) fix the specific
step-3 drop-off, or (c) leave onboarding alone and prioritize something
else for Q3? A recommendation with evidence is due at the roadmap
review above — "more research needed" is not an acceptable outcome
at that meeting.

Questions the research must answer:
1. Where exactly in step 3 do users drop — is it the form itself,
   a specific field, load time, or something upstream (e.g., they
   arrived with the wrong expectation from step 1)?
2. Is the drop-off concentrated in a segment (device, acquisition
   channel, account type) or evenly distributed?
3. Do users who drop at step 3 come back later through another path,
   or are they gone for good? (This determines if it's a "fix the
   step" problem or a "we're losing these people" problem.)

Method and scope (fixed to fit the deadline):
- Funnel + session replay analysis: 1 week
- 6 moderated usability sessions with users who dropped in the last
  30 days: 1 week
- Synthesis + recommendation memo: 3 days
Total: fits inside the 3-week window. No open-ended generative research
add-ons without renegotiating the deadline.

Explicitly out of scope for this brief:
- Broader "how do users feel about onboarding overall" sentiment work
- Competitive benchmarking of other products' onboarding
(Both are legitimate questions — just not this one, not on this clock.)

What "done" looks like:
A memo that names which of the three options (a/b/c) the evidence
supports, with the data behind it, ready to present at the roadmap
review.
```

**What this changes:** without a brief like this, "research onboarding" tends to expand — a survey gets added, someone wants power-user interviews too — and three weeks later there's interesting sentiment data but no answer to the actual decision on the table. With the brief, every method traces back to one of the three numbered questions, which trace back to the a/b/c decision, which has a date. Anything that doesn't serve that chain gets cut or explicitly deferred.

---

### 2.2 Define — Problem Statement

**Context:** Coming out of the discovery brief above; the artifact design will actually work from.

```
PROBLEM STATEMENT — Onboarding Step 3 Drop-off
Owner: [PM name]
Date: [date]
Source: Funnel analysis, [date range], n=[X] sessions;
        6 usability sessions, [date range]

Baseline (measured, not impression):
23% of new users who reach step 3 ("connect your data source") abandon
the flow at that step, measured over the last 90 days of funnel data.
This is up from 14% two quarters ago, coinciding with the addition of
the OAuth permission screen.

Where it breaks (from research, not speculation):
- 68% of drop-offs occur specifically at the OAuth permission screen,
  not the data-source picker before it or the confirmation after it.
- Session replay shows median time-on-screen of 47 seconds before exit
  — consistent with users reading the permission list and bailing,
  not a load-time or technical failure.
- Usability sessions (n=6) surfaced a specific reason: users don't
  understand why the product needs "read access to all files," and
  three of six said this explicitly before abandoning in the test.

What this is NOT (ruling out competing explanations):
- Not a device or channel-specific problem — drop-off rate is within
  2pp across mobile/desktop and all acquisition channels.
- Not a returning-later problem — of users who drop here, only 4%
  come back and complete onboarding within 30 days. This is a loss,
  not a delay.

Baseline this design must move:
Reduce step-3 abandonment from 23% to below 15% (pre-OAuth-screen
baseline), measured over the first 90 days post-launch.

Explicitly not the problem statement:
"Users need a clearer OAuth screen" — that's a solution, not the
problem. The problem is the gap between what access we're requesting
and what the user understands about why. The solution space is open:
narrower scoped permissions, better explanation copy, progressive
disclosure of why each permission is needed, or something else.
```

**What this changes:** design now has a number to beat (23% → 15%), evidence for where and why it breaks, and a guardrail against the most tempting shortcut — jumping straight to "make the OAuth screen nicer" before the actual mechanism (users don't understand the permission ask) has been addressed. If the eventual design ships and step-3 abandonment is still 22%, that's an unambiguous miss against this doc, not a debate about whether it "feels better now."

---

### 2.3 Architect — Constraints Doc

**Context:** Redesigning the seller inventory dashboard, delivered before IA/wireframe work starts.

```
CONSTRAINTS — Seller Inventory Dashboard Redesign
Owner: [PM name]
Date: [date, before IA work begins]
Applies to: IA and structural decisions only (not visual design)

1. Latency: inventory counts are read from the legacy warehouse API,
   which has a 200ms average / 800ms p99 response time. Any structure
   that requires this data to update live on scroll or on every filter
   change will feel laggy. Structures that batch/paginate reads are
   preferred; structures that imply real-time reactivity are not viable
   without a caching layer we have not scoped or funded.

2. Data retention: per legal, we cannot display or retain
   customer-linked order history beyond 30 days in this view. Any
   structure that implies a "full order history" tab or long-range
   trend view for a given customer is out of scope for this release.

3. Bulk actions: the legacy API supports batch updates up to 200 SKUs
   per call. A structure that implies "select all 10,000 SKUs and
   bulk-edit" will fail silently past 200 — either the IA needs to
   chunk this explicitly or set a hard selection cap with messaging.

4. Permissions: three roles (owner, manager, staff) with different
   write access to pricing fields. The IA needs to account for
   role-gated states per screen, not just one canonical layout with
   fields hidden/shown after the fact.

5. Platform: must work inside the existing left-nav shell used by
   4 other dashboard sections. This is not up for revisiting in this
   project — it's a fixed frame, not a structural choice.

Out of scope for this doc: color, type, spacing, visual hierarchy —
covered separately.
```

**What this changes:** without this doc, a designer might reasonably architect a real-time-updating table with a "select all" bulk-edit and a full customer order history panel — all of which look correct on a whiteboard and all of which break against constraints 1, 2, and 3 respectively. Catching that after wireframes exist means re-architecting, not refining. Catching it here means the IA is built against what's actually buildable.

---

### 2.4 Design — Acceptance Criteria

**Context:** Password reset flow, handed to the designer before they open a design tool.

```
ACCEPTANCE CRITERIA — Password Reset Flow
Attached to: FIGMA-482
Owner: [PM name]
Date: [date]

1. Time to completion: median user resets password in under 60 seconds,
   from clicking "Forgot password" to landing back in the authenticated app.
2. First-try success: 90% of users in usability testing (n=10) complete
   the flow without needing to restart or ask for help.
3. Error recovery: if the user enters an invalid/expired reset code, the
   screen must tell them what went wrong and offer a next step, not just
   "Error." Zero dead ends.
4. Steps: no more than 4 screens/states between "Forgot password" and
   "successfully logged in," including the email step.
5. Out of scope: we are not redesigning the login screen itself, only
   the reset flow reached from it.
```

**What this changes:** when the designer returns with a 6-screen flow that adds an email-verification step and a security-question step, the review isn't "I feel like this is too many steps" — it's "criterion 4 says 4 screens max, this is 6, which two are we cutting." Same with a generic "invalid code" error screen — it's a direct miss on criterion 3, not a taste call. It constrains the PM too: adding a step later (e.g., 2FA) means consciously editing the doc and explaining why criterion 4 no longer holds, not just adding scope in a comment thread.

---

### 2.5 Validate — Pre-Registered Success Threshold

**Context:** New single-page checkout flow, replacing a 3-step checkout, registered before the A/B test launches.

```
PRE-REGISTERED SUCCESS CRITERIA — Single-Page Checkout Test
Experiment ID: EXP-1147
Owner: [PM name]
Date registered: [date, before launch]
Test launch date: [date]

1. Primary metric: checkout conversion rate (sessions that reach
   "order confirmed" / sessions that reach checkout start).
2. Ship threshold: variant beats control by ≥2 percentage points,
   with a 95% confidence interval that excludes zero.
3. Sample size / power: minimum 15,000 sessions per arm, calculated
   to detect a 2pp lift at 80% power. Test will not be called before
   this is reached, regardless of interim results.
4. Guardrail metrics (must not regress beyond noted tolerance):
   - Refund/dispute rate: no increase >0.5pp
   - Average order value: no decrease >3%
   - Support tickets tagged "checkout": no increase >10%
5. Decision rule locked in advance:
   - Primary metric hits threshold AND all guardrails hold → ship
   - Primary metric hits threshold but a guardrail breaks → escalate
     to [name], do not unilaterally ship
   - Primary metric misses threshold → do not ship, regardless of
     how "close" or how compelling anecdotal feedback is
6. Who can override this doc post-hoc: nobody, without a written
   justification appended here and dated after the fact.
```

**What this changes:** three weeks in, the variant is up 1.3pp with support tickets down — someone will want to call it a win because "it's basically there." The doc says no — 1.3pp doesn't clear the 2pp bar, and "people love it" was never a pre-registered metric. Without the doc, that's a judgment call made under deadline pressure by whoever's most persuasive in the room. With it, it's just checking a number against a line committed to before there was a reason to want a particular answer. The date-stamping matters as much as the content — a threshold written the same afternoon the results come in isn't a threshold, it's a rationalization with a template.

---

## 3. Practice 1.3: Touchpoints Table

| Phase | PM Contribution (Value-Add) | PM Failure Mode (Overstepping/Gaps) | Tied Artifact |
| :--- | :--- | :--- | :--- |
| **Discover** | Share raw user interviews and quantitative drop-off metrics to ground problem discovery. | Asking leading questions or pushing pet feature solutions during user research. | User Research Brief / Drop-off Analytics |
| **Define** | Frame clear, un-solutionized problem statements and business success metrics. | Supplying a solution-shaped brief (e.g., "add a tipping button") instead of defining the problem. | Problem Statement / Brief |
| **Architect** | Define business logic constraints, edge-case rules, and user role permissions early. | Prescribing specific screen navigation patterns (e.g., "put it in a hamburger menu") before IA is agreed. | System Rules / Spec |
| **Design** | Provide feedback anchored in user outcomes and trade-offs rather than aesthetic taste. | Giving directive visual feedback ("make this button persimmon") instead of asking goal-framed questions. | Critique Log |
| **Validate & Hand-off** | Align on acceptance criteria and success metrics for rollout and post-launch measurement. | Skipping edge-case validation and rushing directly from prototype to engineering build. | Acceptance Criteria / PRD |