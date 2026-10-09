# Academic portfolio (Hugo + PaperMod theme)

This project is configured for **PaperMod**
(https://github.com/adityatelange/hugo-PaperMod). All design, CSS, and HTML
rendering comes from the theme — nothing here overrides its layouts or
styling. I could not vendor the theme itself in this delivery (no network
access on my end); the one command below pulls it in.

## 1. Install the theme

```
cd papermod-site
git init   # if this isn't already a git repo
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive
```

## 2. Run locally

```
hugo server
```

Visit `http://localhost:1313`.

## 3. Fill in the placeholders

- `hugo.toml` — name, tagline, bio, social links (github/linkedin/email), meta description, keywords
- `content/about.md` — bio only
- `content/resume.md` — education, experience, skills, plus a link to the downloadable PDF
- `content/projects/project-1.md`, `project-2.md` — rename/duplicate for each real project; fill in title, summary, tags, body, repo link
- `static/resume.pdf` is a placeholder PDF (just says "INSERT RESUME CONTENT HERE") — replace it with your real resume, same filename, so the download link on the Resume page keeps working

## 4. Verify config fields against the theme

Theme param names can shift between versions. After adding the theme,
cross-check this `hugo.toml` against
`themes/PaperMod/exampleSite/config.yml` (ships with the theme) — if a
section (socialIcons, homeInfoParams, etc.) doesn't render, match the
field names there.

## 5. Deploy to GitHub Pages

Requires a GitHub Actions workflow (Hugo isn't natively built by GitHub
Pages the way Jekyll is). Minimal example at `.github/workflows/hugo.yml`:

```yaml
name: Deploy Hugo site
on:
  push:
    branches: ["main"]
permissions:
  contents: read
  pages: write
  id-token: write
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: recursive
      - uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: "latest"
          extended: true
      - run: hugo --minify
      - uses: actions/upload-pages-artifact@v3
        with:
          path: ./public
  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4
```

`submodules: recursive` in checkout matters — without it, the theme folder
is empty in CI and the build fails.

Then enable Pages in repo Settings → Pages → Source → GitHub Actions.
# hugofolio
