# Dining With Gold — SEO Checklist

## A. Theme / on-page (done on `redesign` branch)
- [x] Organization schema enriched (logo, description, email, `sameAs`) — `snippets/dwg-seo-schema.liquid`
- [x] WebSite + SearchAction (sitelinks search box) on home
- [x] Product + Offer + Brand schema restored on PDP
- [x] BreadcrumbList schema on product + collection
- [x] Removed duplicate Organization block from `header.liquid`
- [x] Title / meta description / canonical / OG / Twitter (via `meta-tags.liquid`)
- [ ] Add an on-page **FAQ section** + FAQPage schema (needs visible Q&A copy)
- [ ] Descriptive **alt text** on every product/lifestyle image (Shopify admin per image)

## B. Google Search Console (already set up) — force discovery
- [ ] **URL Inspection → Request indexing** for: home, `/collections/all`, each product, key pages
- [ ] **Sitemaps** → confirm `sitemap.xml` submitted and "Success"
- [ ] **Pages** report → check "Why pages aren't indexed"; fix any "Discovered/Crawled – not indexed"
- [ ] **Removals / Enhancements** → confirm Products & Breadcrumbs show under "Enhancements" after publish
- [ ] Set the preferred domain / confirm https + non-www canonical matches Shopify

## C. Bing Webmaster Tools
- [ ] Verify site, submit sitemap (import from Search Console is quickest)

## D. Brand entity signals (teaches Google the brand)
- [ ] **Google Business Profile** — create/claim, category, logo, link to site
- [ ] Link all socials and set them as `sameAs` in theme settings (Instagram ✓, add Facebook/TikTok/YouTube/X if any)
- [ ] Consistent brand name + description across all profiles

## E. Off-site authority (backlinks)
- [ ] Product/press features (food blogs, local UK/Nigerian food press)
- [ ] Directory + marketplace listings
- [ ] Influencer/UGC posts linking to the site (you already have review videos — repurpose)

## F. Shopify admin SEO settings (owner)
- [ ] Online Store → Preferences: homepage **title & meta description** (brand-led, ~60 / ~155 chars)
- [ ] Each product/collection/page: fill "Search engine listing" (title + description)
- [ ] Confirm storefront **not password-protected** (blocks indexing entirely)

## G. Post-publish verification
- [ ] Run home + a product URL through Google **Rich Results Test** — Organization, WebSite, Product, Breadcrumb valid
- [ ] Re-check `site:diningwithgold.com` in Google after 1–2 weeks
