# Pricing Optimisation — Group Exercise

**Dataset:** `data/retail_pricing_exercise.csv` (960 rows, 16 columns).
**Deadline:** see Blackboard.
**Group size:** 3-4 students.
**Deliverable:** one slide deck (max 10 slides) using `data/pricing_presentation_template.pptx` + your code (notebook or script).

## Business context

You are a junior analyst at a mid-size retailer with 40 SKUs across three categories (Premium, Mass, Discount). Your CFO wants two answers:

1. **Which products are the most price-sensitive?** Rank them.
2. **For each product, what is the revenue impact of a ±10% price change?** Recommend whether to raise or lower price.

The CEO will read 3 slides over coffee. Make them count.

## Data dictionary

| Column | Notes |
|---|---|
| `product_id` | 40 SKUs |
| `date` | monthly, 24 months (2023-01 → 2024-12) |
| `category` | Premium / Mass / Discount |
| `store_region` | North / Centre / South / Islands |
| `units_sold` | **target (demand)** |
| `price_eur` | **treatment (price)** |
| `cost_eur` | unit cost paid by the retailer |
| `competitor_price_eur` | observed competitor price for a comparable SKU |
| `supplier_cost_index` | macro supplier-cost index (proxy for cost-side shocks) |
| `marketing_spend_eur` | monthly product-level marketing spend |
| `promo_flag` | 1 if the product was on promotion that month |
| `inventory_level` | end-of-month stock |
| `customer_satisfaction` | 1-5 average review |
| `website_traffic` | monthly page views |
| `social_media_score` | 0-100 brand sentiment |
| `temperature_avg_c` | regional monthly average temperature |

## Deliverables

1. **EDA (max 3 plots in the deck)** — show the price-demand relationship at the right scale.
2. **Modelling approach** — explain your choice. *Defend why you did or did not include each control variable.*
3. **Per-product elasticities** — table or chart of the top 10 most elastic and least elastic products.
4. **Scenario simulation** — for each product, simulate revenue at price × {0.9, 1.0, 1.1}. Recommend an action.
5. **Business recommendation** — 3 bullets, framed for a CEO who has 60 seconds.
6. **Caveats** — what your model cannot answer.

## Specific decisions you must defend

You will be graded on the *reasoning*, not just the numbers. Examples of decisions we will look for:

- Whether to **include `promo_flag`** as a control. There are two defensible positions:
  - Exclude: when promo is active, the "true price" perceived by the customer is the discounted price, which is already in `price_eur`. Including the flag double-counts.
  - Include: promo periods can carry confounders (display, ad spend) not captured elsewhere.
  - **Neither is universally right. Defend your choice.**
- Whether to use **`cost_eur`** and/or **`supplier_cost_index`** as controls (they are highly correlated with `price` — useful for identification but watch for multicollinearity).
- Whether to use **`inventory_level`** as a feature. Stop and think about *when* it is measured.
- How to handle **seasonality**.

## What we are NOT looking for

- A black-box model with high R² and no story.
- A regression with 14 predictors and no theory.
- A 30-slide deck with one chart per slide.

We are looking for a **clean, defensible, decision-grade analysis** you would not be ashamed to show a CFO.

## Resources

- Notebook 06 starter: `notebooks/06_pricing_starter.ipynb` (blank canvas — start here).
- Slides Material.
