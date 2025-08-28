# Appleton Tower Electricity Usage — COVID-19 Impact

**University of Edinburgh — Appleton Tower**  
Analysis of how electricity consumption changed pre-, during, and post‑COVID‑19, using half‑hourly meter data and statistical tests.

## Highlights

- Significant drop in average daily electricity consumption **during** and **after** the pandemic compared with pre‑pandemic levels (paired _t_-tests, large effect sizes).
- Diurnal usage pattern (early/late troughs with a 9–5 peak) largely **returned post‑pandemic**, suggesting reduced occupancy—rather than schedule changes—drives the overall decline.
- Two core visuals:
  1. Average **daily** consumption by semester month across periods.
  2. Average **hourly** consumption for an “average day” across periods.

## Getting Started

### 1) Environment

- Python **3.10+** recommended
- Create and activate a virtual environment, then install requirements:
  ```bash
  python -m venv .venv
  source .venv/bin/activate  # Windows: .venv\Scripts\activate
  pip install -r requirements.txt
  ```
  Suggested `requirements.txt` (edit as needed):

```
pandas
numpy
scipy
matplotlib
seaborn
jupyter
```

_(If you used additional libraries—e.g., statsmodels, pyjanitor—add them here.)_

### 2) Data Access

The dataset was provided by the University of Edinburgh Estates Department under a **Copyright University of Edinburgh** license. It is **not redistributed** in this repo..

### 3) Reproduce the Analysis

- Open the notebook:
  ```bash
  jupyter notebook notebooks/FODS-CW2-Code.ipynb
  ```
- Run all cells to:
  - load + clean the data (filter to electricity, handle invalid values, convert dates, add month column)
  - segment into **Pre** (2018‑12‑11 → 2020‑03‑23), **During** (2020‑03‑24 → 2021‑05‑23), **Post** (2021‑09‑20 → 2024‑05‑27) semesters
  - compute monthly and hourly aggregates
  - run paired _t_-tests (pre vs during, pre vs post) and effect sizes (Cohen’s _d_)
  - export figures to `figures/bargraph.png` and `figures/HourlyEnergyUsageLineGraphs.png`


## Key Methods

- **Data cleaning**: drop invalid (≤0) readings, deduplicate, date parsing, remove pre‑2018‑12‑11 “N” source outliers, semester-only filtering (excludes Jun–Aug).
- **Statistics**: paired **t-tests** for period comparisons (α = 0.05); **Cohen’s d** for effect size; correlation between pre/post hourly profiles.
- **Visualization**: Matplotlib/Seaborn bar and line charts.

## Reproducibility Notes

- Randomness is not used, so runs should be deterministic given identical inputs.
- If you choose imputation for missing/invalid slots (rather than dropping), document the method (e.g., forward‑fill previous day same slot) and rerun tests.

## Ethics & Data License

- **Data** © University of Edinburgh (used with permission). Do not re-share.
- **Code** in this repo is released under **MIT License** (or your preferred OSI license).

## How to Cite

If you refer to this work, please cite the report (and optionally this repo). Example:

> Russo, A. _An Analysis of Changes in Electricity Consumption at the University of Edinburgh’s Appleton Tower Due to the COVID‑19 Pandemic_ (2025).

## Contact

Questions or collaboration ideas? Open an issue or reach out via GitHub.

---

_Last updated: 2025-08-28_
