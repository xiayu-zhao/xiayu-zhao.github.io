# CLAUDE.md

Personal academic website of Xiayu (Summer) Zhao, a Ph.D. candidate in Civil Engineering at UIUC. Live at https://xiayu-zhao.github.io.
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
| CV page (the one linked in the nav) | `_pages/cv.md`. Keep it in sync with the LaTeX CV. |
| LaTeX CV and its PDF (linked from the CV page) | `CV_latex/CV_XiayuZhao.tex` plus `publications.tex`. Rebuild with `pdflatex` (MiKTeX is installed) run twice from inside `CV_latex/`. |
| Source notes the owner gives for CV updates | `cv_sources/` (for example `PatentList.txt`, `updating-review_list.txt`) |
| `_data/cv.json` / `/cv-json/` | Leftover template placeholder data that isn't used. Ignore it. |
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
- **Shell quirk**: in Bash heredocs on this machine, an escaped backslash (`"\\begin"`) inside a Python string arrives as `"\begin"`, which Python reads as a backspace character. For scripts that contain LaTeX backslashes, write a `.py` file and run it instead.

## Related sites (separate repos)

- Dear Z. (indie game site): https://xiayu-zhao.github.io/DearZ-web/ ; its preview image is saved here as `images/dearz-card.jpg`
- BubbleTodo: https://xiayu-zhao.github.io/BubbleTodo

## Recent work / state

- 2026-09: blue theme (branch `blue_theme`); Scholar publications synced; tennis news added (Sept 2026, Champaign Park District Labor Day tournament).
- 2026-09-30: added a cat album page (the cat is named **Cheese**, and the album has no captions) and a Dear Z. card to My Life; linked The Sentinel's tennis coverage; switched the main font to Cormorant Garamond.
- Tennis wording, decided by the owner: **consolation champion, Intermediate Open Singles, Champaign Park District Labor Day Tennis Tournament**. Don't call it "first place". The post URL still contains `first-place`, and was left alone to avoid breaking links.
- 2026-10-07: added a "Patent & Software Copyright Applications" section to the LaTeX CV and the website CV (4 patents and 3 software copyrights, all in process with UIUC OTM), and updated the reviewer lists (5 journals, 8 conferences), from `cv_sources/`.
- 2026-10-07 (revision): the patent section is now titled "Patent & Software Copyright" and sits directly before Publications. Its note says the applications are processed by UIUC OTM "for United States Provisional Application". Research Interests were rewritten from the 2024-2026 papers. Removed the China Architecture Design & Research Institute internship, the empty "Professional Committees" heading, and the "two similar 2021 records" note (from the CV, the website and the `_publications` front matter). `CV_latex/publications.tex` is generated by `scripts/build_cv_publications.py`, so edit that script rather than the `.tex` file.
- 2026-10-07: Research Interests shortened to about half (same text in the PDF and on the website). **The PDF CV must stay at 6 pages.** That needed margins of 0.7in, section spacing of 9pt/5pt and tighter spacing between publication entries. Check `pdfinfo` after every CV edit.
- 2026-10-08: the owner's title is now **"Ph.D. Candidate"** everywhere (CV, website, sidebar bio). Dissertation title added. The CV header "Web" link now points to https://xiayu-zhao.github.io/ (the RAISe lab URL was removed there). MCS coursework is summarized by category from `cv_sources/courses-uiuc.txt`. The Tsinghua and Tianjin degrees use the owner's wording ("Master's Degree" / "Bachelor's Degree"). Removed the Tianjin VR-lab Student Assistant and Model Slicing Co-designer entries. ICRA 2027 is the first conference-reviewer item. In the PDF, "Invited Interviews, Exhibitions and Speeches" now comes after Professional Leadership & Service, with the empty Invited Interviews placeholder removed. The PDF is still 6 pages.
- 2026-10-08 (minor revision): removed "construction safety" from the MCS coursework, the Master's Thesis entry, the Penn State TA and team names, and the IASS 2023 abstract. Renamed the section to "Exhibitions and Invited Speeches". **Publication curation, decided by the owner:** the 2021 "Research Progress and Application Status of 3D Printing Construction Technology" record was deleted from `_publications/` (it is a near-duplicate of the "...Current Applications..." paper), and the tafoni paper (Architectural Intelligence 2022) is filed as `category: conferences`. Don't bring either back when re-syncing from Google Scholar. The owner chose to keep the scholarships and awards that now appear under both the Bachelor's degree and Awards & Honors, and to keep the RAISe lab links on the website.
