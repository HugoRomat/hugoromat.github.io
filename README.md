# Hugo Romat — Personal Website

A single-page personal/academic portfolio for **Hugo Romat, Ph.D.**, Senior Research
Engineer at Microsoft Research. Static HTML/CSS/JS — no build step required to deploy.

The design is compact and quiet: a soft pastel gradient backdrop, Manrope type, small
uppercase eyebrows, and white cards with inset media. All content, copy, and code here are Hugo's own.

## Structure

```
index.html              # The whole page (hero, Journey, Projects, Recognition, Experience, Publications, Education)
styles.css              # All styling
script.js               # Cite popovers, copy-to-clipboard, smooth scroll, active-nav highlight
robots.txt              # Search-engine crawling rules and sitemap location
sitemap.xml             # Search-engine sitemap for the site
assets/
  hugo.png              # Portrait (Open Graph image)
  hugo-400.jpg          # Optimized portrait served to browsers
  favicon.svg           # "HR" favicon
  logos/                # Institution logos (placeholders): microsoft, eth, inria, ensc, laval
  media/                # Local animated project previews
  pubs/                 # Publication thumbnails (<pub-id>.jpg)
  pdfs/                 # Publication PDFs (<pub-id>.pdf)
fonts/                   # Self-hosted Manrope fonts
```

Images and project GIFs are served locally; rendering the page does not
depend on external media hosts or Google Fonts. External profile and publication
links remain unchanged.

## Run locally

```powershell
python -m http.server 8099
# then open http://localhost:8099/
```

## Replace the placeholder assets

The site works immediately, but swap these for the real thing:

| File | What to drop in |
| --- | --- |
| `assets/hugo-400.jpg` | Portrait shown in the hero (`assets/hugo.png` is used for social previews). |
| `assets/logos/*.svg` | Official institution logos (keep the same filenames, or update the `src`s). |

Profile photo and paper thumbnails are picked up automatically when present;
until then the site shows tasteful placeholders.

## Update the profile links

The hero links to Google Scholar, DBLP, ACM, and LinkedIn — all four point at the real
profiles. To change any of them, edit `index.html` (search for `scholar.google`,
`dblp.org`, `dl.acm.org`, and `linkedin.com`).

## Journey

The `#journey` section has three chapters (`#area-ai`, `#area-ink`, `#area-data`). Each has
Why it matters, Impact, a media strip, Key papers (linking to `#pub-<id>` entries, which
scroll to and highlight the paper), and Product impact.

## Publications

The publication list is hand-authored directly in `index.html` (the year-grouped
`<ol class="pub-list">` blocks inside the `#research` section). To add, edit, or
remove a paper, edit that HTML by hand. Each entry carries its own authors, venue label,
optional award badge (`<span class="award">…</span>`), DOI/arXiv links, and BibTeX block.
Each entry also has a `.pub-thumb` image from `assets/pubs/` and, when available, a PDF
link to `assets/pdfs/<pub-id>.pdf`, where `<pub-id>` is the `<li>` id without `pub-`.

## Deploy

The site is deployed with GitHub Pages at <https://hugoromat.github.io/>. Push to the
default branch and enable Pages from the branch root. If the deployment URL changes,
also update the canonical and Open Graph URLs in `index.html`, plus `robots.txt` and
`sitemap.xml`.
