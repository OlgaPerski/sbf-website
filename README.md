# Svensk Beteendemedicinsk Förening – website

Bilingual (Swedish/English) Quarto website for the Swedish Society of Behavioural Medicine (SBF). It is published automatically to GitHub Pages whenever changes are pushed to `main`.

## Preview locally

```bash
quarto preview
```

## How the two languages work

- Swedish pages live in the project root and English pages in `en/`. Each Swedish page has an English twin (e.g. `om.qmd` ↔ `en/about.qmd`).
- The **English / Svenska** link in the menu always goes to the matching page in the other language. The pairs are listed at the top of `_lang-switch.html`, which also relabels the menu in English on English pages.
- **Shared content (edit once, shows in both languages):** news posts (`nyheter/`), lunch talks (`lunchseminarier/`) and the board (`styrelse.yml`). News posts and talk pages are written in one language only; the toggle on those pages goes to the other language's news or lunch-talk list.
- **When you change a normal page, update its twin as well.**

## Common tasks

| Task | How |
|---|---|
| **Add a news post** | Copy a file in `nyheter/`, rename it `YYYY-MM-DD-short-title.qmd`, and edit the title, date, description and text. It appears on both news pages and both home pages automatically. |
| **Add a lunch talk** | Copy a file in `lunchseminarier/` and set `status: kommande` (upcoming). After the talk, change it to `status: tidigare` (past) and add recording/slides links. |
| **Update the board** | Edit `styrelse.yml` (name, Swedish + English role, affiliation, photo). Put photos in `images/board/`. |
| **Add a new page** | Create the Swedish page and its English twin in `en/`, add the Swedish page to the navbar in `_quarto.yml`, and add the pair (with its English menu label) to `PAIRS` in `_lang-switch.html`. |
| **Change colours/fonts** | Edit the variables at the top of `styles.scss`. |

Search the project for `TODO` to find placeholder content that still needs to be filled in.

## Structure

```
_quarto.yml          site config + navigation (Swedish labels)
_lang-switch.html    language toggle + English menu labels
styles.scss          theme (colours, fonts, components)
styrelse.yml         board members (used by om.qmd and en/about.qmd)
_board.ejs           template for the board cards
index.qmd            home                  en/index.qmd
om.qmd               about + board         en/about.qmd
lunchseminarier.qmd  lunch talks           en/lunch-talks.qmd
nyheter.qmd          news                  en/news.qmd
medlemskap.qmd       membership            en/membership.qmd
resurser.qmd         resources             en/resources.qmd
kontakt.qmd          contact               en/contact.qmd
nyheter/             news posts (shared)
lunchseminarier/     lunch talks (shared)
.github/workflows/   GitHub Actions publish workflow
```

## Publishing (one-time setup)

In the GitHub repo, go to **Settings → Pages → Build and deployment → Source** and choose **GitHub Actions**. After that, every push to `main` re-publishes the site.
