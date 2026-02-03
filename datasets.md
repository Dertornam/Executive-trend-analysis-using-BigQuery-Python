---
title: Datasets
layout: default
permalink: /datasets/
---

# Datasets — Executive Trend Analysis: Operational Workload Forecast (MA)

This project is built as an executive trend dataset, not a transactional dump.  
The core design decision is aggregation.

---

## Dataset overview
The analytic file contains 42 rows at the Year × Gender level.  
Each row represents total annual workload for a segment.

This is “enough” for executive trend analysis because the underlying operational stream is summarized.  
The point is not row count. The point is long-horizon interpretability.

---

## Repository structure used in this project
**Raw data:** `data/raw/`  
**Figures and reporting assets:** `reports/figures/`

---

## Notes for operational reuse
This structure mirrors how Work Support teams report workload.  
Executives care about annual totals, trend direction, volatility, and segment baselines.

If leadership needs staffing rosters, the next layer is monthly or weekly rollups.  
The executive story still starts at annual trend.
