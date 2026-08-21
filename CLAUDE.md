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

The template's Media Coverage and Beyond Research sections were removed. The inert
`#media` and `.hike` handlers remain in the tail script; they no-op until such markup exists.

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

### Still to fill in

- Google Scholar, ORCID, and LinkedIn URLs — the `social-links` block in `index.html` is
  commented out until these are known.
