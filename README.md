# AVR – Effect of patch provenance on patch selection

Artefacts of the AVR experiment report (Sec. VIII). Starting from the provided `analysis_dataset.csv`, running `AVR.ipynb` from top to bottom regenerates all the other files.

## Contents

| File | Description |
|---|---|
| `analysis_dataset.csv` | Original wide file given by the instructors (96 rows, 102 columns), unchanged. |
| `AVR.ipynb` | Analysis notebook (course Colab template adapted to this experiment): reshaping to long format, decoding of the factor levels and of the `(SWAPPED)` tag, sanity checks, metrics, plots and statistical tests (paired Wilcoxon, sign tests, Fisher tests with Holm correction, GEE). |
| `metrics_long.csv` | 384 rows, one per review (96 reviewers × 4 rounds), with factor levels, S1, S2, the two metrics and the covariates. |
| `metrics_participants.csv` | 96 rows, one per reviewer, with H_p, A_p, Claude_p, Left_p and the two profiles. |
| `images/` | All figures of the report, as saved by the notebook. |
| `pyproject.toml`, `requirements.txt` | Python dependencies. |

## How to run

With [uv](https://docs.astral.sh/uv/):

```bash
uv sync
uv run jupyter notebook AVR.ipynb
```

Or with pip:

```bash
pip install -r requirements.txt jupyter
jupyter notebook AVR.ipynb
```

The notebook expects `analysis_dataset.csv` in the same folder; if it is not found, it opens a file dialog to choose it. Figures are written to `images/`, the two derived CSV files next to the notebook.

The analysis was run with Python 3.13.5, pandas 3.0.6, numpy 2.5.3, scipy 1.18.1, matplotlib 3.11.2, seaborn 0.13.2 and statsmodels 0.15.0. All computations are deterministic; the only random element (the jitter of the points in the rating-gap figure) uses a fixed seed.

## License

The notebook, the derived CSV files and the figures are released under the [MIT License](LICENSE). `analysis_dataset.csv` was provided by the course instructors and is not covered by this license.
