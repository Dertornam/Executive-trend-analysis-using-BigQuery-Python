---
title: SQL & Syntax
layout: default
permalink: /sql-and-syntaxes/
---

# SQL & Syntax — Executive Trend Analysis: Operational Workload Forecast (MA)

This page documents the query pattern used to produce the executive dataset.

## Executive aggregation logic (Year × Gender)
The core design is a `GROUP BY` that compresses high-volume workload into annual totals by segment.

Paste your exact BigQuery SQL here verbatim.  
Keep it unchanged so the portfolio is reproducible and auditable.

## Python transformation notes
In Python, I compute:
- Pooled yearly totals by summing across gender per year.
- YoY percent change on pooled totals.
- Regression on pooled totals for trend and forecast.
- Segment t-test on Year × Gender totals.
- Shapiro-Wilk normality test on pooled yearly totals.
