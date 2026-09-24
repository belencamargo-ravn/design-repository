# Practice 5.2: Let Claude Attack Your Brief

---

## Initial Draft Brief

Vouching replaces star ratings in Vello. Research found that stars carry no weight with requesters ("everyone's four point eight," P01). What they want to know is which neighbors they know have actually used someone ("Tell me Priya used him eleven times"). Two kinds of people can vouch for a provider: requesters (only after they've completed a booking with that provider through Vello) and the community admin, whose vouch counts the same as anyone else's but is labeled as coming from the admin. Each vouch shows the voucher's name, and the voucher can withdraw it at any time. On provider cards and profiles, vouches replace stars completely. Vouches from neighbors the requester knows come first, then vouches from other neighbors in the area.

---

## Gaps Claude Found

1. Every sentence after the first quote is a design decision.
2. Vouching removes negative signal entirely.
3. How does Vello know who I know? Contacts import? Mutual follows? Street proximity?
4. Every provider launches with zero vouches.
5. Does the admin need a completed booking too? If not, she's the only one exempt, which contradicts "counts the same as anyone else's."
6. Withdrawing a vouch for someone you see at the shop is socially expensive.
7. A vouch doesn't say what it vouches for.

---

## Decisions

| Gap | Decision | Status |
|---|---|---|
| **2 + 6** | Requesters see how many neighbors vouched for a provider. If any vouchers are in the requester's personal network, the requester can see all of them by name. Everyone else is shown as a count only. Providers can't see who vouched. | Decided; how it's shown is up to design |
| **3** | How Vello knows who you know belongs to the "network of known people" feature. | Dependency, separate scope |
| **4 + 5** | New providers get a limited window in which established requesters can vouch for them without a completed booking. "Established" means meeting minimum requirements (time on Vello, completed bookings). After the window, only completed bookings count. The admin follows the same rule as any requester. | Decided; window length and thresholds to be defined |
| **7** | A vouch is tied to a specific service (e.g. dog walking), not to the provider in general. | Decided |

---

## Accepted Risks and Limitations

- Requesters with no network see only the count. We ship it and revisit if it causes problems.
- Established requesters may vouch under social pressure or as a favor to a friend. This is subjective and we won't try to prevent it.

---

## Corrected Brief

In Kestrel Park, people decide who to let into their homes, near their children or near their keys based on the word of someone they already trust, not on star ratings, reviews from strangers or platform background checks. "Stars are meaningless, everyone's four point eight. Tell me Priya used him eleven times," as one requester put it. Vello's current prototype leads with exactly the signals people discount. As a result, requesters can't tell whether a provider is someone they'd trust, and they go back to WhatsApp groups and asking neighbors in person, which puts Vello's core promise of trusted local help at risk. The problem to solve is how to carry a personal recommendation into Vello, so requesters can see how people they know have experienced a provider. Standing is earned by using a provider, either through a completed booking or, during a limited window for new providers, through requesters who have an established record on Vello. The community admin follows the same rules as everyone else. This brief depends on a separate "network of known people" feature. It doesn't cover newcomer onboarding, referrals between providers, admin tools or background checks. We accept that requesters with no network will get a weaker signal, and that some vouches will be given as favors; both will be reviewed after launch. The window length and the thresholds for "established" are still to be defined. We'll know it works when requesters in a usability test choose a provider based on neighbors' experience instead of looking for a rating.
