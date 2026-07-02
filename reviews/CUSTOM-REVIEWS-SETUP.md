# DWG Custom Reviews — how it works & how to run it

Dining With Gold's own product-review system. **Replaces Judge.me** (retired — see
`JUDGE-ME-SETUP.md`, now superseded). Fully branded, moderated, and independent of any
third-party review app. Built because DWG is a collaborator store where we can't mint a
Shopify Admin token, so reviews live in **our own Supabase database**, not in Shopify.

## Pieces

| Piece | Where |
|-------|-------|
| Theme section | `theme/sections/dwg-product-reviews.liquid` (wired into `templates/product.detail.json`, position 6) |
| Backend | repo `stackdbase/dwg-reviews-api` → **https://dwg-reviews-api.vercel.app** (Vercel, stackdbase account) |
| Database | Supabase project `udmynmslsxrrhnunziir` → table `public.reviews` |

## Flow
```
customer fills form ─POST /api/submit─▶ Supabase reviews (status = pending)
you approve  ─(Supabase Table Editor: status → published)─▶ visible
product page ─GET /api/list?product=<handle>─▶ published reviews + rating ─▶ rendered
```
Display is rendered client-side by the section's JS; it also injects JSON-LD `AggregateRating`
so Google can show star rich-snippets.

## ✅ Moderating reviews (your day-to-day)
1. Supabase → project `udmynmslsxrrhnunziir` → **Table Editor → `reviews`**.
2. New submissions have **status = `pending`**. Read one, then set **status → `published`**
   (or `spam`) and save.
3. It appears on the storefront within ~1 minute (60s edge cache).

## Redeploying the backend
```
cd ~/Projects/dwg-reviews-api
vc-stackdbase deploy --prod --yes
```
Env vars (already set in Vercel): `SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY`, `ALLOWED_ORIGINS`.
The service-role key is **only** in Vercel/`.env`, never in the theme.

## ⚠️ Editing the theme — IMPORTANT
Push from the repo **with `--path theme`**, or the CLI treats the repo root as the theme root
and silently uploads nothing:
```
NODE_OPTIONS="--dns-result-order=ipv4first" shopify theme push --path theme \
  --theme 198719209820 --only sections/dwg-product-reviews.liquid \
  --nodelete --allow-live --store 1tyg0m-3a.myshopify.com
```
Verify a push actually landed by pulling the same file back and grepping it.

## Anti-spam
- Honeypot field + server-side validation + manual moderation (nothing publishes unapproved).
- **Cloudflare Turnstile is OFF** (built-in but inert). To turn on later: create a Turnstile
  widget → put the **site key** in the section setting *Cloudflare Turnstile site key* and the
  **secret** as `TURNSTILE_SECRET` in Vercel env.

## Known trade-off
Reviews live outside Shopify, so the **star badge on product-collection cards** (Shopify's
`reviews.rating` metafield) is **not** populated. The **product page** reviews work fully.
If a Shopify Admin token ever becomes available from the store owner, we can sync those badges.

## Still to do (admin-side)
- **Review-request email:** point the post-purchase "leave a review" email at the product page
  (that's where reviews now live). Turn off any Judge.me review-request email if still enabled.
