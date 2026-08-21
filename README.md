# AdiToledanoShubi.github.io

Personal academic website for **Adi Toledano-Shubi** — postdoctoral researcher in the
Department of Physical Therapy at the University of Haifa, researching remote fall
prevention and telehealth assessment for older adults.

## Structure

Plain HTML + CSS, no build step required.

- `index.html` — the entire site (header/bio, publications, abstracts, talks, bio)
- `stylesheet.css` — styles (Inter font, light/dark theme toggle, responsive layout)
- `images/` — `profile.jpg` (square avatar crop) and `profile-full.jpg` (full portrait, opened when the avatar is clicked)
- `publication/<slug>/index.html` — one redirect stub per publication, so
  `.../publication/<slug>/` is a stable citable permalink to that entry's anchor
- `data/` — local PDFs for publications or talks without a public host

## Local preview

```
python3 -m http.server 4000
```

Then open http://localhost:4000.

## Deployment

Push to `main`; the GitHub Actions workflow in `.github/workflows/jekyll-gh-pages.yml`
deploys the repository root to GitHub Pages.

To serve at `https://aditoledanoshubi.github.io`, the repo must live in a GitHub account
named `AdiToledanoShubi`. Under a different account it is served as a project site at
`https://<account>.github.io/AdiToledanoShubi.github.io/`; update the absolute URLs in
`index.html` (canonical, Open Graph, JSON-LD), `robots.txt`, `sitemap.xml`, and the
`publication/*/index.html` stubs if the final domain changes.

## Credits

Based on the [Jon Barron template](https://github.com/jonbarron/jonbarron.github.io),
adapted through [Keren Gruteke Klein's fork](https://github.com/KerenGruteke/KerenGruteke.github.io)
and [Omer Shubi's site](https://github.com/OmerShubi/omershubi.github.io), then via the
[academic website template](https://github.com/OmerShubi/academic-website-template).
