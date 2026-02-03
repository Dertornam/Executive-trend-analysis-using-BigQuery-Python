---
title: Executive Summary
layout: default
permalink: /executive-summary/
---

# Executive Summary — Executive Trend Analysis: Operational Workload Forecast (MA)

I built this project to answer a practical leadership question: when operational demand changes over time, am I looking at a planning-grade trend signal that supports proactive resourcing, or am I looking at volatility that forces Work Support teams into reactionary scheduling?

I used BigQuery to aggregate high-volume operational activity into an executive dataset at the Year × Gender level. That is why the analytic file contains 42 rows. It is not 42 raw transactions. It is a long-horizon operational summary where each row represents total annual workload for a segment. This is the right grain for leadership because executives plan on trend, not on millions of event records.

## What I found and why it matters

My results tell a coherent story. The baseline trend is highly predictable at the annual level, segment differences are statistically meaningful, and the distribution behaves like a planning-grade operational series that supports standard forecasting summaries.

First, the trend model fit is strong. My regression result (R² = 0.9060) indicates that time explains about 90.6% of the variance in aggregated annual workload. I interpret this as a “forecastable baseline” series. The slope is negative (-741.97 units/year, p < 0.001), so the baseline direction in this window is declining rather than compounding upward.

Second, I do see evidence that demand differs by segment. My two-sample t-test returns a p-value of 0.000002, which is far below 0.05, so I reject the null hypothesis of equal means. In practical terms, the male segment averages 30,945 units/year while the female segment averages 26,696 units/year, and the separation is large enough to matter in planning conversations if the segment definition reflects real operational routing or assignment patterns.

Third, the annual totals behave like a planning-grade distribution. The normality test p-value is 0.0507, which sits just above the 0.05 threshold. I interpret this as “approximately normal” in this executive aggregation context, which supports mean-based reporting while still pairing it with volatility views for decision realism.

The long-run pooled direction also shows up in a simple growth metric. The compound annual growth rate across pooled annual totals is -1.11%. The forecast translates the model into a decision-ready number: the next-year estimated demand is 49,479.

## What I would tell an executive team in one minute

If I am making the “so what” plain, I would say this: the series is forecastable (R² = 0.9060), it trends downward in this window (slope = -741.97 units/year), segment baselines differ meaningfully (p ≈ 0.000002), and the forecast output provides a defensible baseline number (49,479) that leadership can plan around.

## What I recommend based on the evidence

I recommend forecast-driven staffing and scheduling. The model fit supports using a multi-year planning view with the forecast baseline as the anchor for resourcing assumptions and budget planning.

I recommend segment-aware reporting and validation. Because the segment means differ significantly, I would plan with segment baselines alongside the pooled total, then validate the operational mechanism behind the difference so leadership can decide whether the gap reflects routing, assignment, territory, or process design.

I recommend volatility-aware buffers. The YoY percent-change series has a clear swing profile (average YoY -1.14%, with a worst year of -4.14% in 2020 and a best year of 4.95% in 2021). Planning should include surge playbooks so service levels remain stable when demand diverges from expectation.

## Notes I keep in mind when I interpret the model

A regression forecast is not a guarantee. It is a baseline expectation. That is why I pair trend modeling with volatility. Leaders need “expected direction” and “risk envelope,” not only a single line.

Annual aggregation is a deliberate executive design. It compresses within-year variation to create interpretability. If the question shifts from strategy to staffing rosters, the next drill-down should be monthly or weekly rollups rather than changing the executive story layer.

## Bottom line

I built this project to separate “reactionary scheduling” from “proactive planning.” My results support proactive planning with a defensible baseline forecast, while also showing that segment baselines and volatility are the operational realities that leadership should manage explicitly.
