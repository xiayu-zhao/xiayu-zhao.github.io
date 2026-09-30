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
- **Colors** are CSS custom properties at the top of `_refinement.scss` (a blue palette). Reuse `var(--theme-heading)`, `var(--theme-accent)` and so on rather than hard-coding colors.
- **The site is dark-mode only.** The owner found the serif font too faint on the light background. `data-theme="dark"` is hard-coded on `<html>` in `_layouts/default.html` and `cv-layout.html`, the toggle was removed from `_includes/masthead.html`, and `setTheme` always uses dark. That change is in both `assets/js/_main.js` and the prebuilt `assets/js/main.min.js`; Node isn't installed locally, so `main.min.js` was patched by hand. The unused light variables are still in the CSS.
- **Portrait photo** appears only on the home page (`page.url == "/"` check in `_includes/author-profile.html`). Other pages still show the sidebar name and links.
- **Tab icon**: a "Z" with a dot, styled after the Dear Z. site icon, in the site's blues. The files are `images/favicon.svg`, `favicon.ico`, `favicon-*.png` and `apple-touch-icon-180x180.png`, all generated with Pillow.
- **Font**: the main typeface is **Cormorant Garamond** (with Noto Serif SC for Chinese), chosen to match the owner's game site Dear Z. It is set through `$main-font` in `_themes.scss` and loaded from Google Fonts in `head/custom.html`. Code and news dates stay monospace. Regular (400) looked too thin to the owner, so body text uses Medium (500) and headings and bold use 700. Only weights listed in the Google Fonts URL are available; add any new weight there too.
- **Images**: keep full-resolution originals, and serve resized copies (about 1600px full size plus about 640px `-thumb`) made with Python/Pillow, which is available locally.
- Internal links use `{{ '/path/' | relative_url }}`.

## Related sites (separate repos)

- Dear Z. (indie game site): https://xiayu-zhao.github.io/DearZ-web/ ; its preview image is saved here as `images/dearz-card.jpg`
- BubbleTodo: https://xiayu-zhao.github.io/BubbleTodo

## Recent work / state

- 2026-09: blue theme (branch `blue_theme`); Scholar publications synced; tennis news added (Sept 2026, Champaign Park District Labor Day tournament).
- 2026-09-30: added a cat album page (the cat is named **Cheese**, and the album has no captions) and a Dear Z. card to My Life; linked The Sentinel's tennis coverage; switched the main font to Cormorant Garamond.
- Tennis wording, decided by the owner: **consolation champion, Intermediate Open Singles, Champaign Park District Labor Day Tennis Tournament**. Don't call it "first place". The post URL still contains `first-place`, and was left alone to avoid breaking links.
