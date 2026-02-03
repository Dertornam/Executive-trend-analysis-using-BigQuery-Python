---
title: Statistical Tables
layout: default
permalink: /statistical-tables/
---

# Statistical Tables — Executive Trend Analysis: Operational Workload Forecast (MA)

This page consolidates the numeric outputs used in the report.  
All values come from the aggregated Year × Gender dataset (42 rows) and the pooled yearly totals used for trend, YoY volatility, and CAGR.

---

## A. Dataset shape (executive aggregation)

| Item | Value |
|------|------:|
| Grain | Year × Gender |
| Rows | 42 |
| Years | 21 (2001–2021) |
| Segment count | 2 |

---

## B. Descriptive statistics (Year × Gender demand)

| Gender Segment | Count | Mean Demand | Std. Deviation | Min | Max |
|---------------|------:|------------:|---------------:|----:|----:|
| Female (F) | 21.0 | 26,696.2 | 2,235.8 | 23,793 | 31,456 |
| Male (M) | 21.0 | 30,944.7 | 2,617.7 | 26,769 | 35,576 |

Interpretation note.  
Means and ranges differ materially, which is consistent with the segment variance visible in the boxplot.

---

## C. Inferential test (Segment comparison)

| Test Metric | Value | Interpretation |
|------------|------:|---------------|
| T-Statistic | -5.6554 | Direction indicates which segment is higher in this coding. |
| P-Value | 0.000002 | Significant. Segment means differ. |

---

## D. Predictive model (Trend regression on pooled yearly totals)

| Metric | Value | Business Impact |
|--------|------:|-----------------|
| R-Squared | 0.9060 | 90.6% of variance explained by time at the annual level. |
| Slope (units/year) | -741.97 | Baseline directional change per year in the pooled totals. |
| P-Value (time) | 3.310e-11 | Extremely significant trend signal in this view. |
| Next-Year Forecast (2022) | 49,479 | Decision-ready baseline for planning. |

---

## E. Distribution check (Normality on pooled yearly totals)

| Metric | Value | Interpretation |
|--------|------:|----------------|
| Shapiro-Wilk P-Value | 0.0507 | Approximately normal at the 0.05 threshold for planning summaries. |

---

## F. Operational volatility (YoY % change on pooled yearly totals)

| Metric | Value |
|--------|------:|
| Average YoY % change | -1.14 |
| Std. dev of YoY % change | 1.98 |
| Worst YoY year (min) | -4.14% (2020) |
| Best YoY year (max) | 4.95% (2021) |

---

## G. Long-run growth metric (CAGR on pooled yearly totals)

| Metric | Value | Interpretation |
|--------|------:|----------------|
| Start year total (2001) | 67,032 | Pooled annual total at the beginning of the window. |
| End year total (2021) | 53,066 | Pooled annual total at the end of the window. |
| CAGR | -1.11% | Long-run average growth rate across the window. |
