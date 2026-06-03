# Akademisk/profesjonell CV-nettside (Quarto)

Personlig nettside bygget med [Quarto](https://quarto.org): landing page, CV, forskning
(BibTeX-drevet), og en blogg som støtter kjørbar Python/R med interaktive grafer.

## Førstegangsoppsett

1. **Installer Quarto:** last ned fra <https://quarto.org/docs/get-started/>.
2. **Installer Python-avhengigheter** (for de kjørbare innleggene):
   ```bash
   pip install -r requirements.txt
   ```
   (For R-innlegg: installer pakkene du bruker, f.eks. `install.packages("ggplot2")`.)
3. **Bytt ut plassholdere** merket `[Etternavn]`, `dittbrukernavn`, `din@epost.no` i
   `_quarto.yml`, `index.qmd` og `cv.qmd`. Legg ditt eget bilde i `assets/profile.jpg`.

## Lokal forhåndsvisning

```bash
quarto preview
```
Åpner siden i nettleseren og oppdaterer automatisk når du lagrer.

## Lage nytt blogginnlegg

Kopier en mappe under `posts/`, gi den nytt navn (f.eks. `posts/2026-03-tittel/`),
og rediger `index.qmd`. Innlegg med kjørbar kode trenger `jupyter: python3`
(Python) eller `engine: knitr` (R) i frontmatter. Quarto plukker opp innlegget
automatisk i listingen.

## Publisering til GitHub Pages

To alternativer:

**A. Automatisk via GitHub Actions (anbefalt — kjører koden i skyen):**
Workflowen i `.github/workflows/publish.yml` render-er og deployer ved hver push til
`main`. I repo-innstillingene: *Settings → Pages → Source → GitHub Actions*.

**B. Manuelt fra egen maskin:**
```bash
quarto publish gh-pages
```

For en brukerside, kall repoet `dittbrukernavn.github.io` — da blir URL-en
`https://dittbrukernavn.github.io`.

## Struktur

```
.
├── _quarto.yml          # nettstedskonfig + navigasjon
├── styles.scss          # tema/styling
├── index.qmd            # landing page
├── cv.qmd               # CV
├── research.qmd         # publikasjoner (BibTeX)
├── blog.qmd             # blogg-listing
├── references.bib       # referanser
├── requirements.txt     # Python-avhengigheter
├── assets/              # bilder, CV-PDF
└── posts/               # blogginnlegg (én mappe per innlegg)
```
