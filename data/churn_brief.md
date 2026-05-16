# Churn Challenge — Starter Dataset

**File:** `data/churn_starter.csv` (5,000 rows, synthetic Telco-style).
**Goal:** build a churn-scoring pipeline **without** looking at `notebooks/01_churn_cost_threshold.ipynb` first. Use the notebook only to compare your approach at the end.

## Columns

| Column | Type | Notes |
|---|---|---|
| `customerID` | str | identifier — drop before modelling |
| `SeniorCitizen` | int (0/1) | |
| `Partner`, `Dependents` | Yes/No | |
| `tenure` | int (months) | 0-72 |
| `PhoneService`, `MultipleLines` | categorical | watch the "No phone service" category |
| `InternetService` | DSL / Fiber optic / No | |
| `OnlineSecurity`, `TechSupport`, `StreamingTV` | Yes/No/No internet service | |
| `Contract` | Month-to-month / One year / Two year | strongest single predictor |
| `PaperlessBilling`, `PaymentMethod` | categorical | |
| `MonthlyCharges`, `TotalCharges` | float | **TotalCharges has ~1.5% NaN** |
| `Churn` | Yes/No | **target** |

## Deliverables

1. **EDA (max 6 plots)** — churn rate by contract, by tenure-bucket, by InternetService, by PaymentMethod, by MonthlyCharges decile, plus one correlation heatmap.
2. **Baseline model** — LogisticRegression with one-hot encoding. Report ROC-AUC and PR-AUC.
3. **Cost-based threshold** — assume `C_FP = 5 EUR` (a wasted retention voucher), `C_FN = 250 EUR` (lost customer LTV). Compute the optimal threshold and the corresponding savings vs the default 0.5.
4. **Calibration** — plot a reliability diagram. Decide if calibration is needed; if yes, apply Platt or isotonic and re-evaluate.
5. **Top-decile lift** — what fraction of churners are captured by the top 10% of scored customers?
6. **One-page summary** — three bullets answering: *who churns*, *when to intervene*, *how much we save*.

## Hints (don't peek unless stuck)

- `TotalCharges` NaN are concentrated on `tenure == 0` customers. Drop them or impute with 0.
- Use `pd.get_dummies(..., drop_first=True)` or `sklearn.preprocessing.OneHotEncoder(handle_unknown="ignore")`.
- For the cost threshold: `tau* = C_FP / (C_FP + C_FN)`. With these costs, `tau* ≈ 0.0196`. That sounds tiny but it is correct — the asymmetry of the costs *should* push you to be aggressive in flagging.
- Don't tune the threshold on the test set if you also tune hyperparameters there. Use a separate holdout or CV.

## Comparison

Once you have your numbers, open `notebooks/01_churn_cost_threshold.ipynb` and compare:
- Did you find the same top-3 features?
- Is your optimal threshold within a factor of 2 of the notebook's?
- Did you remember calibration before computing expected cost?

Good luck. The point of this exercise is not to win a Kaggle leaderboard — it is to feel where the **business** decision sits inside the **statistical** pipeline.
