# CLAUDE.md

Guidance for Claude Code (claude.ai/code) when working in this repository.

## Rules

- When an author name appears with only a first initial (e.g. "D. Livne", "L. Khatib"),
  ask the user for the full first name. Do not guess what the initial stands for.
- Publication entries are transcribed verbatim from Adi's publication list. Keep the
  citation format as supplied (surname, initials) rather than normalizing it.
- Her surname changed over time: earlier papers are published as **Toledano-Zarhi, A.**
  and **Toledano, A.**, later ones as **Toledano-Shubi, A.** All three are her and are
  bolded in the author lists.

## Architecture

Plain HTML + CSS personal academic website. No build step — a single `index.html` plus
`stylesheet.css`. Deployed to GitHub Pages via `.github/workflows/jekyll-gh-pages.yml`.

### Key files

- `index.html` — the whole site
- `stylesheet.css` — Inter font, `--accent` #1772d0, `--accent-hover` #f09228, dark theme via `[data-theme="dark"]`
- `images/profile.jpg` — 1200×1200 square crop used for the circular avatar
- `images/profile-full.jpg` — full portrait, opened when the avatar is clicked
- `publication/<slug>/index.html` — permalink redirect stubs

### Sections in index.html

1. **Header** — name, three bio paragraphs, contact line
2. **Publications** — grouped by year, newest first (no featured/highlighted rows: the template's `bgcolor="#ffffd0"` highlight is deliberately not used)
3. **Abstracts in Refereed Journal Supplements** — conference abstracts
4. **Talks & Presentations** — newest first, `entry-tag` for Poster / Co-author / Opening lecture
5. **Bio** — Education, Research Grants, Awards, Teaching, Clinical & Professional Experience, Academic Service
6. **Beyond Research** — Ironman finisher

The template's Media Coverage section was removed. The inert `#media` and `.hike`
handlers remain in the tail script; they no-op until such markup exists.

### Verified external links

All external links were checked. Publisher DOIs return 403 to command-line clients
(bot blocking) but resolve to the correct article pages in a browser. The Scholar and
ORCID profiles were confirmed to be hers by name. The department link is
`https://hw.haifa.ac.il/pt-en/?lang=en` — note the department lives under the faculty
host `hw.haifa.ac.il`, not a `*.haifa.ac.il` subdomain of its own.

### Adding a publication

Add a `<tr id="<slug>">` to the publications table under the right `pub-year` heading:
badge in the left cell, then title link, author list (her name in `<strong>`), venue line,
an optional `<div class="small">` impact-factor line, `.pub-links`, and a hidden
`div id="cite-<slug>"` with the BibTeX. Then copy an existing `publication/<slug>/index.html`
stub so the permalink resolves.

### Local stylesheet change

`.section-head` wraps and `.expand-all` drops its `margin-left: auto` under the 620px
breakpoint. Without this the "Expand all" button forces ~10px of horizontal page overflow
on phones. The upstream template still has that quirk.

### Sources

Content comes from three documents Adi supplied:

- Hebrew CV (August 2026) — the most current; authoritative for the postdoc, grants,
  amounts, and the 2025/2026 talks
- `Publication list Adi Toledano Shubi.docx` (August 2026) — authoritative for the
  seven journal articles, their ordering, and the impact-factor/quartile lines
- English university CV (August 2025) — a year older, but authoritative for English
  wording: course names, conference and award titles, the dissertation title, and the
  funder spelling "Rina Brik Foundation"

Where the Hebrew CV and the English CV disagree (e.g. the KAMIN grant years and role),
the newer Hebrew CV wins.

### Still to fill in

- LinkedIn URL — there is a TODO comment in the `social-links` block in `index.html`.
- Full author lists for the CVPR 2022 and BIO2006 entries; both currently end in
  "et al." because the English CV abbreviates them, and neither has a DOI/paper link.
  These two are in the English CV but not on her August 2026 publication list.
