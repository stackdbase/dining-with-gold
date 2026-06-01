# DWG Welcome Email Flow — Setup Guide

A 3-step automated welcome sequence:

| # | Email | When it sends | File |
|---|-------|---------------|------|
| 1 | Welcome to my table | Immediately on signup | `email-1-welcome.txt` |
| 2 | Three chillies. One small bottle. | Day 3 | `email-2-day3.txt` |
| 3 | Two things people ask me most | Day 7 | `email-3-day7.txt` |

> A 4th email (`email-4-review-OPTIONAL.txt`) is a **separate** post-delivery
> review request — build it on its own with an "Order fulfilled" trigger, not in
> this flow.

---

## Build it in Shopify (Marketing → Automations)

This must be done in the Admin UI — Shopify has no API to create automations.

1. **Shopify admin → Messaging → Automations → Create automation.**
2. Pick **"Welcome new subscribers"** (a pre-built template that triggers on
   *Customer subscribed to email*). If you'd rather build from scratch, choose
   **Create custom automation** and set the trigger to **Customer subscribed**.
3. You'll land on the flow canvas. It usually starts: **Trigger → Send email**.

### Email 1 (immediate)
4. Click the **Send email** block → **Edit email content**.
5. Set **Subject** and **Preview text** from `email-1-welcome.txt`.
6. Drop a **Text** section and paste the body. Add a **Button** section where the
   `[ BUTTON ]` line is → label `Step into the kitchen →`, link
   `https://diningwithgold.com`.
7. Save.

### Wait → Email 2 (Day 3)
8. Below Email 1, click **+** → add a **Wait / Time delay** → set **3 days**.
9. Add another **Send email** block → paste `email-2-day3.txt`
   (subject, preview, body, button → `https://diningwithgold.com/collections/all`).

### Wait → Email 3 (Day 7)
10. Add another **Wait / Time delay** → **4 days** (3 + 4 = Day 7 from signup).
11. Add a **Send email** block → paste `email-3-day7.txt`
    (button → `https://diningwithgold.com/collections/all`).

12. **Turn the automation ON** (top-right toggle).

---

## Notes / gotchas

- **Delays are cumulative.** Email 2 waits 3 days from signup; Email 3's delay is
  **4 days after Email 2**, landing on Day 7 — not another 7.
- **First name:** the welcome emails don't use a name tag, so no personalization is
  needed. The optional review email does — insert it via the editor's
  **Insert → Customer first name** so it degrades gracefully.
- **WELCOME10 discount (Email 3):** create the code first under
  **Discounts → Create discount → 10% off**, code `WELCOME10`. The email just
  prints the text; it doesn't generate the code.
- **Free shipping over £50 (Email 3 copy):** make sure a matching shipping rate
  exists under **Settings → Shipping** so the promise is true.
- **Sender domain:** for best deliverability, verify your sending domain under
  **Settings → Notifications → Sender email** (otherwise Shopify sends via its
  shared domain).
- **Test first:** use **Send test email** on each step before switching the
  automation on.
