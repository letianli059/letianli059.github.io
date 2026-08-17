# Letian Li — Personal Website

This repository contains the source for [letianli059.github.io](https://letianli059.github.io), built with the free, MIT-licensed [al-folio](https://github.com/alshedivat/al-folio) Jekyll starter.

The site intentionally contains only five public sections:

- About (`_pages/about.md`)
- Publications (`_bibliography/papers.bib` and `_pages/publications.md`)
- Talks (`_pages/talks.md`)
- Awards & Service (`_pages/awards.md`)
- CV (`_data/cv.yml` and `_pages/cv.md`)

Blog, projects, repositories, teaching, people, books, news, and submenu pages are intentionally absent until real content exists.

## Updating the site

You do **not** need to clone the repository again for every update. Reuse this local copy:

```powershell
Set-Location 'F:\Working\Personal Website'
git switch master
git pull --ff-only origin master
git switch -c content-update-YYYY-MM-DD
```

Edit the relevant Markdown, YAML, or BibTeX file, preview the result, then merge and push only after review.

## Local preview

The most isolated Windows workflow is Docker Desktop:

```powershell
docker compose up --build
```

Open <http://localhost:8080>. Stop the preview with `Ctrl+C`.

Without Docker, install Ruby 3.3.x with Devkit, Bundler 4.0.6, Node.js 20, and ImageMagick, then run:

```powershell
gem install bundler -v 4.0.6
bundle install
npm ci
bundle exec jekyll serve --livereload
```

## Publication conventions

Each BibTeX record uses one of these status values:

- `published`: shown under Published & forthcoming; verified entries include Abs, DOI, HTML, and PDF buttons when a stable PDF URL exists.
- `accepted`: shown in the same Published & forthcoming section and clearly labeled as awaiting online publication.
- `manuscript`: shown under Selected preprints with its own thumbnail and a per-entry submission status; `preprint_order` keeps revision entries first, followed by entries grouped by Letian's `author_position`.

Published, accepted, and manuscript entries use al-folio's native badge and thumbnail layout. Final PNG previews and fallback SVG placeholders live in `assets/img/publication_preview/`; each BibTeX record points to the active image through its `preview` field. Keep filenames lowercase and avoid spaces because GitHub Pages paths are case-sensitive. PDF source artwork in that directory stays local and is ignored by Git after its PNG export is created.

If an approved private-manuscript abstract is not yet available, omit the BibTeX `abstract` field so the Abs button remains hidden. Add it only after the author supplies the approved abstract.

## Deployment

`.github/workflows/deploy.yml` builds matching site changes pushed to `master` or `main` and publishes the generated `_site` directory to `gh-pages`.

For the first al-folio release:

1. Approve a local preview and give GitHub Actions read/write repository permission.
2. Merge the approved redesign into `master`, then wait for the **Deploy site** workflow to succeed and create `gh-pages`.
3. In **Settings → Pages**, select **Deploy from a branch**, choose `gh-pages` and `/(root)`, then wait for the Pages deployment to finish.

Until that release is approved, keep the redesign on its separate branch; pushing `al-folio-redesign` alone does not deploy it.
