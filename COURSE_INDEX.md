# Data Science Course — Course Index (Student-facing)

**Università Cattolica del Sacro Cuore, Milano**
**Instructor:** Paolo Balasso
**Format:** 3-day intensive master class
**Repository:** [https://github.com/paolobalasso/DataScienceCourse](https://github.com/paolobalasso/DataScienceCourse)

This index is the entry point for students. It tells you what is in the repository, in what order to use it, and what is expected of you.

---

## 1. What is in this repository

| Folder | What's there | When to use it |
|---|---|---|
| `notebooks/` | 6 Jupyter notebooks (01-06) | Run them along the lectures (Colab badges in README) |
| `data/` | Synthetic datasets + briefs | Load them from the notebooks or read the briefs |
| `README.md` | Repository entry point | First read, contains Colab badges |
| `requirements.txt` | Python dependencies | If you run locally, `pip install -r requirements.txt` |
| `LICENSE` | MIT | Use the material freely; cite if you reuse it |

---

## 2. The 6 notebooks — what each one teaches

| # | Notebook | Topic | When in the course | Time to run |
|---|---|---|---|---|
| **01** | `01_churn_cost_threshold.ipynb` | Cost-based threshold, ROC vs PR, calibration, lift, propensity binning | Day 1 afternoon | ~30 s on Colab |
| **02** | `02_demand_eda_single_product.ipynb` | STL decomposition, ADF, ACF/PACF, baselines (Naive/SNaive/ETS), MAPE/WAPE/MASE | Day 2 morning | ~45 s |
| **03** | `03_demand_eda_multi_product.ipynb` | Simpson's paradox, hierarchical demand, bottom-up vs top-down, cannibalisation | Day 2 morning | ~30 s |
| **04** | `04_portfolio_optimization.ipynb` | Markowitz, Investment Clock, Permanent / All-Weather, regime-aware tilt | Day 2 afternoon | ~1 min (fetches FRED data) |
| **05** | `05_conjoint_demand_revenue.ipynb` | Choice-based conjoint, MNL, WTP, market simulator, revenue optimisation, bootstrap | Day 3 morning | ~30 s |
| **06** | `06_pricing_starter.ipynb` | **Group exercise canvas** — blank, you fill it in | End of Day 2 → Day 3 morning | Your work |

How to open any notebook: open `README.md`, click the **Colab badge** in the table. Colab does the rest.

---

## 3. The two hands-on exercises

### Exercise A — Churn fallback (individual, optional)

**Purpose:** if you want to develop the churn analysis yourself before reading the instructor's notebook 01.

**Materials:**
- `data/churn_starter.csv` (5,000 rows, synthetic Telco-style)
- `data/churn_brief.md` — what to do, deliverables, hints

**Time budget:** 2-3 hours.
**Output:** your own analysis + comparison to notebook 01.
**Grading:** not graded; for personal learning.

---

### Exercise B — Pricing Optimisation (group, graded)

**Purpose:** the main hands-on assignment of the course. You will be evaluated.

**Materials:**
- `data/retail_pricing_exercise.csv` — 40 SKUs × 24 months, 16 columns
- `data/pricing_brief.md` — business context, data dictionary, deliverables, decisions to defend
- `data/pricing_presentation_template.pptx` — 8-slide template (use it for the final deck)
- `notebooks/06_pricing_starter.ipynb` — blank canvas starter notebook

**Group size:** 3-4 students. Self-organised.
**Deadline:** end of Day 3 morning.
**Presentations:** Day 3 afternoon, ~15:00.

**Deliverable:**
- Slide deck (8-10 slides) on the provided template
- Code (notebook or .py)

**Evaluation:** the instructor evaluates on 5 dimensions (analytical rigour, confounder handling, business framing, communication, methodological honesty). The grading rubric is **not** distributed before submission — your job is to do the right analysis, not to game the rubric.

**Hints on the pricing brief:**
- Read `data/pricing_brief.md` end to end before starting.
- Pay attention to the section "Specific decisions you must defend" — these are the points the rubric scores hardest on.
- Don't be tempted by a black-box model. The CFO wants a defensible elasticity, not a high R².
- The starter notebook (06) is intentionally minimal. You fill it in.

---

## 4. Recommended path through the course

**Before Day 1:** clone the repo or just bookmark it. Make sure you have a Google account (for Colab).

**Day 1 evening:** open notebook 01, run it, read the cells.

**Day 2 evening:** open notebooks 02-04, run them, read the cells. **Start thinking about Exercise B** — read the brief, do NOT start coding yet.

**Day 3 morning before 09:00:** form your group. Spend the morning on Exercise B.

**Day 3 afternoon:** present.

---

## 5. Tooling — what you need

- **Google Colab** (free tier is enough) — the recommended way to run notebooks
- Or a local Python ≥ 3.10 with `pandas`, `numpy`, `scikit-learn`, `statsmodels`, `matplotlib`, `seaborn`, `yfinance` (for notebook 04). Run `pip install -r requirements.txt`.
- A laptop. Tablets are not recommended for the hands-on.
- A GitHub account is optional but useful (you can fork the repo and keep your own copy).

---

## 6. Reference material (provided after course end)

After the course ends, you will receive (PDF or DOCX):

- **DataScience_KB_Book** — ~200-page reference book covering all 17 chapters of the course content, with worked examples, code walkthroughs, Q&A bank, and full bibliography.
- **Model solution presentation** for Exercise B — a reference deck showing how a top-grade submission looks.

These materials are for self-study. They are NOT required for the in-class work.

---

## 7. Questions during the course

- During lectures: raise hand or use Slido (link will be shared in class).
- During exercises: ask the instructor or post in the group chat.
- After the course: email `pianist.balasso@gmail.com`.

---

## 8. Common questions before the course

| Question | Answer |
|---|---|
| Do I need to know Python? | Basic familiarity helps. The notebooks are commented and the lectures walk through them. |
| Will there be a written exam? | No. The group exercise is the main evaluation. |
| Can I use ChatGPT / Copilot? | Yes, but understand what you submit. We will ask questions during presentations. |
| Will the slides be shared? | Yes, at the end of the course (PDF). |
| Is attendance mandatory? | Yes. Day 3 group presentations require all members present. |

---

*Last updated when v7 of the KB Book was produced. If you find a link broken or a file missing, email the instructor.*
