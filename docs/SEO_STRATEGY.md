# Dining With Gold — SEO Strategy

Last updated: 2026-09-23

## Diagnosis (why "dining with gold" doesn't surface yet)

The store is **technically crawlable** — this is not a robots/noindex block:

- `robots.txt` allows crawling; `sitemap.xml` is live (products, pages, blogs).
- Canonical URLs, meta description, Open Graph & Twitter cards are output by `snippets/meta-tags.liquid`.
- Structured data present: Organization (site-wide) + Product/Offer/Brand (product pages).

The real causes of low visibility are **discovery + authority**, not markup:

1. **Indexing lag / low crawl priority** — a newer store with little authority is crawled slowly and ranked below established results. Fix via Search Console (force re-crawl) + backlinks.
2. **"Dining With Gold" is a competitive, generic phrase** — competes with restaurants, jewelry, "fine dining" content. Brand-entity signals (schema `sameAs`, Google Business Profile, consistent NAP, social) teach Google the brand exists.
3. **Thin off-site footprint** — few backlinks / brand mentions / social profiles linked as `sameAs`.

## What's implemented in the theme (redesign branch)

`snippets/dwg-seo-schema.liquid` (rendered from `layout/theme.liquid`):

- **Organization** (site-wide): name, url, logo, description, email, `sameAs` (Instagram + any social links set in theme settings). Deduplicated — removed the old Organization block from `header.liquid`.
- **WebSite + SearchAction** (home): enables the Google sitelinks search box.
- **Product + Offer + Brand** (product pages): restored after the custom PDP (`dwg-rd-product-hero`) had replaced the default product section that carried it.
- **BreadcrumbList** (product + collection): breadcrumb rich results.

Head basics already handled by `snippets/meta-tags.liquid`: `<title>` (with shop-name suffix), meta description, canonical, OG, Twitter cards, product price OG.

> Note: These take effect on the live store **when the redesign theme is published**. The live theme already carries the base meta + Organization/Product schema.

## Keyword targets

Primary: `african chilli oil`, `nigerian chilli oil`, `travel chilli oil`, `chilli oil spray`, `spicy chilli oil UK`.
Brand: `dining with gold`, `dining with gold chilli oil`.
Long-tail / content: `best chilli oil for noodles`, `how to use chilli oil`, `chilli oil on eggs`, `gift chilli oil`.

## Owner actions (highest impact — cannot be done from the theme)

See `SEO_CHECKLIST.md`. In priority order: Search Console re-crawl → Google Business Profile → social `sameAs` → backlinks/PR → content/blog cadence.

## Content plan (blog — builds long-tail + authority)

Publish 1–2 posts/month targeting the long-tail keywords, each linking to the product:
- "5 ways to use African chilli oil" (noodles, eggs, dumplings, grilled meat, veg)
- "African vs Asian chilli oil — what's the difference"
- "Why our chilli oil comes in a travel spray"
- "The story behind Dining With Gold"
