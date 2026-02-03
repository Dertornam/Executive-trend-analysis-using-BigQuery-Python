---
title: Data Dictionary
layout: default
permalink: /data-dictionary/
---

# Data Dictionary — Executive Trend Analysis: Operational Workload Forecast (MA)

This dictionary documents the main fields used in the analysis.

---

## Core fields
**year**  
Definition: Calendar year of the aggregated workload total.  
Role: Time index for trend modeling and YoY volatility.

**gender**  
Definition: Segment label used in the aggregation.  
Role: Used for segment variance comparisons.

**simulated_service_demand**  
Definition: Aggregated annual workload total for the segment in that year.  
Role: Primary operational demand outcome.

---

## Derived fields (pooled yearly totals)
**yearly_total**  
Definition: Total service demand pooled across segments per year (sum over gender).  
Role: Executive “total load” view, trend regression, forecast, CAGR.

**pct_change**  
Definition: Year-over-year percent change in pooled yearly totals.  
Role: Volatility and shock identification.
