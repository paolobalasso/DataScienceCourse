# Data Science Master Class — Università Cattolica del Sacro Cuore, Milan

- **Instructor:** Paolo Balasso
- **Format:** 3-day intensive master class, taught in English
- **Audience:** business-oriented master students, from first-time Python users to quantitative profiles

---

This repository contains the **Jupyter notebooks** used in the hands-on sessions of the course, the files of the **pricing group exercise** and an optional **churn practice dataset**.
The notebooks are written to help concepts stick: short readable code, many plots, and small "change one parameter" exercises. They are teaching material, not production code.

## Quick start (no installation)

1. Click an **Open in Colab** badge in the table below. You only need a Google account.
2. In Colab, choose **File → Save a copy in Drive**, so your changes are kept.
3. Run the cells from top to bottom (**Runtime → Run all**).

On Colab there is nothing else to set up: everything the notebooks need is already installed, or is installed by the first code cell.

## Notebooks

| # | Notebook | Topic | Data | Open in Colab |
|---|----------|-------|------|---------------|
| 01 | [`01_churn_cost_threshold.ipynb`](notebooks/01_churn_cost_threshold.ipynb) | Churn — beyond the 0.5 threshold | synthetic, generated in the notebook | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/01_churn_cost_threshold.ipynb) |
| 02 | [`02_demand_eda_single_product.ipynb`](notebooks/02_demand_eda_single_product.ipynb) | Demand EDA — single product | synthetic, generated in the notebook | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/02_demand_eda_single_product.ipynb) |
| 03 | [`03_demand_eda_multi_product.ipynb`](notebooks/03_demand_eda_multi_product.ipynb) | Demand EDA — multi-product hierarchy | synthetic, generated in the notebook | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/03_demand_eda_multi_product.ipynb) |
| 04 | [`04_portfolio_optimization.ipynb`](notebooks/04_portfolio_optimization.ipynb) | Portfolio optimisation and macro regimes | public market and macro data, downloaded at run time; automatic synthetic fallback if the download fails | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/04_portfolio_optimization.ipynb) |
| 05 | [`05_conjoint_demand_revenue.ipynb`](notebooks/05_conjoint_demand_revenue.ipynb) | Conjoint analysis → demand → revenue | synthetic, generated in the notebook | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/05_conjoint_demand_revenue.ipynb) |
| 06 | [`06_pricing_starter.ipynb`](notebooks/06_pricing_starter.ipynb) | Pricing group exercise — starter canvas | [`data/retail_pricing_exercise.csv`](data/retail_pricing_exercise.csv) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/06_pricing_starter.ipynb) |

Notebooks 01, 02, 03 and 05 generate their own data and run end-to-end in under a minute on a laptop; allow about a minute on a free Colab CPU.
Notebook 04 downloads market and macro data from two public services. If a download fails, it switches automatically to clearly labelled synthetic data and says so in a banner: the code still runs, but the numbers are then illustrative, not market facts.

## What each notebook covers

**01 · Churn — beyond the 0.5 threshold.**
ROC vs precision-recall curves under class imbalance, probability calibration, lift and gain charts, from probabilities to action tiers in euros, and the cost-based decision threshold chosen on a validation set.

**02 · Demand EDA — single product.**
STL decomposition, stationarity, ACF/PACF, outlier handling, baseline forecasts (naive, seasonal naive, Holt-Winters), MAPE / WAPE / MASE, residual checks.

**03 · Demand EDA — multi-product hierarchy.**
How aggregation hides SKU-level errors, WAPE vs MAPE on a hierarchy (and why MAPE breaks on intermittent products), bottom-up vs top-down reconciliation (and when they coincide), cannibalisation between substitute products.

**04 · Portfolio optimisation and macro regimes.**
Returns and correlations of a small ETF universe, macro data from FRED, a simplified Investment Clock, seven portfolios (Markowitz optimisers, rule-based portfolios and the 60/40 benchmark), in-sample vs out-of-sample results, and a regime-aware tilt tested honestly. *Educational material only, not investment advice.*

**05 · Conjoint analysis → demand → revenue.**
Choice-based conjoint design, simulated respondents with heterogeneous preferences, an aggregate logit model and its limits, attribute importance and willingness to pay, a market simulator, the revenue curve, and bootstrap uncertainty on the optimal price.

**06 · Pricing group exercise — starter canvas.**
The starting canvas for your group: setup steps, data loading with a check that you have the current dataset, sections that follow the deliverables with clock-time checkpoints, the line that saves the elasticity file, and a small syntax toolbox (tools only, no answers). It loads the exercise dataset directly from this repository.

## Group exercise: pricing optimisation

The graded group exercise uses these files:

- [`data/pricing_brief.md`](data/pricing_brief.md) — business question, data dictionary, deliverables. **Read it first, end to end.**
- [`data/retail_pricing_exercise.csv`](data/retail_pricing_exercise.csv) — synthetic retail panel, 40 products × 24 months.
- [`data/pricing_presentation_template.pptx`](data/pricing_presentation_template.pptx) — slide template for your final presentation.
- [`notebooks/06_pricing_starter.ipynb`](notebooks/06_pricing_starter.ipynb) — starter notebook.

The brief gives the timeline, the deliverables and the file names. Groups are formed at the launch; the submission channel is announced in class.

## Practice dataset: churn

If you want to build a churn analysis yourself before opening notebook 01:

- [`data/churn_starter.csv`](data/churn_starter.csv) — 5,000-row synthetic telco-style dataset.
- [`data/churn_brief.md`](data/churn_brief.md) — short brief with deliverables and hints.

This exercise is optional and not graded.

## Running the notebooks on your own computer

You need Python 3.10 or newer.

```bash
git clone https://github.com/paolobalasso/DataScienceCourse.git
cd DataScienceCourse
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

Notebook 06 reads the dataset from GitHub and falls back to the local copy in `data/` when there is no internet connection. If the copy it finds is not the current one, it stops and asks you to download the file again.

## Repository structure

```
DataScienceCourse/
├── notebooks/          six teaching notebooks (01-06)
├── data/               datasets, exercise briefs, presentation template
├── requirements.txt    Python packages for local use
├── LICENSE             MIT
└── README.md
```

## Slides

The full course slides are shared with participants as PDF at the end of the course. A PDF excerpt of the pricing theory slides (without speaker notes) is shared at the exercise launch on Day 2. Slides are not part of this repository.

## Questions

During the course, ask in class: questions are welcome at any time.

## License

MIT — see [`LICENSE`](LICENSE). The datasets are synthetic, except the public market and macro series that notebook 04 downloads at run time from their original providers.

## How to cite

```
Balasso, P. (2026). Data Science Master Class — Università Cattolica del Sacro Cuore, Milan.
https://github.com/paolobalasso/DataScienceCourse
```
