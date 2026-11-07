# Pricing Optimisation — Group Exercise

- **Dataset:** [`data/retail_pricing_exercise.csv`](retail_pricing_exercise.csv) (960 rows, 16 columns: one row per product per month, no missing values). Use the file as it is in the repository at the launch: if you cloned or downloaded it before, download it again. Quick check: in the current file the first data row (right after the header, as seen in a text editor) starts with `P001,2023-01,Mass,Centre,330.9` (Notebook 06 stops with a message if it loads an older copy).
- **Group size:** 3-4 students.
- **Deliverables:** one slide deck on [`data/pricing_presentation_template.pptx`](pricing_presentation_template.pptx), your code (notebook or script) and an elasticity file (CSV, deliverable 7).
- **Deck length:** max 10 slides, title slide included. The template has a title slide + 8 content slides, so you can add one. Backup slides after *Caveats* do not count and are not presented.
- **Submission:** one member submits the deck (.pptx or .pdf), the code (.ipynb or .py) and the elasticity file (.csv) by **Day 3, 14:30**, before presentations start. File names: `Group_X_pricing.pptx` (or `.pdf`), `Group_X_pricing.ipynb` (or `.py`) and `Group_X_elasticities.csv` (X = your group number). The submission channel is announced in class.

## Timeline

| When | What |
|---|---|
| Day 2, end of day (from 16:00) | Launch. Form your group, read this brief, agree your first move. |
| Day 3, 11:30-12:15 and 13:15-14:30 | Work session in class. The instructor answers questions about tools; modelling choices are yours to defend. |
| Day 3, 14:30 | Deck, code and elasticity file submitted. |
| Day 3, from 14:45 | Presentations: 7 minutes + 3 minutes of questions per group (shorter if there are more than seven groups; confirmed at the launch). Every member presents at least one slide. |

## Business context

You are a junior analyst at a mid-size retailer with 40 SKUs across three categories (Premium, Mass, Discount). Your CFO wants two answers:

1. **Which products are the most price-sensitive?** Rank them.
2. **For each product, what is the revenue impact of a ±10% price change?** Recommend raise, lower or hold, and say how confident you are.

Revenue is the CFO's question. If the cost data changes your recommendation, say so.

The CEO will read two slides over coffee: your *Executive Summary* and your *Recommendation* must stand on their own.

## Data dictionary

| Column | Notes |
|---|---|
| `product_id` | 40 SKUs (P001-P040) |
| `date` | monthly, 24 months (2023-01 → 2024-12), text `YYYY-MM` |
| `category` | Premium / Mass / Discount (one category per SKU) |
| `store_region` | North / Centre / South / Islands (each SKU is sold in one region) |
| `units_sold` | **target (demand)**: units sold in the month, recorded to one decimal |
| `price_eur` | **treatment (price)**: average selling price in the month, after any promotional discount |
| `cost_eur` | unit cost paid by the retailer |
| `competitor_price_eur` | observed competitor price for a comparable SKU |
| `supplier_cost_index` | supplier-cost index for the SKU's inputs (around 100; proxy for cost-side shocks) |
| `marketing_spend_eur` | monthly product-level marketing spend |
| `promo_flag` | 1 if the product was on promotion that month |
| `inventory_level` | end-of-month stock |
| `customer_satisfaction` | 1-5 average review |
| `website_traffic` | monthly page views |
| `social_media_score` | 0-100 brand sentiment |
| `temperature_avg_c` | monthly average temperature at the SKU's stores (°C; synthetic, one climate profile for all regions) |

## Deliverables

1. **EDA (max 3 plots in the deck)** — show the price-demand relationship at the right scale. The strongest plot goes on the template slide *Key EDA chart*.
2. **Modelling approach** — explain your choice. *Defend why you did or did not include each control variable.*
3. **Per-product elasticities** — table or chart of the top 10 most elastic and least elastic products.
4. **Scenario simulation** — for each product, simulate revenue at price × {0.9, 1.0, 1.1}. Recommend an action. The full table can go in backup.
5. **Business recommendation** — 3 bullets, framed for a CEO who has 60 seconds.
6. **Caveats** — what your model cannot answer.
7. **Elasticity file** — `Group_X_elasticities.csv` with one row per product (all 40) and four columns: `product_id, elasticity, ci_low, ci_high` (your estimate and its 95% interval). `elasticity` is the own-price elasticity of `units_sold` as you estimate it (normally negative, e.g. `-2.5`), with `ci_low` < `ci_high`. Save it as a plain comma-separated file with a decimal point (no `;` separator, no decimal comma) and exactly this header row: `product_id,elasticity,ci_low,ci_high`. Write `product_id` as in the dataset (P001-P040). It is part of the rigour assessment.

## Specific decisions you must defend

You will be graded on the *reasoning*, not just the numbers. Examples of decisions we will look for:

- Whether to **include `promo_flag`** as a control. There are two defensible positions:
  - Exclude: when promo is active, the "true price" perceived by the customer is the discounted price, which is already in `price_eur`. Including the flag double-counts.
  - Include: promo periods can carry confounders (display, ad spend) not captured elsewhere.
  - **Neither is universally right. Defend your choice.**
- Whether to use **`cost_eur`** and/or **`supplier_cost_index`** as controls. Cost-side variables can help identify the price effect, but check how strongly each one moves with price — across SKUs and within a SKU over time — and watch for multicollinearity.
- Whether to use **`inventory_level`** as a feature. Stop and think about *when* it is measured.
- How to handle **seasonality**.

## What we are NOT looking for

- A black-box model with high R² and no story.
- A regression with 14 predictors and no theory.
- A 30-slide deck with one chart per slide.

We are looking for a **clean, defensible, decision-grade analysis** you would not be ashamed to show a CFO.

Whatever model you use, you must be able to state, for each product, what a price change does to units — and how sure you are. A high-R² model that cannot do this does not answer the CFO's question, and it is graded accordingly.

## How your work is assessed

30 points across five dimensions:

| Dimension | Weight | The question we ask |
|---|---:|---|
| Analytical rigour | 25% | Are the elasticities reasonable and defensible? Does the EDA support the modelling choice? |
| Confounder handling | 25% | Is every variable choice — in or out — justified? |
| Business framing | 20% | Is the price lever isolated? Is the recommendation actionable: which product, which direction, what impact? |
| Communication | 20% | Can a CEO follow the story over coffee? Are the charts readable by a non-technical reader? |
| Methodological honesty | 10% | Do you say what your model does NOT answer? |

## Tools and questions

- Every member must be able to explain every number on your slides: after each presentation we ask questions, and anyone in the group may be asked.
- During the work session the instructor answers questions about tools and syntax. Questions about modelling choices get a question back: they are yours to defend.

## Resources

- **Notebook 06 starter:** [`notebooks/06_pricing_starter.ipynb`](../notebooks/06_pricing_starter.ipynb) ([open in Colab](https://colab.research.google.com/github/paolobalasso/DataScienceCourse/blob/main/notebooks/06_pricing_starter.ipynb)). A blank canvas whose sections follow deliverables 1-6, with a syntax toolbox at the end; the elasticity file (deliverable 7) is saved at the end of its section 3. Start here.
- **Lecture slides to revisit:** a PDF excerpt of these slides, without speaker notes, is shared at the launch. Titles as on the slides, with the page of the PDF excerpt:
  - Day 1, *Sales Forecasting*: "Time Series Decomposition" (p. 1), for seasonality.
  - Day 2 morning, *Model Selection*: "Complexity vs Explainability Axis" (p. 2).
  - Day 2 afternoon, *Pricing Deep Dive*: "Marshall's Law (1890) — Still Fundamental" (p. 3), "Log-Log OLS: The Workhorse" (p. 4), "Demand Curve Specifications — Linear, Log-Log, and Logistic" (p. 6), "Optimal Pricing via Calculus" (p. 7), "Margin Maximisation — Accounting for Cost of Supply" (p. 8), "Retail Pricing Challenge — Confounding in Store-Level Data" (p. 11), "Elasticity Interpretation in Context" (p. 12).
- **Notebooks from the lectures:** 02 (seasonal decomposition) and 05 (from a demand curve to a revenue curve).
