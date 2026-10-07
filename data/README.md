# Dataset

The notebooks use public Amazon product review data that was part of the original coursework workflow.

The raw dataset is intentionally not duplicated here.

Expected fields used by the notebooks include:

- `reviews.text`
- `reviews.rating`
- `name`
- product / category metadata

Sentiment mapping used in the transformer workflow:

- ratings 1â€“2 -> negative
- rating 3 -> neutral
- ratings 4â€“5 -> positive

For a fully reproducible public version, the next iteration should document the exact public dataset URL and add a deterministic data-download / preprocessing script.