# Dining With Gold

Monorepo for the **Dining With Gold** (DWG) Shopify store — a UK travel-sized
chilli oil brand. https://diningwithgold.com

## Structure

| Path | What it is |
|------|------------|
| [`theme/`](./theme) | The Shopify **Horizon** theme (live storefront). Pushed to the store via Shopify CLI. |
| [`email-flow/`](./email-flow) | Email marketing assets — the 3-step welcome flow, post-purchase review email, the marketing knowledge base, and setup guides (Markdown + PDF + .docx). |

## Theme

- Platform: Shopify (Basic plan, UK / GBP), **Horizon** theme.
- Store (permanent domain): `1tyg0m-3a.myshopify.com`
- Deploy: Shopify CLI, e.g.
  ```bash
  shopify theme push --theme <id> --store 1tyg0m-3a.myshopify.com --only <file> --nodelete --allow-live
  ```
  Note: if pushes report a network error, retry with
  `NODE_OPTIONS="--dns-result-order=ipv4first"`.

## Email flow

See [`email-flow/SETUP-GUIDE.md`](./email-flow/SETUP-GUIDE.md) for build steps and
[`email-flow/DWG-Email-Marketing-Knowledge-Base.md`](./email-flow/DWG-Email-Marketing-Knowledge-Base.md)
for the full knowledge base. The welcome flow is built in Shopify
**Messaging → Automations** (signup → Day 3 → Day 7).
