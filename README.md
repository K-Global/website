# K Global — public website

The public recruitment / marketing website for **K Global**, a fictional
VATSIM virtual airline. Built with [MkDocs](https://www.mkdocs.org/) and the
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme, and
deployed to GitHub Pages via GitHub Actions on every push to `main`.

> **Live URL:** https://k-global.github.io/website/ (unless a custom domain is
> configured — see [`HANDOFF.md`](HANDOFF.md)).

## Local preview

Requires Python 3.9+.

```bash
pip install -r requirements.txt
mkdocs serve
```

Then open <http://127.0.0.1:8000>. The site rebuilds live as you edit.

To reproduce the exact build CI runs (fails on broken links / nav):

```bash
mkdocs build --strict
```

## Project layout

```
website/
├── .github/workflows/deploy.yml   # Build + deploy to GitHub Pages
├── docs/                          # All site content (Markdown)
│   ├── index.md                   # Homepage (hero via overrides/home.html)
│   ├── about.md
│   ├── network/                   # Network overview + hubs
│   ├── business-units/            # The nine units
│   ├── fleet/                     # Fleet by category
│   ├── flying/                    # Events & incentives
│   ├── join.md                    # Primary call to action
│   ├── stylesheets/extra.css      # Brand colours (single source of truth)
│   └── assets/                    # Logo, favicon, imagery (some placeholders)
├── overrides/home.html            # Homepage hero template
├── mkdocs.yml                     # Site + theme configuration
├── requirements.txt               # Pinned build dependencies
└── HANDOFF.md                     # What the owner still needs to do
```

## Editing content

- Content is plain Markdown under `docs/`. Nav is defined in `mkdocs.yml`.
- **Rebranding** is a one-file change: edit the colour tokens at the top of
  `docs/stylesheets/extra.css`.
- Placeholders (the join URL and some imagery) are called out in
  [`HANDOFF.md`](HANDOFF.md) and flagged inline in the relevant files.

## A note on scope

This is the public shop window only. It intentionally omits internal
operations detail (dispatch mechanics, IDs, numbering schemes, decision
records). Keep it that way — if a fact reveals how the back office runs rather
than making the airline appealing to a prospective pilot, it doesn't belong
here.
