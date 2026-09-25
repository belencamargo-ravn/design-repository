# The Design-Ready Brief & Final Package

This document traces the Vello vouching brief across every version it went through: the true first draft (Practice 5.1/5.2), the version Claude's critique corrected, the design-ready spec built from that correction, the Claude Design prototype that tested it, and the final brief that closed the gaps the prototype exposed. Every quoted brief below is unedited — nothing inside a blockquote has been changed. Everything outside the quotes (the at-a-glance breakdowns, the gap tables, this sentence) is added commentary.

---

## Stage 1: Initial Draft Brief

> Vouching replaces star ratings in Vello. Research found that stars carry no weight with requesters ("everyone's four point eight," P01). What they want to know is which neighbors they know have actually used someone ("Tell me Priya used him eleven times"). Two kinds of people can vouch for a provider: requesters (only after they've completed a booking with that provider through Vello) and the community admin, whose vouch counts the same as anyone else's but is labeled as coming from the admin. Each vouch shows the voucher's name, and the voucher can withdraw it at any time. On provider cards and profiles, vouches replace stars completely. Vouches from neighbors the requester knows come first, then vouches from other neighbors in the area.

### At a Glance (not part of the original brief)

| | |
|---|---|
| **Who** | Requesters, providers, and the community admin in Vello |
| **What** | Replace star ratings with a vouching system |
| **Why** | Stars carry no weight with requesters |
| **Evidence** | "everyone's four point eight" (P01); "Tell me Priya used him eleven times" |
| **Goal** | Not stated in this draft |
| **Constraints** | Not stated in this draft |

---

## Stage 1 Review: Gaps Claude Found

> 1. Every sentence after the first quote is a design decision.
> 2. Vouching removes negative signal entirely.
> 3. How does Vello know who I know? Contacts import? Mutual follows? Street proximity?
> 4. Every provider launches with zero vouches.
> 5. Does the admin need a completed booking too? If not, she's the only one exempt, which contradicts "counts the same as anyone else's."
> 6. Withdrawing a vouch for someone you see at the shop is socially expensive.
> 7. A vouch doesn't say what it vouches for.

### Decisions Made in Response

> | Gap | Decision | Status |
> |---|---|---|
> | **2 + 6** | Requesters see how many neighbors vouched for a provider. If any vouchers are in the requester's personal network, the requester can see all of them by name. Everyone else is shown as a count only. Providers can't see who vouched. | Decided; how it's shown is up to design |
> | **3** | How Vello knows who you know belongs to the "network of known people" feature. | Dependency, separate scope |
> | **4 + 5** | New providers get a limited window in which established requesters can vouch for them without a completed booking. "Established" means meeting minimum requirements (time on Vello, completed bookings). After the window, only completed bookings count. The admin follows the same rule as any requester. | Decided; window length and thresholds to be defined |
> | **7** | A vouch is tied to a specific service (e.g. dog walking), not to the provider in general. | Decided |

### Accepted Risks and Limitations

> - Requesters with no network see only the count. We ship it and revisit if it causes problems.
> - Established requesters may vouch under social pressure or as a favor to a friend. This is subjective and we won't try to prevent it.

---

## Stage 2: Corrected Brief

> In Kestrel Park, people decide who to let into their homes, near their children or near their keys based on the word of someone they already trust, not on star ratings, reviews from strangers or platform background checks. "Stars are meaningless, everyone's four point eight. Tell me Priya used him eleven times," as one requester put it. Vello's current prototype leads with exactly the signals people discount. As a result, requesters can't tell whether a provider is someone they'd trust, and they go back to WhatsApp groups and asking neighbors in person, which puts Vello's core promise of trusted local help at risk. The problem to solve is how to carry a personal recommendation into Vello, so requesters can see how people they know have experienced a provider. Standing is earned by using a provider, either through a completed booking or, during a limited window for new providers, through requesters who have an established record on Vello. The community admin follows the same rules as everyone else. This brief depends on a separate "network of known people" feature. It doesn't cover newcomer onboarding, referrals between providers, admin tools or background checks. We accept that requesters with no network will get a weaker signal, and that some vouches will be given as favors; both will be reviewed after launch. The window length and the thresholds for "established" are still to be defined. We'll know it works when requesters in a usability test choose a provider based on neighbors' experience instead of looking for a rating.

### At a Glance (not part of the corrected brief)

| | |
|---|---|
| **Who** | Requesters and the community admin |
| **What** | Vouching earned through completed bookings, or through established requesters during a new-provider window |
| **Why** | Same as Stage 1: stars carry no trust weight |
| **Evidence** | Same quotes, now folded into a single problem narrative |
| **Goal** | Requesters in a usability test choose a provider by neighbors' experience, not a rating |
| **Constraints** | Depends on the "network of known people" feature; excludes onboarding, referrals, admin tools, background checks |

*Note: this version ties a vouch to the provider in general, while the Stage 1 decision table above ties it to a specific service. This particular detail shifts again by Stage 4 (see below) — a reminder that "corrected" doesn't mean "final."*

---

## Stage 3: Design-Ready Brief

> ## Problem
> In Kestrel Park, people decide who to let into their homes, near their children or near their keys based on the word of someone they already trust, not on star ratings, reviews from strangers or platform background checks. "Stars are meaningless, everyone's four point eight. Tell me Priya used him eleven times," as one requester put it. Vello's current prototype leads with exactly the signals people discount. As a result, requesters can't tell whether a provider is someone they'd trust, and they go back to WhatsApp groups and asking neighbors in person, which puts Vello's core promise of trusted local help at risk.
>
> The problem to solve is how to carry a personal recommendation into Vello, so requesters can see how people they know have experienced a provider.
>
> ## Definitions
> - **Vouch:** a requester's public statement that they'd recommend a provider. A vouch is always positive; there is no negative vouch.
> - **How a vouch is earned:** (a) after at least one completed booking with that provider, or (b) an early vouch, allowed only during the new-provider window and only from established requesters.
> - **Established requester:** [DEFINITION TBD]. Until it's defined, show early vouches only; don't design an eligibility check or a "not eligible" screen.
> - **New-provider window:** [LENGTH TBD]. Show it as a placeholder in the UI.
>
> ## UI requirements
> Must show
> - On provider cards and profiles: the people you know who vouched, by name, and how each vouch was earned ("booked 11 times" or "early vouch").
> - For vouches from people outside your network: a count only, never names.
> - Allowed trust signals: vouches and completed-booking counts. Nothing else.
>
> Must not show
> - Star ratings, review counts or review text, anywhere in the flow.
> - Any badge, label or extra weight for the community admin; admins appear like every other neighbor.
> - Background checks or platform-verification badges.
>
> Screens in scope
> 1. Browse: providers vouched for by people you know come first.
> 2. Provider profile: the vouches from people you know come before any other content.
> 3. Vouch detail: how one person you know has used this provider.
> 4. Vouching: offered after a completed booking. The requester chooses whether to vouch; a booking doesn't create a vouch automatically.
> 5. Confirmation after vouching: [DECIDE: a confirmation message only, or a preview of how the vouch appears to others].
>
> States to cover
> - Loading, the network failing to load, a requester with no network, and a new provider with no bookings.
>
> ## Scope
> Depends on the separate "network of known people" feature. Doesn't cover newcomer onboarding, referrals between providers, admin tools, background checks or the booking flow itself.
>
> ## Accepted risks
> Requesters with no network get a weaker signal, and some vouches will be given as favors; both will be reviewed after launch.
>
> ## Success
> In a usability test, requesters choose a provider based on neighbors' experience, with no rating available to look for.

### At a Glance (not part of the design-ready brief)

| | |
|---|---|
| **Who** | Requesters in Kestrel Park (providers and the community admin are affected but not the primary audience) |
| **What** | A fully specced vouching system: definitions, must-show/must-not-show UI rules, five screens in scope, and states to cover |
| **Why** | Same as Stage 2 |
| **Evidence** | Same as Stage 2 |
| **Goal** | Same as Stage 2 |
| **Constraints** | Same dependency and out-of-scope list as Stage 2 |

---

## Prototype Test: Validating the Design-Ready Brief

**Prototype**: [Vello vouching feature, built by Claude](https://claude.ai/artifact/UdDVoLfERGRK545z5kQVtr?sk=2hoZsgi8Mj-ByiZuxtHN1g)
**Incompleteness score**: 4 (full write-up in [Practice 5.3](Practice%205.3%20Prototype%20as%20a%20Brief%20Test.md))

Building this brief into a real prototype forced four UI decisions the brief hadn't made, and confirmed nine decisions it had made correctly.

---

## Gaps Exposed and How They Were Closed

| # | Gap the prototype exposed | How the Stage 4 brief closes it |
|---|---|---|
| 1 | Claude invented a rule for who counts as an "established requester" and showed a "you can't vouch yet" screen with no stated basis. | `Established requester` stays an explicit `[TBD]` placeholder, now with the instruction "Don't invent a definition; use the placeholder." The eligibility question becomes **Open Question #4**: "How might requesters tell an early vouch apart from one earned through bookings, without making early vouches feel second-class?" |
| 2 | Star ratings and reviews were still shown, despite the brief's "Must not show" list. | Elevated from a bulleted "must not show" item to a standalone **Constraint**: "No star ratings, review counts or review text anywhere in this experience." |
| 3 | A booking-count badge appeared, which wasn't explicitly requested. | Not actually a gap: the Stage 3 brief already allowed "vouches and completed-booking counts" as trust signals, and booking counts are also how a vouch is earned ("booked 11 times"). Kept intentionally. |
| 4 | The post-vouch confirmation screen showed a card whose purpose wasn't explained. | The Stage 3 brief had already flagged this as undecided (`Confirmation after vouching: [DECIDE...]`). The Stage 4 brief drops the prescriptive "screens in scope" list and turns it into **Open Question #2**: "What's the lightest way to capture a satisfied requester's recommendation after a completed booking without interrupting their day, or should a completed booking speak for itself?" |

The pattern across both critique rounds is the same: wherever the brief tried to pre-decide something that wasn't actually settled, the prototype either invented an answer no one approved or exposed a UI dead end. Each fix below replaces a premature decision with an explicit placeholder or open question.

---

## Stage 4: Final Corrected Brief

> ## Problem
> In Kestrel Park, people decide who to let into their homes, near their children or near their keys based on the word of someone they already trust, not on star ratings, reviews from strangers or platform background checks. "Stars are meaningless, everyone's four point eight. Tell me Priya used him eleven times," as one requester put it. Vello's current prototype leads with exactly the signals people discount. As a result, requesters can't tell whether a provider is someone they'd trust, and they go back to WhatsApp groups and asking neighbors in person, which puts Vello's core promise of trusted local help at risk.
>
> The problem to solve is how to carry a personal recommendation into Vello, so requesters can see how people they know have experienced a provider.
>
> ## Definitions
> - **Vouch:** a requester's positive recommendation of a provider. There is no negative vouch.
> - **How a vouch is earned:** (a) after a completed booking with that provider, or (b) an early vouch, allowed only during the new-provider window and only from established requesters.
> - **Established requester:** [TBD]. Don't invent a definition; use the placeholder.
> - **New-provider window:** [LENGTH TBD].
>
> ## Constraints
> - No star ratings, review counts or review text anywhere in this experience.
> - Requesters see names only for vouchers in their own network; vouches from anyone else appear as counts, never names.
> - The community admin follows the same rules and gets no badge, label or extra weight.
> - Relies on the separate "network of known people" feature for who knows whom.
> - Out of scope: newcomer onboarding, referrals between providers, admin tools, background checks, the booking flow itself.
>
> ## Open questions for design exploration
> 1. How might we make the experience of people I know the first and strongest thing I see about a provider?
> 2. What's the lightest way to capture a satisfied requester's recommendation after a completed booking without interrupting their day, or should a completed booking speak for itself?
> 3. How might we present a new provider with few or no vouches so they aren't unfairly penalized?
> 4. How might requesters tell an early vouch apart from one earned through bookings, without making early vouches feel second-class?
> 5. What should a requester with no network yet see, so the weaker signal is still useful and honest?
>
> ## Accepted risks
> Requesters with no network get a weaker signal, and some vouches will be given as favors; both will be reviewed after launch.
>
> ## Success
> In a usability test, requesters choose a provider based on neighbors' experience, with no rating available to look for.

### At a Glance (not part of the final brief)

| | |
|---|---|
| **Who** | Requesters in Kestrel Park |
| **What** | Same core problem, but every unresolved rule is now an explicit placeholder or open question instead of a spec Claude has to guess at |
| **Why** | Unchanged: star ratings carry no trust weight |
| **Evidence** | Unchanged: "Tell me Priya used him eleven times" |
| **Goal** | Unchanged: requesters choose a provider by neighbor experience, not rating |
| **Constraints** | Same dependency and out-of-scope list as Stage 3, restated as explicit constraints rather than a mixed "must/must not show" list |

---

## Final Prototype: Validating the Final Brief

**Prototype**: [Vello vouching feature, final version, built by Claude](https://claude.ai/artifact/Cfx5mAbHiVxDiKwsD9EcYD?sk=FnoD4GepzcnhWhgqMsOtVw)

Built from the Stage 4 brief above. Where the Stage 3 prototype had to invent answers to unstated rules, this one had explicit placeholders and open questions to work from instead of gaps to fill in silently.
