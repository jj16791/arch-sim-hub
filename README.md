# SC26 BoF — community hub (Jekyll site)

The website for the SC26 Birds of a Feather *"The State of Open-Source Computer Architecture Simulators: Shared Problems and Community Action."* Built with [Jekyll](https://jekyllrb.com/) so it builds natively on GitHub Pages.

## Structure

```
_config.yml                     site settings (title, baseurl, url)
Gemfile                         Ruby dependencies (github-pages gem)
index.html                      landing page  (layout: default, home: true)
sca-hpcasia26-summary.html      SCA/HPCAsia26 outcomes summary (layout: page)
_layouts/
  default.html                  page skeleton: <head>, nav, content, footer
  page.html                     content pages: red hero from front matter + <main>
_includes/
  head.html  nav.html  footer.html  dots.html   reusable partials
_data/
  themes.yml                    the six discussion themes (edit here to change cards)
assets/css/
  main.scss                     the University of Bristol theme (compiled to main.css)
```

**To change the themes**, edit `_data/themes.yml` — the cards on the landing page are generated from it.
**To change styling/branding**, edit `assets/css/main.scss`.
**To add a page**, drop an `.html`/`.md` file with `layout: page` front matter (see the summary page).

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
3. Push. In the repo, **Settings → Pages → Build and deployment → Source: Deploy from a branch**, pick the branch and folder. GitHub Pages builds the Jekyll site automatically — no Actions needed.

## Branding

University of Bristol identity: University Red (`#a6192e`) primary, grey (`#e5e6e5`) call-out panels, Sora headings / Open Sans body, and the Three Dots motif in the hero. Colours and type live in `assets/css/main.scss`.

*Still a draft: panellist names are held until the line-up is locked; the contribution guide and post-SC channel are placeholders.*
