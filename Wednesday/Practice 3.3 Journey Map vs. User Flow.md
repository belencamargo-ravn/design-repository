# Micro-practice 3.3: Journey Map vs. User Flow

**User goal**: Get a leaky faucet fixed today (Requester role)
**Who**: Alex, a renter in Bedford-Stuyvesant, Brooklyn. Moved in 8 months ago and knows 3 neighbors.
**Sources**: Vello App UI kit (provider Tom Baptiste, licensed handyperson, 1.6 mi away, $60/hr), the Vello design system, and the Kestrel Park research (people trust neighbor vouches, newcomers lack a local network, everyone worries about fair pricing).
**Artifacts**: [Leaky Faucet Journey](https://claude.ai/artifact/YDNreskCRtcw5roxNx8vVH) (the journey map) · [Request & Match Flow](https://claude.ai/artifact/KkRJgQAY7vy4hSW9vMQp3P) (the user flow)

---

## 1. High-Level Journey Map (Macro Level)

| Phase | User Actions | Mindset & Goals | Emotional State |
| :--- | :--- | :--- | :--- |
| **1. Discovery** | Hears the kitchen tap dripping at 7:40 am and tightens the handle, but it keeps dripping. Texts the landlord and gets no reply. Remembers the Vello flyer in the lobby and looks for someone who can fix it today. | *"I need someone today, and I don't know anyone here to ask."* | Frustrated / Anxious |
| **2. Request** | Takes a photo of the drip. Explains the problem, when they'll be home and where they live. Checks what a fair price looks like, then asks for help. | *"Let me explain this once so nobody wastes my time."* | Cautiously hopeful |
| **3. Match (Decision)** | Weighs who's nearby, affordable and vouched for by neighbors. Chooses Tom, waits to hear back, and learns he'll arrive between 3:30 and 4:00 pm. | *"Who have my neighbors actually used? Will anyone come today?"* | Anxious → Relieved |
| **4. Service** | Knows when Tom is on his way and lets him in. Watches the diagnosis (a worn cartridge), agrees to the extra part before Tom uses it, and checks that the tap is dry. | *"Is this the person I booked, and is the fix what I was quoted?"* | Reassured |
| **5. Payment** | Checks the bill against the quote (45 minutes of labor plus the part), adds a tip and pays. | *"Did I pay a fair price?"* | Watchful → Satisfied |
| **6. Review** | Rates the job, vouches for Tom to others in the building, and keeps Tom's contact for next time. | *"I'd tell the neighbors about him."* | Confident / Belonging |

**Channels by phase**:

1. Discovery: the kitchen sink, a text to the landlord, the lobby flyer, the Vello app
2. Request: the Vello app, the phone camera
3. Match: the Vello app, notifications
4. Service: in person at the door, messages with Tom
5. Payment: the Vello app, a card
6. Review: the Vello app, conversations with neighbors

**Emotion curve**: Low at Discovery, rising through Request. It dips while Alex waits to hear back from a provider, then lifts once the booking is confirmed. It dips again slightly at Payment while Alex checks the price, then peaks at Review.

> **Why a journey map**: It zooms out to the full six-phase arc so the team can see where trust and emotion rise or fall. Screen-level detail would bury that.

---

## 2. Request & Match User Flow (Micro Level)

Covers only phases 2 and 3: Request and Match.

![Request & Match user flow](request-match-flow.png)

**How to read it**

| Shape | Meaning |
| :--- | :--- |
| White rectangle | Screen the user sees (S1–S9) |
| Amber diamond | Decision branch |
| Blue dashed pill | System state (e.g. `Loading`, `Pending Acceptance`) |
| Red rectangle | Error or recovery screen |
| Dark green pill | Start, end, or hand-off to the next phase |

The main path is straight: **S1 → S2 → S3 → S4 → S5 → S6 → S7 → S8 → S9**. Every branch that leaves this path eventually comes back to it:

* **Address can't be verified** → S4a lets the user fix it. If it still fails, the request is saved as a draft with a limited set of providers.
* **No card on file** → S5a adds one (just a hold) and returns to S6.
* **No providers free today** → S6a offers three options: widen the search to 3 mi, pick another day (back to S3), or join a waitlist.
* **Tom declines, doesn't reply in 15 minutes, or suggests another time** → the user sees the next match (back to S7), or the S6a screen if no matches are left.

<details>
<summary>Mermaid source (renders in GitHub, Notion, Obsidian)</summary>

```mermaid
flowchart TD
  subgraph REQ["PHASE 2 · REQUEST"]
    direction TB
    A([Start: Explore home<br/>taps Handyperson]):::terminal --> S1[S1 · Choose job type<br/>Plumbing › Leaky faucet]:::screen
    S1 --> S2[S2 · Describe the job<br/>photo + note]:::screen
    S2 --> S3[S3 · Pick a time<br/>Today · after 2 pm]:::screen
    S3 --> S4[S4 · Confirm address]:::screen
    S4 --> L1([Loading · checking address]):::state
    L1 --> D1{Address<br/>verified?}:::decision
    D1 -->|No| S4a[S4a · Verify address<br/>add apt number or mail code]:::error
    S4a -->|Still unverified| DR([Draft saved<br/>limited set of providers]):::state
    D1 -->|Yes| S5[S5 · Price guide<br/>neighbors paid $60–95]:::screen
    S4a -->|Verified| S5
    DR --> S5
    S5 --> D2{Card on<br/>file?}:::decision
    D2 -->|No| S5a[S5a · Add card<br/>hold only, charged after job]:::screen
    D2 -->|Yes| S6[S6 · Review & post request]:::screen
    S5a --> S6
  end

  subgraph MATCH["PHASE 3 · MATCH"]
    direction TB
    L2([Loading · finding providers]):::state --> D3{Anyone free<br/>today?}:::decision
    D3 -->|No| E[S6a · No one free today]:::error
    E -->|Widen to 3 mi| L2
    E -->|Notify me| W([Request open · waitlisted]):::state
    D3 -->|Yes| S7[S7 · Matches list<br/>vouches · $/hr · ETA]:::screen
    W -.->|provider frees up| S7
    S7 --> S8[S8 · Provider profile<br/>Book Tom · $60/hr]:::screen
    S8 --> PA([Pending acceptance<br/>15-min timer]):::state
    PA --> D4{Tom's<br/>response?}:::decision
    D4 -->|Accepts| OK([S9 · Booking confirmed<br/>arrives 3:30–4:00 pm]):::terminal
    D4 -->|Suggests new time| S8b[S8b · Review counter-offer]:::screen
    S8b -->|Accept| OK
    S8b -->|Decline| D5
    D4 -->|Declines or no reply| D5{Other<br/>matches left?}:::decision
    D5 -->|Yes, try next| S7
    D5 -->|No| E
  end

  S6 --> L2
  E -->|Pick another day| S3
  OK --> NEXT([→ Phase 4 · Service]):::terminal

  classDef screen fill:#FFFFFF,stroke:#16462F,stroke-width:1.5px,color:#1D2A22;
  classDef decision fill:#F5E7CC,stroke:#A96A12,stroke-width:1.5px,color:#3B2A08;
  classDef state fill:#DCE7EE,stroke:#2F5D7C,stroke-width:1.5px,stroke-dasharray:5 3,color:#16303F;
  classDef error fill:#F3DDD5,stroke:#A8442E,stroke-width:1.5px,color:#4A1C12;
  classDef terminal fill:#16462F,stroke:#16462F,color:#F6F2E7;
```

</details>

**System states covered**: `Loading · Checking address`, `Draft saved`, `Card hold pending`, `Loading · Finding providers`, `Request open · waitlisted`, `Live: new matches appear`, `Pending Acceptance · 15 min`, `Confirmed`.

**Open questions for the team**: Should the acceptance window really be 15 minutes? Should the wider search radius really be 3 miles?

> **Why a user flow**: It narrows to one slice of the journey so every screen, branch, and system state is clear enough for design and engineering to actually build and test.

---

## 3. What I Fixed After the First Draft

I asked Claude to check both documents for two things: UI language sneaking into the journey map, and feelings sneaking into the user flow.

* **Journey map described screens instead of people.** It said things like *"Taps 'Leaky faucet' under Plumbing"* or *"Approves the $18 part in-app."* I rewrote these as what a person actually does: *"Explains the problem and when they'll be home"*, *"Weighs who's nearby, affordable, and vouched for by neighbors."*
* **Touchpoint row repeated the user flow.** It listed app screens and components instead of real-world channels. I replaced it with a **Channels** row: the kitchen sink, a text to the landlord, the lobby flyer, the app, Tom at the door, conversations with neighbors.
* **User flow explained feelings, not just steps.** Its footer justified a design choice by how users feel. I cut that line — reasoning about emotion belongs in the journey map, not the flow.
* **One step was out of scope.** *"Adds it to the calendar"* happens after booking, outside Request & Match, so I removed it.
* **Kept the offline moments in the journey map on purpose.** Tightening the handle, texting the landlord, letting Tom in — these give the big picture its human context, even though they never touch the app.