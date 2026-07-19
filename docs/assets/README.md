# Asset placeholders

This folder holds the site's brand imagery. Some assets are **placeholders**
generated during the build and should be replaced with real artwork from the
K Global brand guidelines.

| File | Status | Notes |
|---|---|---|
| `logo.svg` | **Placeholder** | Paddler + wordmark lockup used in the header. Replace with the real brand lockup (`wordmark-light.png` / `symbol.png`). Keep it light — it sits on the dark Ink header bar. |
| `favicon.svg` | **Placeholder** | Paddler symbol on Ink. Replace with the real K Global symbol. |
| `route-map.png` | **Missing** | World route map with the ten hubs. Referenced on `docs/network/index.md` (currently a styled placeholder block). |
| Fleet / livery shots | **Missing** | A hero livery image would lift `docs/fleet/index.md`. |

Brand colours and type live in `docs/stylesheets/extra.css` (single source of
truth): Marine Teal accent on a monochrome core; Inter Tight / Inter / B612
Mono. Replacing these files does not require touching Markdown except where a
`.kg-placeholder` block should become an `![...](...)` image tag.
