# Asset placeholders

This folder holds the site's brand imagery. Some assets are **placeholders**
generated during the initial build and should be replaced with real artwork.

| File | Status | Notes |
|---|---|---|
| `logo.svg` | **Placeholder** | Text/SVG wordmark used in the header. Replace with the real K Global logo (keep it light — it sits on the navy header bar). |
| `favicon.svg` | **Placeholder** | "K" + globe favicon. Replace with the real favicon. |
| `route-map.png` | **Missing** | World route map with the ten hubs. Referenced on `docs/network/index.md` (currently a styled placeholder block). Drop the file here and swap the placeholder for an image. |
| Fleet / livery shots | **Missing** | A hero livery image would lift `docs/fleet/index.md`. |

Brand colours live in `docs/stylesheets/extra.css` (single source of truth).
Replacing these files does not require touching any Markdown except where a
`.kg-placeholder` block needs to become an `![...](...)` image tag — those
spots are marked with HTML comments in the relevant pages.
