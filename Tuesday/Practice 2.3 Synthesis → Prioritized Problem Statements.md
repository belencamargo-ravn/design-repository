# Micro-Practice 2.3: Synthesis → Prioritized Problem Statements

## Part 1: Theme Traced to Source (Theme #1 Audit)

### Audited Theme:
**People trust a personal recommendation from someone they know more than they trust a platform's rating or background check. But this only holds up to a point: for high-stakes situations like childcare, or when no one is available to vouch for someone, people actively want real verification instead.**

* **Verbatim Supporting Quotes & Participant IDs**:
  * **P01 (Requester), mid-interview**: *"If you gave me the choice between a man with a certificate who I've never seen before and a man with no certificate who Priya has used for two years, I'm taking Priya's man. Every time."*
  * **P01 (Requester), closing**: *"Stars are meaningless, everyone's four point eight. Tell me Priya used him eleven times. That's the whole product, isn't it."*
  * **P02 (Requester), mid-interview**: *"Denise vouched for her. That's the check... It's a person taking responsibility, that's not the same as a company saying trust us."*
  * **P05 (Provider), mid-interview**: *"That's my reputation, that took twenty years. I'm not lending it to a stranger."*
  * **P06 (Community Admin), opening**: *"Somebody who lives here has to have used them and said they were good. That's the rule. I don't put anyone on it because they asked me to."*

* **Contradicting / Complicating Evidence**:
  * **P02 (Requester), closing statement**: His own final answer contradicts the theme's headline. When asked what he wants most, he says: *"Proper vetting. Real checks, real ID, real references, and don't let people on without it. If you did that I'd use it tomorrow, honestly, and I'd pay more for it."* He only trusts a personal vouch when one already exists: *"I suppose the checks are for when you don't have a Denise."* In other words, he doesn't reject formal checks. He wants them as a backup, and as his top priority once the stakes are higher (childcare).
  * **P01 (Requester)**: Under time pressure, he did the opposite of what he said he preferred. He booked a childcare sitter through an app based on reviews alone, having never met her: *"Nothing changed, I was just desperate."*
  * **P03's household (Requester, via her daughter)**: With no one locally to vouch for a provider, the daughter falls back on the exact thing the theme says people distrust: *"I mostly just search and read reviews and go with a gut feeling."* This example actually works against the theme, not for it.
  * **P06 (Community Admin)**: Relying only on personal vouches has a real downside. It excludes good people the admin simply doesn't happen to know: *"The list is a bit of a closed shop... the people I don't know are almost always the ones who moved in recently."*

* **How strong is this evidence?**: The theme holds up clearly for 3 of 6 people interviewed (P01, P05, P06). P02 is a mixed case: he trusts a personal vouch for his cleaner, but names formal background checks as his top priority for childcare. P03's household is actually an example against the theme, not an example of it. P04 doesn't talk about vouches versus checks at all. So the real, honest version of this theme is: a personal vouch is the preferred signal for everyday, lower-stakes needs, but people actively want formal verification once the stakes go up, or when nobody is around to vouch for someone.

* **What this means for the product (data we'd need to track)**:
  * **A "Vouch"**: a record of one person recommending a provider to someone else. Needs to capture who is vouching, who they're vouching for, how they know them, when, whether it's still active, and whether the admin's name is shown or hidden (P06 wants to stay anonymous when she turns someone down).
  * **A "Verification"**: a formal check on a provider, separate from a vouch. Needs to capture the type of check (ID, background check, reference, insurance), who ran it, the date, and whether it's still valid. This is the fallback path P01 and P02 both described, and P02's top request.
  * **A "Connection"**: a simple record of who knows whom. This is needed to tell whether a vouch comes from someone the requester actually recognizes, since P02 says a vouch from a name he doesn't recognize "is nothing."
  * **A "stakes level" on each service type**: something as simple as marking dog walking as lower-stakes and childcare as higher-stakes. Both P01 and P02 change how much proof they need depending on the category.

---

## Part 2: Three Prioritized Problem Statements (No Solutions)

### 1. Problem 1 (Highest Impact: Requester Role)
* **Who**: Vello Requesters, especially newcomers and parents evaluating providers for higher-stakes tasks like childcare or home access (P01, P02, P03's daughter).
* **What**: Requesters can't tell whether an unfamiliar provider is trustworthy enough to hand over house keys or be left alone with their children, because the signals they have access to (star ratings, reviews, generic vetting badges) don't answer the question they actually have.
* **Why**: Getting this decision wrong carries real, sometimes irreversible risk. So requesters either stall on booking, fall back on a small and often accidental personal network, or make a high-stakes decision under time pressure that goes against their own stated standards.

### 2. Problem 2 (Medium Impact: Requester and Community Admin Roles)
* **Who**: Requesters without an existing local network, such as newcomers, isolated older residents, and family members managing services on someone else's behalf, along with the Community Admin who decides who gets vouched for (P02, P03, P03's daughter, P06).
* **What**: People who haven't yet built local relationships have no way into the personal-vouch system everyone else relies on, no matter how long they've lived somewhere or how much they need the service. At the same time, the admin has no way to evaluate a recommendation from someone she doesn't personally know.
* **Why**: Because trust here only moves between people who already know each other, the residents who know the fewest people (the newly arrived, the isolated, the elderly) are the ones most likely to get overcharged or underserved. Meanwhile, legitimate new providers wait months longer to be recognized, for no reason related to the quality of their work.

### 3. Problem 3 (Medium Impact: Provider and Community Admin Roles)
* **Who**: Independent Providers who rely on word-of-mouth for new clients (P04, P05), and the Community Admin who processes those recommendations on the community's behalf (P06).
* **What**: Providers can't get new clients on demand or fill gaps in their schedule, and the admin can't process new provider requests as fast as people expect, because the only trusted channel (a personal recommendation) moves at the speed of relationships, not the speed of business or admin work.
* **Why**: Since both growth and approval depend on someone already known vouching for a newcomer, providers deal with unpredictable, unpaid income gaps, and the admin spends hours each week on unpaid manual verification work, with no way to tell a strong unfamiliar recommendation from a weak one.