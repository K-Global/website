# Handoff — K Global website

The site is built, passes `mkdocs build --strict` with zero warnings, and is
wired to deploy to GitHub Pages via GitHub Actions on every push to `main`.
It's now branded to the **K Global Brand Guidelines v1.0** (Marine Teal accent
on a monochrome core; Inter Tight / Inter / B612 Mono; "Go further, together")
and configured for the custom domain **kglobalair.com**. A few things need
**you** (Miguel) to finish.

## 1. Turn on Pages + custom domain (required — nothing is live until this)

> ⚠️ The first deploy after the initial merge **failed** because Pages wasn't
> enabled yet. Do this and it'll go green.

In **`K-Global/website` → Settings → Pages**:

1. **Source: GitHub Actions**
2. **Custom domain:** `kglobalair.com` → Save (this repo already ships
   `docs/CNAME` with that domain, and `site_url` is set to match).
3. Tick **Enforce HTTPS** once the certificate is issued.

### DNS to add at your domain registrar (for the apex `kglobalair.com`)

| Type | Name | Value |
|---|---|---|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |

(If you also want `www.kglobalair.com` to work, add a `CNAME` record
`www → k-global.github.io`.) DNS can take a little while to propagate before
GitHub will issue the HTTPS certificate.

After Pages is enabled, re-run the latest **Actions → Deploy** workflow if it
had already failed once.

## 2. Supply the join URL (required to convert visitors)

The primary call to action points at a placeholder, **`{{JOIN_URL}}`**.

- File: `docs/join.md` — replace `{{JOIN_URL}}` in the "Apply to join" button
  `href` with the real VAMSYS / VATSIM signup URL, and delete the
  "Join link coming soon" warning admonition just below it.
- While you're there, confirm the join **requirements** listed on that page
  (VATSIM account, a simulator, a VAMSYS profile) match your actual onboarding.

## 3. Drop in real brand assets (recommended)

The logo and favicon are **placeholders** built in the brand style (paddler
symbol + wordmark, mono + Marine Teal). Replace with the real artwork from the
brand guide:

| Asset | Where | Status |
|---|---|---|
| `docs/assets/logo.svg` | Header lockup | Placeholder — swap for `wordmark-light.png` / `symbol.png` |
| `docs/assets/favicon.svg` | Browser tab icon | Placeholder — swap for the real symbol |
| `docs/assets/route-map.png` | `docs/network/index.md` | **Missing** — styled placeholder block |
| Fleet / livery hero shot | `docs/fleet/index.md` | **Missing** — styled placeholder block |

The brand-guide asset PNGs (`symbol.png`, `wordmark-light/dark.png`, unit
lockups) weren't included with the guidelines file — send them and I'll wire
them in. When you add the route map / fleet image, swap the `.kg-placeholder`
blocks (marked with HTML comments) for `![alt](../assets/route-map.png)` tags.

> All brand colour and type live in `docs/stylesheets/extra.css` — a rebrand is
> a one-file edit.

## What was deliberately left out

This is the public shop window only. Per the brand direction it reads as a
**community-driven premium VA** ("a premium place to fly, learn and belong"),
with no back-office detail: no VAMSYS IDs/API, no numbering schemes, no ops
internals. Public figures are rounded and type-level only (~421 aircraft, ~848
city pairs, ten hubs, nine units). No registration nationality or single
radio-callsign is asserted (the brand guide's `G-KGLB` / `EGLL` are treated as
illustrative specimens). The stale `KGlobal_Fleet_Catalog.xlsx` was **not** used.

## Local preview

```bash
pip install -r requirements.txt
mkdocs serve            # http://127.0.0.1:8000
mkdocs build --strict   # reproduce the CI build
```
