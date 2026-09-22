# Practice 1.2: Teach the Vocabulary Back

2026-09-21 · @Belen Camargo

## 1. Weak Spots Identified (My 2 Tricky Scenarios)

- **Scenario 1 (Payment failure error message: "Insufficient funds" vs. generic "Payment failed")**
  - **My Answer**: UX category, Design owns it outright.
  - **Claude's Correction**: Category (UX) was right — this is microcopy/content strategy. Ownership was wrong: it should be **Co-owned**, because payment processors and card networks often restrict which decline reasons can be surfaced to users, and revealing specific reasons like "insufficient funds" is a known vector for card-testing fraud. That's a compliance/risk constraint, not a wording preference.
  - **Ownership Takeaway**: Design owns *how* the message is worded; PM/compliance owns *what's allowed to be disclosed at all* in a payment flow specifically.
- **Scenario 2 (App-wide button corner radius: sharp vs. rounded, as part of a design-system rollout)**
  - **My Answer**: UI category, Co-owned.
  - **Claude's Correction**: Category (UI) held up. Ownership was over-called — I justified "Co-owned" with an unverified claim ("could affect conversion") rather than any actual data, legal exposure, or committed roadmap cost. That's the wrong test for pulling in a PM.
  - **Ownership Takeaway**: A systemized style-token change with no *proven* business impact stays with **Design** alone — "could theoretically matter" isn't enough to trigger co-ownership, or nearly everything would qualify.

## 2. Key Vocabulary Rules Re-anchored

- **Product Design**: The "should we build this, and under what rules?" layer — business model, monetization, funnel/data strategy, legal or trust-and-safety exposure. Owned by PM because it requires weighing revenue and risk trade-offs Design isn't mandated to own.
- **UX**: Structure and flow — how information is organized and how a user moves through a task, independent of how it's rendered on screen. The test: would this decision hold even in a wireframe with no visual styling at all?
- **UI**: The component/system layer — how interactive elements are built and standardized across the app (buttons, cards, layout patterns, design-system components). Sits between structure (UX) and pure styling (Visual Design).
- **Visual Design**: Styling and rendering tokens — color, typography, iconography, spacing — with no change to structure, flow, or interaction logic.

**The ownership test that actually works**: a decision needs a PM (i.e., is Co-owned, not Design-only) when there is *proven* business impact (real data, not a hunch), a legal/compliance constraint, or a committed roadmap/resource cost attached — not merely because the change is visible, emotionally significant, or *could* theoretically matter.

## 3. Quiz Transcript / Chat Link

This doc summarizes an 8-scenario quiz run in a Claude chat, using a hyperlocal services app (think: cleaners, handymen, tutors, pet sitters) as shared context. Each scenario asked for a category (Product Design / UX / UI / Visual Design), an owner (PM / Design / Co-owned), and open-ended reasoning, with Claude revealing the verdict only after each full answer.

**Scorecard**

- Category: 8/8 correct
- Ownership: 4/8 correct
- Most-confused category: none misidentified outright — the miss was consistently in the *ownership* call, not the category call
- Pattern in mistakes: an inconsistent evidentiary bar for "does this need a PM." Errors ran in both directions — under-calling ownership when a compliance/data-risk angle was missed (payment error copy), and over-calling ownership on speculative grounds without real data, legal exposure, or roadmap cost (corner radius, map view). The fix: ask "what's the *evidence* this needs a PM?" rather than "does this feel important?"

*Full scenario-by-scenario transcript available in the original Claude conversation.*
