# Philip Ugbede Ododo — portfolio site

A static, single-page portfolio and résumé site built with plain HTML, CSS, and a little JS. It has no build step, so GitHub Pages can serve it as-is.

```
index.html                              page content
styles.css                              design tokens, layout, light/dark themes, print styles
script.js                               mobile menu + active-section highlight (optional enhancement)
assets/Philip-Ugbede-Ododo-Resume.pdf   downloadable résumé
assets/og-card.png                      link-preview image (LinkedIn, Slack, iMessage…)
assets/favicon.svg                      tab icon
.nojekyll                               tells GitHub Pages to serve files as-is
```

## Preview locally

```
npx http-server . -p 8080
```

Then open http://localhost:8080. Opening `index.html` straight from disk also works.

## Publish on GitHub Pages

### Option A: root site at https://philipododo.github.io/ (recommended)

The repo `philipododo/philipododo.github.io` already exists and already serves Pages from `main` at `/`. It currently holds two
notebooks and a README. Adding these files leaves the notebooks where they are, and `index.html` becomes the homepage.

```
git remote add origin https://github.com/philipododo/philipododo.github.io.git
git fetch origin
git merge origin/main --allow-unrelated-histories   # keeps the existing notebooks; on a README.md conflict, keep this repo's version
git push origin HEAD:main
```

The site goes live at https://philipododo.github.io/ within a minute or two. You can watch progress in the repo's **Actions** tab.

### Option B: separate repo at https://philipododo.github.io/resume/

```
gh repo create philipododo/resume --public --source . --push
gh api -X POST repos/philipododo/resume/pages -f "source[branch]=main" -f "source[path]=/"
```

If you choose Option B, update the three `https://philipododo.github.io/` URLs in the `<head>` of `index.html` (canonical, og:url, og:image)
to `https://philipododo.github.io/resume/`.

## Updating the résumé

Replace `assets/Philip-Ugbede-Ododo-Resume.pdf` with a new export under the same name, then commit and push. If the content changes,
update the matching text in `index.html` too.
