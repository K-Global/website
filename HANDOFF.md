# Handoff — K Global website

The site is built, passes `mkdocs build --strict` with zero warnings, and is
wired to deploy to GitHub Pages via GitHub Actions on every push to `main`.
A few things need **you** (Miguel) to finish — none block the build, but the
site isn't fully "live and converting" until they're done.

## 1. Turn on GitHub Pages (required — the deploy won't publish without it)

In **`K-Global/website` → Settings → Pages**, set:

- **Source: GitHub Actions**

That's it. The included workflow (`.github/workflows/deploy.yml`) handles build
and deploy. Once Pages source is set to GitHub Actions and a commit lands on
`main`, the site publishes to:

> **https://k-global.github.io/website/**

The first push may need the workflow to run once *after* Pages is enabled — if
the very first deploy errors on Pages not being configured, just re-run the
workflow (Actions tab → Deploy → Run workflow) once the setting is in place.

## 2. Supply the join URL (required to convert visitors)

The primary call to action currently points at a placeholder, **`{{JOIN_URL}}`**.

- File: `docs/join.md` — replace `{{JOIN_URL}}` in the "Apply to join" button
  `href` with the real VAMSYS / VATSIM signup URL, and delete the
  "Join link coming soon" warning admonition just below it.
- The same placeholder note is worth a scan elsewhere, but this is the only
  live spot.
- While you're there, confirm the join **requirements** listed on that page
  (VATSIM account, a simulator, a VAMSYS profile) match your actual onboarding.

## 3. Drop in real brand assets (recommended)

Everything works with placeholders today, but these should be replaced with
real artwork. See `docs/assets/README.md` for the full list. In short:

| Asset | Where | Status |
|---|---|---|
| `docs/assets/logo.svg` | Header wordmark | Placeholder (CSS/SVG stand-in) |
| `docs/assets/favicon.svg` | Browser tab icon | Placeholder |
| `docs/assets/route-map.png` | `docs/network/index.md` | **Missing** — currently a styled placeholder block |
| Fleet / livery hero shot | `docs/fleet/index.md` | **Missing** — currently a styled placeholder block |

When you add the route map and a fleet image, swap the `.kg-placeholder`
blocks (marked with HTML comments in those two pages) for normal
`![alt](../assets/route-map.png)` image tags.

> **Note:** the brand palette (deep navy + warm gold) is a deliberately
> legally-distinct homage — it does **not** reproduce any real airline's logo
> or trademarked colour. All brand colour lives in
> `docs/stylesheets/extra.css`; a rebrand is a one-file edit.

## 4. Decide on a custom domain (optional)

Without a custom domain the site serves at `https://k-global.github.io/website/`
and `site_url` in `mkdocs.yml` already reflects that.

If you want a custom domain (e.g. `www.kglobal.example`):

1. Add it in **Settings → Pages → Custom domain**.
2. Add a `docs/CNAME` file containing just the domain.
3. Update `site_url` in `mkdocs.yml` to the new domain.

## What was deliberately left out

Per the brief, this is the public shop window only. None of the internal
`Knowledge/` material is published — no VAMSYS IDs or API details, no
flight-number / callsign-numbering scheme, no decision records or status
notes, no per-hub ops detail, no fleet ID tables or sizing formulas. Public
figures are rounded and type-level only (~421 aircraft, ~848 city pairs, ten
hubs, nine units). The stale `KGlobal_Fleet_Catalog.xlsx` was **not** used.

## Local preview

```bash
pip install -r requirements.txt
mkdocs serve      # http://127.0.0.1:8000
mkdocs build --strict   # reproduce the CI build
```
