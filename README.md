# vallee.no — personal CV site (Quarto, bilingual)

Minimal academic CV site built with [Quarto](https://quarto.org), in English and
Norwegian. English is the default language served at the root domain.

## Structure

```
_quarto.yml         # base config + profile group (en, nb)
_quarto-en.yml      # English profile  -> _site/en  (navbar in English)
_quarto-nb.yml      # Norwegian profile -> _site/nb (navbar in Norwegian)
index.qmd           # home / about (LinkedIn + e-mail)
cv.qmd              # CV
cv-extended.qmd     # detailed CV (courses, roles, projects)
styles.scss         # theme
assets/profile.jpg  # portrait
CNAME               # custom domain
```

Both languages live in the same `.qmd` files. Content is switched with
`::: {when-profile="en"} ... :::` and `::: {when-profile="nb"} ... :::` blocks,
so the two versions stay side by side in one file.

## Build locally

Preview one language at a time:

```bash
quarto preview --profile en
quarto preview --profile nb
```

Render both (what CI does):

```bash
quarto render --profile en
quarto render --profile nb
```

## Publish

Pushing to `main` triggers `.github/workflows/publish.yml`, which renders both
profiles into `_site/en` and `_site/nb`, writes a root redirect (`/` -> `/en/`)
and the `CNAME`, and deploys to GitHub Pages.

Repo settings: *Settings -> Pages -> Source -> GitHub Actions*.

## Language toggle

The navbar "EN"/"NO" link points to `../en/` or `../nb/`. Note: switching
language always lands on the other language's home page, not the equivalent
sub-page (a known limitation of the profile approach — fine for a small site).
