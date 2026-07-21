# pvbhanuteja.github.io

Personal site for **Venkata Bhanu Teja Pallakonda** (Bhanu Pallakonda) —
AI researcher & engineer. Static HTML/CSS/JS, no build step, no dependencies.

## Design

Direction: **registry minimal**. The page treats public identifiers — patent
numbers, arXiv IDs, DOIs — as first-class design elements: serif prose in the
center, machine-readable mono metadata at the edges. No cards, no shadows, no
badges; hierarchy comes from type and whitespace.

| Token | Light | Dark |
|---|---|---|
| paper | `#fcfcfa` | `#16181d` |
| ink / muted / soft | `#1b1e24` / `#565d68` / `#7d838d` | `#e7e5e0` / `#a3a7ae` / `#7c818a` |
| rule | `#e6e7e9` | `#2a2e36` |
| accent | `#3d5a80` (résumé slate blue) | `#9cb9de` |

Type: **Newsreader** (display + italic thesis), **IBM Plex Sans** (body),
**IBM Plex Mono** (labels, registry IDs).

## Structure

```
index.html               — single-page content (semantic, static)
styles/
  tokens.css             — design tokens + light/dark themes (vars only)
  base.css               — reset, element defaults, focus/print/motion rules
  layout.css             — sidebar shell, hero, sections, footer
  components.css         — the .entry ledger pattern, .phases, .def-row, contact
main.js                  — theme toggle + footer year + sidebar scroll-spy (~40 lines)
favicon.svg              — monogram (also the sidebar mark)
assets/me.jpg            — optional headshot; the hero hides it if absent
resume.pdf               — downloadable résumé
```

Layout: a left sidebar carries all wayfinding (monogram, section nav with a
scroll-spy active state, résumé link, theme toggle). It collapses to a slim
sticky header on small screens. Drop a square photo at `assets/me.jpg` to show
the (grayscale, color-on-hover) headshot in the hero.

Everything on the page is built from one component: `.entry`
(title left, mono id right, note below). Systems, publications, patents, and
roles all reuse it — add a new item by copying an existing `<article class="entry">`.

## Preview locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy to GitHub Pages (user site)

The repo must be named exactly `pvbhanuteja.github.io`.

```bash
git init
git add .
git commit -m "Profile site"
git branch -M main
git remote add origin https://github.com/pvbhanuteja/pvbhanuteja.github.io.git
git push -u origin main
```

Then **Settings → Pages → Source: Deploy from a branch**, branch `main` / root `/`.
Publishes at `https://pvbhanuteja.github.io/`.

## Custom domain (optional — bhanu.cyou)

1. Add a `CNAME` file containing one line: `bhanu.cyou`
2. DNS: apex `A` records → `185.199.108.153`, `185.199.109.153`,
   `185.199.110.153`, `185.199.111.153`; `www` CNAME → `pvbhanuteja.github.io`
3. **Settings → Pages** → set custom domain, enable **Enforce HTTPS**
4. Update `canonical` / `og:url` in `index.html`

> The site links only public artifacts (Google Scholar, arXiv, DOIs, Google
> Patents). Proprietary Armada repositories are described but not linked.
