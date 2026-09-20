# Engineering portfolio

A three-page static site — home, projects, about. No build step, no dependencies,
no framework. Plain HTML and one stylesheet, which means it will still work in
five years when you come back to update it.

```
index.html      Home — title block, selected work, contact
projects.html   Full project list
about.html      Bio, experience, skills
style.css       Everything visual
assets/         Your photo, résumé PDF, project images (create this)
```

## Put it online

1. Create a repo. If you name it `your-username.github.io` the site lives at
   `https://your-username.github.io`. Any other name puts it at
   `https://your-username.github.io/repo-name/`.
2. Push these files to the repo root — `index.html` must be at the top level.
3. In the repo, go to **Settings → Pages**, set **Source** to *Deploy from a
   branch*, pick `main` and `/ (root)`, and save.
4. Wait a minute, then load the URL. Every push after that redeploys.

To preview locally, run `python3 -m http.server` in this folder and open
`http://localhost:8000`.

## Make it yours

Replace these before you publish. Most appear on all three pages, so use your
editor's find-and-replace across the whole folder.

| Find | Replace with |
| --- | --- |
| `Jordan Reyes` | Your name |
| `Mechatronics engineer` | Your discipline |
| `you@example.com` | Your email |
| `your-username` | Your GitHub username |
| `your-handle` | Your LinkedIn handle |

Then, by hand:

- **Hero** in `index.html` — the intro paragraph and the four title-block
  fields (discipline, location, status, date). The chartreuse field is the one
  thing on the page that shouts, so keep the most useful fact there. If you are
  not job-hunting, make it something else worth shouting.
- **Projects** — each project is one `<article class="entry">` block. Copy a
  block to add one, delete a block to remove one. The right-hand `<dl class="spec">`
  is a parameter/value table; add or drop `<dt>`/`<dd>` pairs freely.
- **About** — swap the placeholder `<div class="portrait">` for
  `<div class="portrait"><img src="assets/portrait.jpg" alt="Your name"></div>`.
- **Résumé** — drop `resume.pdf` in the repo root, or update the footer link.

## Change the look

Everything lives in the token block at the top of `style.css`:

```css
--paper:   #ECEFF0;  /* page background */
--ink:     #0E2029;  /* all primary text */
--signal:  #C8F04A;  /* the one accent, used as a flat fill */
```

Change `--signal` and you re-skin the site. Dark mode is handled automatically
from the visitor's system setting — the overrides are in the
`prefers-color-scheme` block just below the tokens.

Fonts are Archivo (headings, UI) and Source Serif 4 (body text), loaded from
Google Fonts in each page's `<head>`. To swap them, change that `<link>` and the
`--sans` / `--serif` tokens.

## Notes

- The header and footer are copied into all three pages. There is no templating,
  so if you change one, change all three.
- Accessibility is built in: skip link, visible keyboard focus, `aria-current`
  on the active nav item, and reduced-motion support. Try not to remove it.
- Add a `CNAME` file containing your domain if you want a custom one, then point
  a CNAME DNS record at `your-username.github.io`.
