# DWG — Review request email

Post-purchase email that sends customers to the on-site review form (the custom
reviews system, not Judge.me). The CTA deep-links to the product page and
**auto-opens the review form**.

## Setup (Shopify → same place as the welcome flow: Email → Automations)
- **Trigger:** *Order fulfilled* (or *delivered*, if available) → **wait 7 days**.
  - 7 days ≈ enough time to receive it and actually cook with it.
- **Audience:** customers who completed a purchase (exclude anyone who already reviewed if you like — optional).
- **One email**, template below.
- **CTA button link:**
  `https://diningwithgold.com/products/dwg-travel-chilli-oil#write-a-review`
  - The `#write-a-review` fragment auto-opens the form and scrolls to it.
  - (Single hero product, so link straight to it. If you add products later and the
    automation supports a dynamic product URL, append `#write-a-review` to that.)
- **Turn OFF** any Judge.me review-request email so customers don't get two.

---

## Email copy

**Subject line** (pick one):
- How did the gold treat you? ✨
- Loved it? Tell us (and the world)
- A quick favour, from Dining With Gold

**Preheader:** Your words help someone else discover their new favourite.

**Body:**

> Hi {{ first_name }},
>
> We hope your Dining With Gold chilli oil has been earning its place at the table.
>
> If it's brought a little heat and a little luxury to your cooking, we'd love for you
> to share it — a quick review helps fellow food lovers discover what you already know.
>
> It takes about 30 seconds.
>
> **[ Leave a review → ]**  ← button links to the URL above
>
> Thank you for being part of the DWG table.
>
> — The Dining With Gold team

**Fallback text link (under the button):**
Or paste this into your browser: https://diningwithgold.com/products/dwg-travel-chilli-oil#write-a-review

---

## Notes
- No login required — the form takes name, rating, title, and review text.
- Reviews **auto-publish**, so a customer sees their review go live right after submitting.
- Keep the brand look: gold accent (#C9882A), dark text (#1C1C1C), Playfair headings.
