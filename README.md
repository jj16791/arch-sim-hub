# Open-Source Architecture Simulators — community hub (Jekyll site)

The public hub for the recurring Birds of a Feather session on the state of open-source computer architecture simulators. Built with [Jekyll](https://jekyllrb.com/) so it builds natively on GitHub Pages. The landing page always carries whichever venue is current; past venues are archived and always reachable from the "Previous sessions" section.

## Structure

```
_config.yml                     site settings (title, baseurl, url)
Gemfile                         Ruby dependencies (github-pages gem)
index.html                      landing page — the CURRENT venue's content (layout: default, home: true)
venues/
  sca-hpcasia26-bof.html             archived venue page (layout: page)
_layouts/
  default.html                  page skeleton: <head>, nav, content, footer
  page.html                     content pages: red hero from front matter + <main>
_includes/
  head.html  nav.html  footer.html  dots.html   reusable partials
_data/
  themes.yml                    the current venue's discussion themes (edit here to change cards)
  panel.yml                     the current venue's panel cards
  venues.yml                    every venue this hub has run at — drives the "Previous sessions" list
assets/css/
  main.scss                     the University of Bristol theme (compiled to main.css)
```

**To change the current venue's themes/panel**, edit `_data/themes.yml` / `_data/panel.yml`.
**To change styling/branding**, edit `assets/css/main.scss`.
**To add a standalone page**, drop an `.html`/`.md` file with `layout: page` front matter (see `venues/sca-hpcasia26-bof.html`).

## Rolling the landing page to a new venue

When the current venue concludes and a new one is confirmed:

1. Move `index.html`'s content into `venues/<old-slug>.html` (front matter `layout: page`, same pattern as `venues/sca-hpcasia26-bof.html`).
2. In `_data/venues.yml`, flip that entry's `status` to `past` and set its `url` to `/venues/<old-slug>.html`.
3. Write the new venue's content into `index.html` (hero, about, themes, format, panel, outcomes — themes/panel come from `_data/themes.yml` / `_data/panel.yml`, so update those too).
4. Add the new venue's entry to `_data/venues.yml` with `status: current` and `url: "/"`.

The "Previous sessions" section on the landing page loops `site.data.venues` for every `status: past` entry automatically — nothing else needs hand-editing.

## Run locally

Requires Ruby (3.x) and Bundler.

```
cd website
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000>.

## Deploy to GitHub Pages

1. Put this `website/` folder in a repo (either as the repo root, or as `/docs` with Pages set to serve from `/docs`).
2. In `_config.yml`, set `url` and `baseurl`:
   - User/org site (`<user>.github.io`): `baseurl: ""`.
   - Project site (`<user>.github.io/<repo>`): `baseurl: "/<repo>"`.
   (All internal links use `relative_url`, so they follow `baseurl` automatically.)
3. Push. In the repo, **Settings → Pages → Build and deployment → Source: Deploy from a branch**, pick the branch and folder. GitHub Pages builds the Jekyll site automatically — no Actions needed. Note: on a free GitHub plan, Pages can only build from a **public** repo, so flip visibility before enabling Pages.

## Branding

University of Bristol identity: University Red (`#a6192e`) primary, grey (`#e5e6e5`) call-out panels, Sora headings / Open Sans body, and the Three Dots motif in the hero. Colours and type live in `assets/css/main.scss`.
