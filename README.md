# Data Science Course — Università Cattolica del Sacro Cuore, Milano

**Instructor:** Paolo Balasso
**Format:** 3-day intensive master class
**Audience:** Business-oriented data science master students

---

This repository hosts the **Jupyter notebooks** used in the hands-on sessions of the course.
Each notebook is **self-contained** (synthetic data generators inside), runs end-to-end in ~30 seconds on a Colab CPU, and is designed for **content sedimentation** rather than production deployment.

## Notebooks

| # | Notebook | Topic | Open in Colab |
|---|----------|-------|----------------|
| 01 | [`01_churn_cost_threshold.ipynb`](notebooks/01_churn_cost_threshold.ipynb) | Churn — Beyond the Threshold | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/01_churn_cost_threshold.ipynb) |
| 02 | [`02_demand_eda_single_product.ipynb`](notebooks/02_demand_eda_single_product.ipynb) | Demand EDA — Single Product | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/02_demand_eda_single_product.ipynb) |
| 03 | [`03_demand_eda_multi_product.ipynb`](notebooks/03_demand_eda_multi_product.ipynb) | Demand EDA — Multi-Product Hierarchy | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/03_demand_eda_multi_product.ipynb) |
| 04 | [`04_portfolio_optimization.ipynb`](notebooks/04_portfolio_optimization.ipynb) | Portfolio Optimization — Macro Regime | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/04_portfolio_optimization.ipynb) |

## Notebook contents

### `01_churn_cost_threshold.ipynb` — Churn — Beyond the Threshold
Cost-based threshold, ROC vs PR, calibration, lift/gain, propensity binning.

### `02_demand_eda_single_product.ipynb` — Demand EDA — Single Product
STL decomposition, stationarity, ACF/PACF, outlier handling, naive/SNaive/ETS baselines, MAPE/WAPE/MASE.

### `03_demand_eda_multi_product.ipynb` — Demand EDA — Multi-Product Hierarchy
Mix problem / Simpson's paradox, WAPE vs MAPE, bottom-up vs top-down reconciliation, cannibalisation.

### `04_portfolio_optimization.ipynb` — Portfolio Optimization — Macro Regime
Markowitz, Investment Clock (FRED), Permanent (Browne) / All-Weather (Dalio), regime-aware tilt.

## Local installation

```bash
git clone https://github.com/paolobalasso/DataScienceCourse.git
cd DataScienceCourse
python -m venv .venv
source .venv/bin/activate   # on Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

Each notebook installs the few extra dependencies it needs in its first cell via `%pip install -q`. Re-running the cell in Colab is silent and idempotent.

## Pedagogical design notes

- **Exploratory & didactic** — short readable functions, lots of plots, explicit data-science hygiene (shapes, NaN, duplicates, train/test split).
- **Mini-exercises are parametric.** Students change a cost coefficient, a calibration method, a seasonal period — *not* re-implement the model. The goal is concept reinforcement.
- **Synthetic data generators** are versioned with the notebook so results are 100% reproducible.
- **Caveats sections** at the end of every notebook explicitly mark what would break the analysis in production (look-ahead bias, in-sample optimism, calibration drift, hard-threshold artefacts).

## Companion slide decks

The course uses three slide decks (not included in this public repo):
- `DS_Course_v7_Main_FIX8.pptx` — main 99-slide deck
- `DS_Course_v7_AdvancedTopics_FIX4.pptx` — 26-slide deep-dives (NN, GBT, finance markets extension)
- `DS_Course_v7_DemandMultiProduct.pptx` — 6-slide standalone deck for the hierarchical-demand session

## License

MIT — see [`LICENSE`](LICENSE).

## Citation

If you use any of this material in your teaching, please cite as:

```
Balasso, P. (2026). Data Science Master Class — Università Cattolica del Sacro Cuore, Milano.
https://github.com/paolobalasso/DataScienceCourse
```


## Starter dataset for the churn fallback exercise

For students who prefer to develop the analysis themselves before reading `01_churn_cost_threshold.ipynb`, the repo ships a starter CSV and a one-page brief:

- [`data/churn_starter.csv`](data/churn_starter.csv) — 5,000-row synthetic Telco-style dataset.
- [`data/churn_brief.md`](data/churn_brief.md) — challenge brief, deliverables, hints.

## Notebook 05 — Conjoint → Demand → Revenue

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/05_conjoint_demand_revenue.ipynb) [`notebooks/05_conjoint_demand_revenue.ipynb`](notebooks/05_conjoint_demand_revenue.ipynb)

End-to-end pricing pipeline: choice-based conjoint design → simulated respondents → MNL part-worth estimation → attribute importance & willingness-to-pay → market simulator → potential demand → revenue curve → bootstrap sensitivity.
