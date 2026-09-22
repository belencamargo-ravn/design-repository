# Design & Product at Ravn: A Reflection

## What design owns

Design owns the how. On Vello, that means:

- Making it effortless to go from "I need help" to "it's booked" by the use of UX strategies for browsing Providers, sending a request, and confirming a booking.
- Designing each screen's layout, imagery, and micro-interactions (a Provider's profile, the booking confirmation, the Admin approval view) so the app feels pleasant, not just functional.
- Designing the trust cues, like the verification badge and the Admin's presence, so a Requester feels safe letting a stranger into their home.
- Building engagement patterns, like rebooking a trusted Provider and post-booking nudges, that keep Requesters and Providers coming back to Vello.
- Defining clear forward and ongoing flows so users easily understand what part of the flow they're in and can go back without confusion.
- Handling errors in a healthy way, so mistakes (a failed booking, a declined verification) are communicated clearly and don't leave users confused or frustrated.

## What product contributes across the lifecycle

Product brings the why and the constraints design can't see alone. On Vello, that means:

- Organizing and prioritizing what the team works on next, so design and engineering know what matters most right now.
- Supporting the team with the business rules Vello must meet, and guiding everyone toward achieving them.
- Defining what "verified" means before an Admin approves a Provider.
- Defining how the pricing model behaves for each booking.
- Running competitive analysis on platforms like TaskRabbit and Thumbtack to improve our overall approach.
- Defining success metrics, like repeat bookings and Provider retention, so we know after launch whether a decision actually worked, not just whether people signed up.
- Defining scope boundaries for each launch, like the first service and neighborhood size for v1, so design and engineering aren't guessing at what's in or out.
- Defining what a Requester, Provider, and Admin are each authorized to do, since role boundaries are a business rule, not a design choice.

It's a job of context and priorities, not pixels; once it starts saying how a badge should look, that's design's job.

## Mapping Product's touchpoints across the 5 lifecycle phases

Product's specific role across the 5 phases for Vello:

- **Discover:** Testing whether Requesters trust neighborhood Providers enough to book them over a big platform alternative, and whether Providers trust the platform and Requesters enough to offer their services, and where that trust breaks down either way.
- **Define:** Defining v1 scope: the first service category, what each user role (Requester, Provider, Admin) can do, how payment works, and what "trust" means for our users.
- **Architect:** Defining how the three roles flow through and communicate with each other, and what specific tasks and permissions each one has.
- **Design (Critique):** Bringing business-rule constraints, available data, and the outcomes driving our North Star metric into design critiques, without dictating UI.
- **Validate:** Measuring completed transactions over time as our North Star metric, tracking conversion, engagement, and adoption together, not just signups.

## Pushbacks to Claude's Draft

[Documenting pushbacks against generic PM boilerplate in favor of Vello's 3 roles and plain language.]

- Pushed back on generic PM language in the first draft, asking every section to name Vello's hyperlocal scope, three roles (Requester, Provider, Admin), and trust model directly instead of talking about ownership and contribution in the abstract.
- Rejected paragraph-style writing for "What design owns," asking for straight bullet points instead so each responsibility is scannable on its own.
- Pushed each bullet further into a direct action sentence (e.g. "Making it effortless to go from 'I need help' to 'it's booked'...") rather than a label followed by an explanation.
- Rejected the original "badge vocabulary" bullet as too narrow, replacing it with a bullet about clear forward/ongoing flow navigation, and added a separate bullet on handling errors in a healthy way, since neither was covered yet.
- Brought my own list of what Product contributes (prioritization, business-rule support, defining "verified," pricing model, competitive analysis) instead of accepting a generic list, and only added Claude's suggestions (success metrics, launch scope boundaries, role authority) after confirming I wanted them.
- Asked for a dedicated phase-by-phase mapping of Product's role instead of a single paragraph, and corrected the Discover phase to cover trust in both directions (Requester trusting Provider, and Provider trusting the platform/Requesters), not just one.
- Kept the North Star metric description general ("completed transactions over time") rather than letting Claude invent a specific, unconfirmed metric definition.

## Reframing a decision: solution → problem

Two moments show this slip, from framing a problem to prescribing a solution: one on Vello's trust model, one from a different project with the same lesson.

**Candidate 1: Verification badges (Vello).** I said: make the badge look like this, here. Better: "Requesters need to trust a neighbor Provider fast, without pages of proof, before letting them in. How can design show that trust when someone picks a nearby Provider?"

**Candidate 2: Add-to-purchase (ReNest), a Vello parallel.** I said: put the button here, like this. Better: "People need a low-friction way to add something the moment they find it. What's simplest, and where does it live?" On Vello, the same fix: instead of dictating a "book again" button's spot, ask, "a Requester who trusts a Provider shouldn't have to re-search the neighborhood to rebook them. Where does that shortcut belong?"

Both started from a real need. The mistake wasn't the opinion; it was skipping the problem and handing design a finished solution.

## Conclusion

PMs are facilitators and colleagues to designers, not bosses. Success comes when both work side by side toward the same goal, with clear communication.
