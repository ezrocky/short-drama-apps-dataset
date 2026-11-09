# Short Drama Apps Dataset

Store ratings, install counts, in-app prices, aggregated user-review complaint shares and data-based scores for the short drama (vertical micro-drama) apps ranked by Vertical Drama Reviews. Updated weekly, with a monthly snapshot archive.

Published by [Vertical Drama Reviews](https://verticaldramareviews.com). Dataset page: https://verticaldramareviews.com/data

Last updated: 2026-11-09. Apps: 25.

## Files

| File | What it is |
| --- | --- |
| [`data/short-drama-apps.csv`](data/short-drama-apps.csv) | Current snapshot, CSV (UTF-8, header row, comma-separated) |
| [`data/short-drama-apps.json`](data/short-drama-apps.json) | Current snapshot, JSON (same values, plus field definitions) |
| [`data/history/short-drama-apps-2026-11.csv`](data/history/short-drama-apps-2026-11.csv) | Monthly snapshot for 2026-11 (never changed after it's written) |

The same files are served at https://verticaldramareviews.com/data/short-drama-apps.csv and https://verticaldramareviews.com/data/short-drama-apps.json.

## Fields

| Field | Description | Source | Unit |
| --- | --- | --- | --- |
| `slug` | Stable identifier of the app at Vertical Drama Reviews. | Vertical Drama Reviews | text |
| `name` | App name. | App Store / Google Play listing | text |
| `developer` | Developer or publisher. | App Store / Google Play listing | text |
| `platforms` | Platforms the app is available on. In the CSV, values are separated by ";". | App Store / Google Play listing | list |
| `app_store_rating` | Average user rating on the US App Store, as returned by Apple (not rounded). | App Store (US) | stars, 1–5 |
| `app_store_ratings_count` | Number of ratings behind app_store_rating. | App Store (US) | count |
| `google_play_rating` | Average user rating on Google Play (US), as returned by Google (not rounded). | Google Play (US) | stars, 1–5 |
| `google_play_ratings_count` | Number of ratings behind google_play_rating. | Google Play (US) | count |
| `google_play_installs` | Lower bound of the install range shown on Google Play (for example, "100,000,000+" becomes 100000000). | Google Play (US) | installs |
| `price_from_usd` | The "from" price shown on our site: the cheapest item in the App Store's top in-app purchases list, or the low end of the Google Play price range when the App Store lists none. Apple shows only the most popular in-app purchases on an app's page (up to 10), not the full price list. Empty if neither store lists prices. | App Store / Google Play (US) | USD |
| `iap_price_min_usd` | Lowest price in the App Store's top in-app purchases list. Apple shows only the most popular in-app purchases on an app's page (up to 10), not the full price list. Cheaper items may exist. | App Store (US), top in-app purchases | USD |
| `iap_price_max_usd` | Highest price in the App Store's top in-app purchases list. Apple shows only the most popular in-app purchases on an app's page (up to 10), not the full price list. More expensive items may exist. | App Store (US), top in-app purchases | USD |
| `subscription_seen_in_app_store_top_iaps` | true if a subscription appears in the App Store's top in-app purchases list. Empty means unknown, not "no subscription": Apple shows only the most popular in-app purchases on an app's page (up to 10), not the full price list. The value is never false. | App Store (US), top in-app purchases | true / empty |
| `review_sample_size` | Number of recent user reviews analyzed (App Store and Google Play combined). | App Store / Google Play user reviews | reviews |
| `review_period_start` | Date of the oldest analyzed review. | App Store / Google Play user reviews | YYYY-MM-DD |
| `review_period_end` | Date of the newest analyzed review. | App Store / Google Play user reviews | YYYY-MM-DD |
| `complaint_share_billing` | Share of analyzed reviews that complain about unexpected charges or auto-renewal. | Recent App Store and Google Play user reviews, labeled by theme automatically | share of analyzed reviews, 0–1 |
| `complaint_share_ads` | Share of analyzed reviews that complain about too many ads. | Recent App Store and Google Play user reviews, labeled by theme automatically | share of analyzed reviews, 0–1 |
| `complaint_share_paywall` | Share of analyzed reviews that say the paywall comes too early or there are too few free episodes. | Recent App Store and Google Play user reviews, labeled by theme automatically | share of analyzed reviews, 0–1 |
| `complaint_share_bugs` | Share of analyzed reviews that report crashes, playback or login bugs. | Recent App Store and Google Play user reviews, labeled by theme automatically | share of analyzed reviews, 0–1 |
| `praise_share_content` | Share of analyzed reviews that praise the shows themselves. | Recent App Store and Google Play user reviews, labeled by theme automatically | share of analyzed reviews, 0–1 |
| `data_based_score` | Our overall score for the app, the same number shown on Vertical Drama Reviews. Computed by a published formula from store data and user reviews (see How we test). | Vertical Drama Reviews | points, 0–10 |
| `score_rank` | Position in our ranking (1 = highest score). | Vertical Drama Reviews | rank |
| `checked_at` | Latest date any value in this row was collected (store ratings, store listing, prices or review analysis). | Vertical Drama Reviews | YYYY-MM-DD |

Empty cells mean the value is not available. Numbers are unformatted (no thousands separators, no currency signs).

### Things to know

- **Apple shows only the most popular in-app purchases** on an app's App Store page, not the full price list. `iap_price_min_usd`, `iap_price_max_usd` and `subscription_seen_in_app_store_top_iaps` describe that top list only. An empty `subscription_seen_in_app_store_top_iaps` means unknown, not "no subscription".
- Store data comes from the US App Store and US Google Play.
- Complaint and praise shares come from a sample of recent user reviews that were labeled by theme automatically. One review can count toward several themes. Raw reviews are not included.
- `data_based_score` and `score_rank` are the same values shown on Vertical Drama Reviews. The formula is described at https://verticaldramareviews.com/how-we-test.

## Methodology

Every week Vertical Drama Reviews collects ratings and listings from the App Store and Google Play, analyzes a sample of recent user reviews and recomputes scores. This dataset is exported from the same data that powers the site. Full methodology: https://verticaldramareviews.com/how-we-test

## License

[Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0). You can share and adapt the data for any purpose, including commercial, as long as you give credit:

> Source: Vertical Drama Reviews (https://verticaldramareviews.com/data)

## How to cite

Vertical Drama Reviews (2026). Short Drama Apps Dataset [Data set]. https://verticaldramareviews.com/data. Licensed under CC BY 4.0.

```bibtex
@misc{vdr_short_drama_apps_2026,
  author       = {{Vertical Drama Reviews}},
  title        = {Short Drama Apps Dataset},
  year         = {2026},
  howpublished = {\url{https://verticaldramareviews.com/data}},
  note         = {Version of 2026-11-09. Licensed under CC BY 4.0},
}
```

GitHub shows a "Cite this repository" button based on [`CITATION.cff`](CITATION.cff). Each monthly release is archived on Zenodo with its own DOI.

## Updates

Files are updated weekly. A new monthly snapshot is added to `data/history/` in the first update of each month, and each monthly snapshot gets a release ([releases](https://github.com/ezrocky/short-drama-apps-dataset/releases)).
