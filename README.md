# Unveiling the Android App Market

An analysis of Google Play Store data — cleaning it, exploring how apps are
distributed across categories, and looking at what ratings, size, install counts
and price say about the market.

Built with pandas, matplotlib and Plotly. Both datasets are included, so the
notebook runs on a fresh clone with nothing else to download.

## Contents

| File | What it is |
|---|---|
| [`playstore-analysis.ipynb`](playstore-analysis.ipynb) | The analysis — 33 cells, all output preserved |
| [`playstore analysis .html`](playstore%20analysis%20.html) | Rendered export, viewable without Jupyter |
| `apps.csv` | 9,659 apps — category, rating, reviews, size, installs, type, price, genre, Android version |
| `user_reviews.csv` | 64,295 reviews — app, translated text, sentiment, polarity, subjectivity |
| `android app.docx` | Written report |

> The notebook is 6 MB because every chart is embedded. GitHub sometimes
> declines to render files that large — if the preview fails, the HTML export
> shows the same thing.

## What the analysis covers

**Data preparation** — counts nulls per column, drops incomplete rows, checks
dtypes, and summarises with `describe()` before anything else happens.

**Category exploration** — lists the distinct categories, ranks them by app
count, and plots the distribution as a bar chart.

**Metric analysis** — separate summaries and distribution plots for the four
things that characterise an app:

| Metric | How it's shown |
|---|---|
| Rating | histogram, 20 bins |
| Size | boxplot, to expose spread and outliers |
| Installs | histogram of download counts |
| Price | summary statistics |

**Review text preparation** — loads the review dataset and normalises
`Translated_Review` through a `clean_text` function that strips non-alphabetic
characters and lowercases the result.

**Interactive charts** — key relationships rebuilt in Plotly so they can be
hovered and zoomed: installs by category, rating against size with app names on
hover, and the rating distribution.

## Running it

```bash
git clone https://github.com/les-k/unveiling-the-android-app-market.git
cd unveiling-the-android-app-market
pip install -r requirements.txt
jupyter notebook playstore-analysis.ipynb
```

The notebook reads both CSVs from the working directory, so start Jupyter from
the repository root.

## Scope

Two things this project sets up but doesn't finish, worth stating plainly rather
than leaving a reader to discover:

- **Sentiment is prepared, not scored.** Review text is cleaned and ready, but no
  polarity model or lexicon is applied. `user_reviews.csv` already ships with
  `Sentiment`, `Sentiment_Polarity` and `Sentiment_Subjectivity` columns that the
  notebook doesn't yet touch — that's the obvious next step.
- **The analysis is descriptive.** It characterises the market; it doesn't model
  or predict anything.

## License

MIT — see [LICENSE](LICENSE).
