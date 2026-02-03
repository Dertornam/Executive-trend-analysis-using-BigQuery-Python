---
title: Reproducibility
layout: default
permalink: /reproducibility/
---

# Reproducibility — Executive Trend Analysis: Operational Workload Forecast (MA)

This page explains how to reproduce the analysis and outputs.

---

## Reproducible workflow
Step 1. Run the BigQuery aggregation query to produce Year × Gender annual totals.  
Step 2. Export the results to `data/raw/`.  
Step 3. Run the Python notebook to compute pooled yearly totals, regression trend, forecast, YoY volatility, segment test, and normality test.  
Step 4. Save figures into `reports/figures/` and copy the numeric outputs into `statistical-tables.md`.

---

## Core transformations
The key transformation is aggregation.  
The dataset is engineered so each row represents a full-year segment workload summary.

That is why the row count is small.  
It is small by design, but large in meaning.

---

## Output files referenced in the report
- `reports/figures/01_ng_ma_20yr_operational_load_growth_trend.png`  
- `reports/figures/02_linear_regression_operational_growth_forecast.png`  
- `reports/figures/03_variance_analysis_demand_by_segment.png`  
- `reports/figures/04_workload_distribution_normality.png`  
- `reports/figures/05_operational_volatility_yoy_pct_change.png`

---

## What makes this reproducible
Everything is deterministic once the data is fixed.  
The query defines the grain, and the notebook defines the metrics and visuals.

If someone reruns the same query and notebook, they should recreate the same figures and tables.  
That is the standard for executive analytics credibility.
