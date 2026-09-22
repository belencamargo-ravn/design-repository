# Vello Research Synthesis & Prioritized Problems

**Date:** 22 Sept 2026
**Author:** @Belen Camargo
**Scope:** Kestrel Park discovery interviews P01–P06, covering Requesters, Providers and a Community Admin

---

## 1. Executive Summary & Methodology

**Method.** I analyzed six discovery interviews, conducted 11–18 June 2026, covering all three Vello roles:

| ID | Role | Context |
|---|---|---|
| P01 | Requester | 41, two kids, resident 6 years |
| P02 | Requester | 36, new father, resident 8 months |
| P03 | Requester | 71, lives alone, resident 11 years. Her daughter (quoted as **P03-D**) joined part of the session. |
| P04 | Provider | Cleaner working across three areas, lives outside Kestrel Park |
| P05 | Provider | Handyman, local, self-employed 22 years |
| P06 | Community Admin | Volunteer chair of the residents' association, maintains the trades list |

Themes were coded across all transcripts. Every quote below is verbatim, and P03 and P03-D count as one participant.

**Core insight.** Trust in Kestrel Park is conditional:
- **When a vouch is available, it's the preferred signal.** Requesters use one from someone they know even for unsupervised key access to their home.
- **When no vouch is available, requesters fall back on other signals.** P02 wants formal checks for childcare. Others rely on reviews, and feel uneasy about it.
- **Who gets excluded.** Newcomers, long-term residents whose networks have decayed, and new providers are the people this trust system leaves out.

---

## 2. Key Research Themes

### Theme 1: Personal vouches vs. formal verification: trust depends on context

**Participant reach:**
- A vouch is the preferred signal for 5 of 6 participants (P01, P02, P04, P05, P06).
- Only 1 participant explicitly wants formal checks: P02, for childcare.

**Verbatim evidence**
- "I'm taking Priya's man. Every time. I don't think the certificate is telling me what I actually want to know." (P01)
- "Somebody who lives here has to have used them and said they were good. That's the rule." (P06)
- "I suppose the checks are for when you don't have a Denise." (P02)

**Contradictions & edge cases**
- **P02 wants formal checks for childcare.** "Proper vetting. Real checks, real ID, real references, and don't let people on without it." (P02)
- **Checks aren't treated as mandatory, even for childcare.** P01 hired a sitter she had never met: "I booked someone off an app who I had never met, based on reviews, and she was great."
- **Vouches cover high-access help too, not just low-stakes jobs.** Both vouched hires hold house keys. P01's dog walker: "He has a key to my house and he's in there when nobody's home." P02's cleaner: "And Marta's got a key now."
- **A vouch only works if the requester recognizes the voucher.** P02 says of an unnamed neighbour: "that's just a stranger who lives nearby."
- **Open question:** Does childcare genuinely require formal checks, or is that one participant's preference? This needs testing in the next round.

### Theme 2: No-shows and late cancellations are the failure requesters actually experience

**Participant reach:** 3 of 6 (P01, P04, P05)

**Verbatim evidence**
- "Whether he'll turn up. [laughs] Honestly. That's the real thing." (P01)
- "Turning up. That's ninety per cent of it." (P05)

**Contradictions & edge cases**
- **Safety is still the stated fear for high-stakes help.** "If somebody is going to be alone with my son, I want to see a check." (P02)
- **What people fear isn't what actually goes wrong.** Safety is what people raise upfront, but the failure they report is cancellation. P01's previous cleaner cancelled on the day three times, and that ended the relationship.
- **Trust builds through a track record that isn't written down anywhere.** P04 says clients stop watching after three on-time visits and hand over the key at the fourth.
- **Arrival windows are a separate problem, not part of this theme.** P03's provider did turn up. Her complaint was the two-hour window: "Just tell me a time. Not a window, a time." For a housebound requester, the window costs the whole day. Providers define reliability at the level of a half-day ("If you say Thursday morning and you're there Thursday morning, you're already better than most," P05). This comes from one participant only.

### Theme 3: Exclusion of residents and providers without a working local network

**Participant reach:** 5 of 6 (P02, P03, P04, P05, P06)

People end up without a working network in two distinct ways.

**3a. The network was never built (newcomers and new providers)**
- "There's forty flats on this street and I could name three people." (P02, 8 months in the area)
- "So the list is a bit of a closed shop and I'm aware of it." (P06)

**3b. The network decayed (long-term, older residents)**
- "There were people I knew when I moved in but that's all changed over, it's mostly young people now, they're out at work." (P03, 11 years in the area)
- "And after Ken I didn't have anyone." (P03)

**Contradictions & edge cases**
- **The network works well for people inside it.** P01 found a dog walker through a WhatsApp group in about a week.
- **Tenure alone doesn't predict whether someone is connected.** P06 (24 years) is highly connected, while P03 (11 years) is not.
- **P03 rejects being seen as isolated.** "I'm not sitting here feeling sorry for myself, I've got my daughter twenty minutes away and I've got the church." Her support networks exist, but they sit outside her building.
- **Established providers have more demand than they can handle.** P05 is booked about five weeks out.

### Theme 4: Price transparency and doorstep overcharging

**Participant reach:** 4 of 6 (P02, P03-D, P05, P06)

**Verbatim evidence**
- "I just had no way to know if I was being had." (P02)
- "All the checking in the world doesn't stop someone quoting a stupid number on the doorstep." (P03-D)

**Contradictions & edge cases**
- **Tradespeople say fixed quotes upfront often aren't possible.** "you can't price a wall off three photos, and if you say that they think you're being awkward." (P05)
- **Price matters less for ongoing, key-holding help.** "the price, the schedule, all of that is negotiable, but somebody's got a key." (P01)
- **The risk concentrates on isolated older residents.** P03-D and P06 independently cite £400 charged for a job worth £80.

---

## 3. Data Model & System Implications

These entities are hypotheses drawn from observed behavior. Each needs validation.

### `ProviderEndorsement`
A vouch from one person for a provider.

**Fields:** endorser, provider, relationship to the requester, repeat-booking count, endorsement status, endorser visibility.

**Where each field comes from:**
- **Repeat-booking count:** requesters value the number of times someone they know used a provider over star ratings. P01: "Tell me Priya used him eleven times."
- **Status:** needs a middle state between included and removed. P06: "I didn't have anything in between. Either you're on it or you're not."
- **Visibility:** the admin wants to stay anonymous when she turns someone down. P06: "If I turn someone down I'd rather they didn't know it was me who did it."
- **Open question:** P06 wonders whether several endorsements from people nobody knows could add up to one trusted vouch. "Three unknowns might be worth one Denise." No requester has tested this.

### `StakesLevel`
How much trust a booking requires.

**Derived from:** the level of access the provider gets (keys, children, repeat presence) combined with how vulnerable the requester is. Job category alone doesn't determine it.

**Evidence:**
- P01 sorts jobs by access: "Ongoing thing, someone in my house, someone with my kids, completely different question."
- P03's one-off repairs carry high trust and price risk because of her circumstances.
- Dog walking involves key access (P01), so it isn't a low-stakes category.

### `DelegatedBooking`
Separates the person who arranges and pays from the person who receives the service, and keeps a history of past bookings.

**Evidence:**
- "Every one of these apps assumes the person who needs the thing is the person holding the phone." (P03-D)
- "She's had four different people in this flat in two years and there's no record of any of it." (P03-D)
- P06 corroborates indirectly: "I hear about it afterwards from a daughter or a son."

Direct evidence comes from one household only.

---

## 4. Three Prioritized Problem Statements

### Problem 1: Highest impact (Requester)

- **Who:** Requesters without an established local network who need high-access help: childcare, or someone holding house keys.
- **What:** They can't judge whether an unfamiliar provider is trustworthy. The signals available to them, like star ratings and badges, don't answer what they actually want to know: will this person show up, and has someone I know used them?
- **Why:** A wrong decision here carries high personal risk, so requesters either stall or book anxiously. P02 says of sitter apps, "I look, I browse, and then I close it." P01 booked a sitter she'd never met because she was desperate.
- **Evidence:** P01, P02, P03-D (Themes 1, 2).

### Problem 2: High impact (Requester, with Community Admin)

- **Who:** Network-isolated Requesters, both newcomers and long-term older residents whose networks have decayed, plus the volunteer Community Admin who manages recommendations.
- **What:** Isolated residents can't get into the word-of-mouth circles that local trust depends on. The Admin can judge a recommendation only by whether she personally knows the person making it, and this unpaid work takes about three hours of her evenings each week.
- **Why:** Trust only travels between people who already know each other. That leaves isolated residents exposed to doorstep overcharging, and it has kept a new provider off the list for months.
- **Evidence:** P02, P03, P06 (Themes 3, 4).

### Problem 3: Medium impact (Provider)

- **Who:** Independent local Providers, especially those who are new or trying to grow.
- **What:** They can't win new clients when they need them, because work only arrives through word of mouth. A single disputed job or unfair review can also follow them permanently, with no way to resolve it.
- **Why:** Their business depends on long-term reputation and repeat clients. Offline, problems get fixed face to face, and that conversation doesn't happen when the relationship runs through a platform.
- **Evidence:** P04, P05, P06 (Themes 1, 3).

---

## 5. AI Audit Log (Human Verification Pass)

I checked Claude's synthesis against the raw transcripts and corrected three errors.

**1. Theme 1 overstated as a universal rule.**
- **What Claude wrote:** a Theme 1 heading that read "Trust comes from a person you know vouching, not from checks or ratings."
- **What I found:** P02 wants formal checks for childcare, so the heading didn't hold as a universal rule.
- **The correction:** Theme 1 was reframed as conditional. Checking the transcripts also showed P01 hiring a sitter without any check, and vouched hires holding keys. So the final version treats checks as a fallback, not a requirement, and doesn't limit vouches to low-stakes help.

**2. Two different reliability problems merged.**
- **What Claude wrote:** it put no-shows and cancellations (P01) together with P03's arrival windows, describing the windows as "the same reliability problem."
- **What I found:** P03's provider did arrive. Her problem was how imprecise the time slot was, not whether he came.
- **The correction:** arrival windows are now a separate problem that affects housebound requesters.

**3. An unsupported claim that time in the area determines who is connected.**
- **What Claude wrote:** it inferred that "length of time in the area" was the deciding factor.
- **What I found:** P03 has lived here 11 years and is as cut off as a newcomer.
- **The correction:** Theme 3 now separates networks that were never built from networks that decayed.