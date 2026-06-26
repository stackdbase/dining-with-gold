# Judge.me Reviews — Setup & Integration (DWG)

Goal: give the store a real **star-review input + display**, and make the
review-request email's stars land on a working submission form.

Store: `1tyg0m-3a.myshopify.com` · Live theme: **198719209820** ("Copy of Dining
with Gold Sandbox") · Country: United Kingdom · Plan: **Judge.me Free**.

App handle: `judge-me-reviews` · Theme-extension UUID: `61ccd3b1-a9f2-4160-9fe9-4fec8413e5d8`

---

## Status (2026-06-26)

### ✅ Done
- **Judge.me Product Reviews** installed; core embed enabled
  (`config/settings_data.json` → `judgeme_core`, `disabled: false`).
- **Product page already shows the review widget + star badge** — Judge.me
  auto-injected them. Verified live on
  `diningwithgold.com/products/dwg-travel-chilli-oil`:
  `jdgm-review-widget` (write-a-review form + list) and `jdgm-preview-badge`.
- Old hardcoded **"Based on 128 reviews"** block is **disabled** — no fake
  reviews showing next to the real 0-count widget.
- **Brand colour (on-site):** gold `#C9882A` override appended to
  `theme/assets/dwg-brand.css` (Judge.me ships teal `#108474` by default) and
  pushed to the live theme. Recolours stars, the "Write a review" button,
  histogram bars, verified badge, pagination. *(Storefront edge-cache may take a
  few minutes / a theme-editor Save to roll over to the new asset version.)*

### 🔧 Remaining — admin-only (no API/CLI; must be done in the dashboards)

**1. Brand colour in EMAILS** *(CSS can't reach emails)*
- Judge.me → **Settings → Widget customization / Look & feel** → set the
  primary / star / button colour to **`#C9882A`** and Save. This makes the
  stars in the review-request email gold too.

**2. Switch the review-request email to Judge.me's** *(this is what fixes the
"email links nowhere" problem)*
- Judge.me → **Settings → Review requests (emails)** → enable; delay
  **~5–7 days after fulfillment**.
- Shopify → **Messaging → Automations** → turn **OFF** the native
  review-request automation (so customers don't get two emails).
- Judge.me's email stars deep-link to the product's review form (pre-filled
  with rating + product + order) — which is now live.

**3. (Optional) Add an All-Reviews display to `/pages/reviews`**
- Theme editor → open the **Reviews** page → **Add block** in the page section →
  under **Apps**, pick the Judge.me **All Reviews** (or **Reviews Carousel**)
  block → place it under the "Loved By You" video wall → **Save**.
- Saving also force-rolls the storefront cache so the gold branding above shows
  immediately.
- (Not scripted via CLI on purpose: this store's section-JSON render-cache means
  a template push won't display until a Save, so the editor is the reliable
  route.)

---

## Why Judge.me (vs a native Liquid form)

- Reviews **auto-publish** after one-click approval — no hand-copying.
- Produces **Google star snippets** — plain Liquid cannot.
- The review-request **email loop is native to the app** (pre-filled stars).
- **Free**, no monthly cost.
