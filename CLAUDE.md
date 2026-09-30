# CLAUDE.md

Personal academic website of Xiayu (Summer) Zhao, a PhD student in Civil Engineering at UIUC. Live at https://xiayu-zhao.github.io.
It is a Jekyll site built on the academicpages / Minimal Mistakes template.

## Workflow

- The owner edits in VS Code with Claude Code and pushes/opens PRs with **GitHub Desktop**. The steps are in [README-XY.md](README-XY.md).
- Work happens on a feature branch, then a PR goes into `master`. GitHub Actions deploys automatically after `master` is updated.
- Only commit, push or open a PR when the owner asks.
- The owner moves between computers. **This file is the handoff**: after meaningful work, update "Recent work / state" below so the next session can pick it up.
- Ruby, Jekyll and Docker may not be installed locally, so changes often can't be built here. Check Liquid, SCSS variable order and paths by hand, and tell the owner to check the deployed site.

## Where things live

| What | Where |
|---|---|
| Site config, sidebar author links | `_config.yml` |
| Top navigation | `_data/navigation.yml` |
| About / home page (includes the News list) | `_pages/about.md` |
| **My Life** page (`/my-life/`) | `_pages/markdown.md` (file name is historical) |
| Cat photo album (`/my-life/cat/`) | `_pages/my-cat.md`; images in `images/cat/web/` |
| Life-doctrine essay | `_pages/four-dimensional-life-doctrine.md` |
| Awards | `_pages/awards.md` |
| CV page, CV JSON, LaTeX CV | `_pages/cv.md`, `_data/cv.json`, `CV_latex/` |
| Publications | `_publications/*.md` (synced from Google Scholar) |
| News posts | `_posts/YYYY-MM-DD-slug.md` (shown at `/year-archive/`) |
| Custom `<head>` (fonts, favicons) | `_includes/head/custom.html` |
| Font variables | `_sass/_themes.scss` |
| Site-wide style overrides (blue theme, typography, cards, gallery) | `_sass/layout/_refinement.scss`, imported last in `assets/css/main.scss` |

## Conventions

- **Adding news**: create a post in `_posts/`, add a line to the News list in `_pages/about.md` (`<li><time datetime="YYYY-MM">Mon YYYY</time><span>…</span></li>`), and cross-link it from the relevant page (Awards, My Life) if it fits.
- **Colors** are CSS custom properties at the top of `_refinement.scss` (a blue palette with light and dark variants). Reuse `var(--theme-heading)`, `var(--theme-accent)` and so on rather than hard-coding colors.
- **Font**: the main typeface is **Cormorant Garamond** (with Noto Serif SC for Chinese), chosen to match the owner's game site Dear Z. It is set through `$main-font` in `_themes.scss` and loaded from Google Fonts in `head/custom.html`. Code and news dates stay monospace.
- **Images**: keep full-resolution originals, and serve resized copies (about 1600px full size plus about 640px `-thumb`) made with Python/Pillow, which is available locally.
- Internal links use `{{ '/path/' | relative_url }}`.

## Related sites (separate repos)

- Dear Z. (indie game site): https://xiayu-zhao.github.io/DearZ-web/ ; its preview image is saved here as `images/dearz-card.jpg`
- BubbleTodo: https://xiayu-zhao.github.io/BubbleTodo

## Recent work / state

- 2026-09: blue theme (branch `blue_theme`); Scholar publications synced; tennis news added (Sept 2026, Champaign Park District Labor Day tournament).
- 2026-09-30: added a cat album page and a Dear Z. card to My Life; added a link to The Sentinel's tennis coverage; switched the main font to Cormorant Garamond. Open question: The Sentinel lists the owner as winner of the Beginner/Intermediate **Consolation Final**, while the site says "first place". The owner needs to decide which wording to use.
