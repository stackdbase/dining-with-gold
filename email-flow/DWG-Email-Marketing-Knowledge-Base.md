# Dining With Gold — Email Marketing Knowledge Base

**Owner:** Dining With Gold (DWG)
**Store:** https://diningwithgold.com  ·  Shopify (Basic plan, UK / GBP)
**Prepared:** 2026-06-01
**Audience:** Email marketing specialist / agency picking up DWG email
**Purpose:** Single source of truth for the welcome flow, the post-purchase
review request, brand voice, setup steps, prerequisites, testing, deliverability
and KPIs. Everything needed to build, run and extend DWG email without prior
context on the brand.

---

## 1. Brand snapshot

| | |
|---|---|
| **Product** | Travel-sized chilli oil. Bold, flavour-first, "small enough for your handbag." |
| **Range** | Travel Chilli Oil (single, £12), 2-Pack (£21.99), 3-Pack (£29.99), Home Jar (£25). |
| **Founder / sender** | **Wura** — founder & chef. *Wura* means "gold" in Yoruba. All emails are written first-person as Wura. |
| **Market** | UK-first (free UK shipping over £50). International travel/food-lover audience. |
| **Positioning** | "No bland plates allowed." Three chillies, salt, seasoning, vegetable oil — no fillers. Heat *with flavour*, made with intention. |
| **Tone** | Warm, personal, conversational, a little cheeky. Short punchy paragraphs. First-person founder voice. Sign-off is always **"Come hungry, Wura — Founder, Dining With Gold."** |

**Voice rules (keep these intact in any future email):**
- Write as Wura, to one person, like a note across a kitchen table.
- Short paragraphs, frequent line breaks, no corporate filler.
- British spelling (flavour, colour).
- One clear CTA per email.
- End every email with the **"Come hungry, Wura"** sign-off.

---

## 2. Programs at a glance

DWG runs **two separate automations**. Do not merge them — different triggers.

| Program | Trigger | Steps | Goal |
|---|---|---|---|
| **A. Welcome flow** | Customer subscribes to email marketing | 3 emails: signup → Day 3 → Day 7 | Introduce the founder & product, build trust, convert first order (WELCOME10). |
| **B. Review request** | Order fulfilled / delivered | 1 email, +3 days after delivery | Collect reviews & surface issues for recovery. |

Source copy files (plain text, paste-ready) live alongside this doc:
- `email-1-welcome.txt`, `email-2-day3.txt`, `email-3-day7.txt` (Program A)
- `email-4-review-OPTIONAL.txt` (Program B)
- `SETUP-GUIDE.md` (quick build steps)

---

## 3. Where to build it in Shopify (important platform note)

This store uses **Shopify Email** for automations. On this account, **Shopify
Email is surfaced *under the Shopify marketing/messaging app surface*, not as a
standalone "Shopify Email" tile** — so:

- **Automations** lives at **Marketing → Automations** *once Shopify Email is
  present*. If the Automations tab seems missing, it's nested under the
  marketing app (the same surface as Shopify Inbox/Messaging), not absent.
- App Store **search for "Shopify Email" is unreliable** (often returns Shopify
  Inbox). Use the direct link if you ever need to (re)install: `https://apps.shopify.com/email`.
- **Account permissions matter:** the Automations tab and app install are hidden
  for staff/collaborator accounts lacking **"Manage and create marketing"** and
  **"Apps and channels"** permissions. Use the store-owner account or have those
  granted (Settings → Users and permissions).
- **Region is fine:** store is registered UK (GB) / GBP, which fully supports
  Shopify Email. (Shopify Email gates on the *store's registered country*, not
  shipping destinations.)

---

## 4. PROGRAM A — Welcome Flow (build spec)

**Trigger:** *Customer subscribes to email marketing.*
**Audience:** New email subscribers (storefront footer signup, welcome popup,
checkout opt-in).
**Structure:**

```
[Subscribe] → Email 1 (immediate)
            → Wait 3 days
            → Email 2
            → Wait 4 days          (3 + 4 = Day 7 from signup)
            → Email 3
```

> **Critical timing note:** Shopify wait blocks are **cumulative between emails**.
> Email 3's wait is **+4 days after Email 2**, which lands on **Day 7 from
> signup** — NOT another 7 days. Setting it to 7 would push Email 3 to Day 10.

### Email 1 — Immediate
- **Subject:** `Welcome to my table`
- **Preview text:** `A small bottle. A big story. Come hungry.`
- **CTA:** `Step into the kitchen →` → `https://diningwithgold.com`
- **Body:** see `email-1-welcome.txt`. Founder intro + origin story. No
  personalization tags required.

### Email 2 — Day 3
- **Subject:** `Three chillies. One small bottle.`
- **Preview text:** `Why DWG isn't just another hot sauce.`
- **CTA:** `Try a bottle →` → `https://diningwithgold.com/collections/all`
- **Body:** see `email-2-day3.txt`. Ingredients & product philosophy.

### Email 3 — Day 7
- **Subject:** `Two things people ask me most`
- **Preview text:** `Shipping, size, and why it fits in your handbag.`
- **CTA:** `Order your first bottle →` → `https://diningwithgold.com/collections/all`
- **Body:** see `email-3-day7.txt`. FAQ (handbag size + shipping) and the
  **first-order offer**.
- **Offer:** `Code: WELCOME10` (10% off first order).

---

## 5. PROGRAM B — Post-purchase Review Request (build spec)

**Trigger:** *Order fulfilled* (ideally *delivered*, if a delivery event is
available via your shipping/tracking app).
**Send timing:** **3 days after delivery confirmation.** Fallback: **7–10 days
after order date** if delivery isn't tracked.
**Build as its own automation — do NOT attach to the welcome flow.**

- **Subject:** `So… how was it?`
- **Preview text:** `Tell me what your plate thinks.`
- **CTA:** `Leave a quick review →` → `https://diningwithgold.com/pages/reviews`
- **Personalization:** opens with `Dear {{ first_name }}` — insert via the
  editor's **Insert → Customer first name** so it degrades gracefully when no
  name exists.
- **Body:** see `email-4-review-OPTIONAL.txt`. Note the built-in service-recovery
  line ("if something wasn't right with your order, just hit reply") — keep it;
  it catches dissatisfied customers before they leave a public 1-star.

> **Reviews destination note:** `/pages/reviews` is currently the "Loved By You"
> video wall (social proof), not a structured review-collection form. If DWG
> wants star-rating capture, install a reviews app (e.g. Shopify Product Reviews
> alternative / Judge.me / Loox) and point this CTA at its submission link.

---

## 6. Prerequisites checklist (do BEFORE turning anything on)

- [ ] **`WELCOME10` discount created** — Discounts → Create discount → 10% off,
      code `WELCOME10`. (Email 3 only prints the text; the code must exist.)
      Decide: first-order only? min spend? expiry? — set guardrails.
- [ ] **Free shipping over £50 rate exists** — Settings → Shipping. Email 3
      promises it; the rate must be real for UK.
- [ ] **Sender domain authenticated** — Settings → Notifications → Sender email.
      Authenticate `diningwithgold.com` (SPF/DKIM) for deliverability; otherwise
      Shopify sends via its shared domain (weaker inbox placement).
- [ ] **Subscription capture points live** — storefront footer signup, welcome
      popup/banner, and checkout email-marketing opt-in all feed the same
      "subscribed" trigger.
- [ ] **Consent compliance (UK GDPR / PECR)** — only email contacts with explicit
      marketing consent. Every email must carry a working unsubscribe (Shopify
      adds this automatically — don't remove it) and a physical business address
      in the footer.

---

## 7. Testing protocol

1. **Content QA:** use **Send test email** on each step. Check on desktop + mobile:
   subject, preview text, body line breaks, button links, sign-off, images.
2. **Link check:** click every CTA; confirm it lands on the right page and the
   `WELCOME10` code applies at checkout.
3. **Trigger test (end-to-end):** subscribe a Gmail alias (e.g.
   `name+dwgtest@gmail.com`) via the live storefront signup. Confirm Email 1
   arrives immediately. (Manually adding a customer **without** marketing consent
   will NOT trigger the flow.)
4. **Timing sanity:** verify the wait blocks read **3 days** then **4 days**.
5. **Review flow:** place a test order, mark fulfilled/delivered, confirm the
   review email schedules to +3 days.
6. **Spam/inbox placement:** send tests to Gmail, Outlook and Apple Mail; watch
   for Promotions-tab vs spam.

---

## 8. Deliverability & list health

- Authenticate the sending domain (SPF + DKIM). Consider DMARC.
- Warm up gradually if list volume jumps; avoid a cold blast to a large old list.
- Keep a **sunset policy**: suppress contacts with no opens in ~6–12 months.
- Monitor bounce + spam-complaint rates; keep complaints < 0.1%.
- Never buy lists. Consent only.

---

## 9. KPIs & benchmarks

Track per email and per program. Rough DTC/food benchmarks (treat as directional,
not targets — establish DWG's own baseline after 4–6 weeks):

| Metric | Welcome-flow ballpark | Notes |
|---|---|---|
| Open rate | 40–60% (Email 1 highest) | Welcome emails over-index; decay across steps is normal. |
| Click rate | 5–15% | Driven by the single clear CTA. |
| Click-to-open | 10–25% | |
| Placed-order rate (flow-attributed) | 1–5% | Email 3 (offer) should carry most revenue. |
| Unsubscribe rate | < 0.5% per send | Spikes = frequency/relevance problem. |
| Review email response | 1–5% of recipients | Lifts with incentive or one-tap rating. |

**Primary success metric:** first-order conversion attributable to the welcome
flow, and review volume from Program B.

---

## 10. Roadmap / expansion ideas (optional, after baseline)

- **Abandoned checkout** automation (highest-ROI flow after welcome).
- **Win-back** flow for lapsed buyers (60–90 days no purchase).
- **Post-first-purchase** cross-sell (single → bundle / Home Jar).
- **Recipe / usage** seasonal campaigns (eggs, jollof, pasta — reinforce "put it
  on anything").
- **Replenishment** nudge timed to typical bottle-finish window.
- A/B test subject lines on Email 1 and the offer in Email 3.

---

## 11. Reference

- **Store:** https://diningwithgold.com
- **Collections / shop link used in CTAs:** https://diningwithgold.com/collections/all
- **Reviews page:** https://diningwithgold.com/pages/reviews
- **Platform:** Shopify Basic (UK/GBP), Shopify Email for automations.
- **Copy files:** `email-1-welcome.txt`, `email-2-day3.txt`, `email-3-day7.txt`,
  `email-4-review-OPTIONAL.txt` (same folder as this doc).
- **Quick build steps:** `SETUP-GUIDE.md`.

### Appendix — automation diagram

```
PROGRAM A: WELCOME
──────────────────
Subscribe ─▶ ✉ Email 1  "Welcome to my table"           (t = 0)
            ⏲ wait 3 days
            ✉ Email 2  "Three chillies. One small bottle." (Day 3)
            ⏲ wait 4 days
            ✉ Email 3  "Two things people ask me most"      (Day 7)  ← WELCOME10

PROGRAM B: REVIEW (separate)
────────────────────────────
Order delivered ─▶ ⏲ wait 3 days ─▶ ✉ "So… how was it?"
```
