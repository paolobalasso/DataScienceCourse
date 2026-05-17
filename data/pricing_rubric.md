# Pricing Optimisation — Grading Rubric

Total: **30 points** (Italian system). Pass: 18. Honours (lode) require 30 + outstanding business framing.

| # | Dimension | Weight | What we check |
|---|---|---:|---|
| 1 | **Analytical rigour** | 25% | Are the elasticities reasonable? (We compare to the ground truth; median absolute error below 0.30 = full marks.) Is the EDA aligned with the modelling choice? |
| 2 | **Confounder handling** | 25% | Have you reasoned about which variables to include? Did you avoid the obvious traps (e.g. using `inventory_level` as a predictor of demand)? Did you defend your choice on `promo_flag`? |
| 3 | **Business framing** | 20% | Is the business lever clearly isolated and explained? Is the recommendation actionable (which product, which direction, what uplift)? Would the CFO act on this? |
| 4 | **Communication & storytelling** | 20% | Does the deck follow a clear narrative arc (Situation → Complication → Question → Answer, or equivalent)? Are charts readable by a non-technical reader? Is there a one-sentence executive summary? |
| 5 | **Methodological honesty** | 10% | Have you stated the limits of your analysis? Are there caveats (e.g. no cross-price elasticity, no causal identification beyond observational)? Bonus for the team that says "we tried X and rejected it because Y". |

## Indicative grade bands

| Score | What it looks like |
|---|---|
| **28-30** | Recovered elasticities to within 0.25 of truth on average. Defended every control variable. Recommendation is one CFO-ready sentence with a number attached. Slides feel like a McKinsey deliverable. |
| **24-27** | Solid model with one or two interpretation errors. Business framing is present but generic. Good rigor, decent storytelling. |
| **21-23** | Reasonable approach but missed at least one major confounder (e.g. left `inventory_level` in, or did not handle seasonality). Recommendation is technically correct but not business-actionable. |
| **18-20** | Methodology works but story is weak. Or: story is great but the numbers are not defensible. |
| **< 18** | Major analytical error (e.g. predicted demand from inventory level and reported R²=0.85), or no recommendation, or no caveats. |

## Mechanical anti-patterns that cap your grade

- Using **XGBoost / Random Forest / Neural Network as the primary model** without a defensible elasticity estimate → **maximum 18/30**. A black-box model that cannot answer "what happens if I change the price by 5%?" is not a pricing model.
- Including **`inventory_level`** as a predictor of demand without a one-paragraph justification → **−3 points** (it is measured at end-of-period and is mostly a consequence of demand, not a cause).
- Quoting an elasticity with **no confidence interval** → **−2 points**.

## What gets you the bonus

- A team that explicitly compares two modelling strategies (e.g. naive OLS vs OLS-with-controls) and explains *why* they chose one. Up to **+2 points**.
- A team that quantifies the **revenue uplift** of their recommendation in euros, with an honest range. Up to **+2 points**.

Maximum achievable (with bonuses): **30 e lode**.
