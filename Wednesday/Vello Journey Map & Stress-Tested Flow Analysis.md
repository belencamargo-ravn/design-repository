# Vello: Gaps, Missing States & Assumptions I Caught

**Sources**: Practice 3.2 (Break a Happy Path: dog-walk booking) and the [Match phase user flow (FigJam)](https://www.figma.com/board/qnfFuu5vkWb5UAmqkk4hJj/Untitled?node-id=0-1).

---

## 1. Missing states in the happy path

1. **Empty**: a search returns nothing, or the service the requester wants isn't listed (step 1).
2. **Loading**: while searching for providers (step 2) and while a booking is being created (step 4 → 5).
3. **Form validation error**: a wrong date, time or duration, or an unclear description (step 4).
4. **Timeout / no response**:
   * No time limit on holding a slot between the booking details and confirming (step 4).
   * The provider doesn't reply to messages after confirmation (step 5).
5. **Conflict / race condition**: the provider becomes unavailable, or another requester books them first (step 4).
6. **Cancellation before the job**:
   * Second thoughts before confirming (step 4). This needs a clear, guilt-free way out, not just "form abandonment".
   * Cancelling a confirmed booking, and capturing why ("I found another solution") (step 5).
7. **Permission denied**: location (needed to find nearby providers) and notifications (needed for messages and reminders).
8. **"Not trusted enough"**: what makes a requester trust a provider, and what they can do when the proof isn't enough yet (step 3).
9. **Requester counter-offer**: the requester proposes a different price. The draft only let the provider do this (step 4).
10. **Edit / reschedule**: the requester proposes a new date or time for a confirmed booking (step 5).
11. **Dispute & refund after the job**: how to complain and get money back when payment is released automatically (step 6).

## 2. Scope gap in the Match flow

* **"Price clear enough to book?" → No** had grown into a full quote sub-flow that belongs to the **Request phase**. I cut it back to a single exit, **"→ Request a quote (Request phase)"**.
* This took A5 ("providers answer quotes within 2 hours") out of scope for the Match flow.

## 3. Missing state in the Match flow: payment failure

The draft only had a generic "Card declined — try another" loop. It now also has:

* **Bank verification (3-D Secure)** inside the app.
* **Declined or timed out**: the attempt is recorded, the slot stays on hold, and the requester is **never charged twice**.
* **Retry limit**: up to 3 tries while the slot is still held.
* **Final failure**: "No charge made · slot released", then back to picking a date and time.

## 4. Assumptions

| # | Assumption | Status |
| :--- | :--- | :--- |
| A2 | Cards lead with neighbor vouches, not star ratings. | ✅ Confirmed |
| A6 | Address and entry notes are released only after the booking is confirmed. | ✅ Confirmed |
| A7 | Payment is authorized at booking and captured after the service. | ✅ Confirmed |
| A9 | With no matches, Vello routes to "Post a need" instead of widening the boundary. | ✅ Confirmed |
| A10 | The requester has no personal link to the provider. | ✏️ Corrected: this can happen but isn't required. The flow has to work in both cases. |
| A5 | Providers answer quotes within 2 hours. | ⏸️ Out of scope (belongs to the Request phase) |
| A1 · A3 · A4 · A8 · A11 · A12 | Verified-only listing · vouchers agree to be named · per-job quotes · provider accepts each booking · 3 payment attempts · 3-D Secure in the app | 🔍 Still to validate |

**Placeholders to confirm**: the 10-minute slot hold and the 1-hour window for the provider to accept.