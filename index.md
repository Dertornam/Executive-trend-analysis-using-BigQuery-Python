---
title: ## Executive Trend Analysis: Operational Workload Forecast (MA)
layout: default
---

**Tools:** Google BigQuery (SQL), Python (Pandas, NumPy, SciPy, Statsmodels, Matplotlib)

<style>
.port-btn{
  display:inline-block;
  padding:.6rem 1rem;
  margin:.25rem .4rem 0 0;
  border-radius:8px;
  background:#0366d6;
  color:#fff !important;
  text-decoration:none !important;
  border:1px solid rgba(0,0,0,.08);
  box-shadow:0 1px 2px rgba(0,0,0,.05);
  font-weight:600;
}
.port-btn:hover{ filter:brightness(0.95); }
</style>

<div style="margin: 1rem 0;">
  <a class="port-btn" href="{{ '/executive-summary' | relative_url }}">Executive Summary</a>
  <a class="port-btn" href="{{ '/statistical-tables' | relative_url }}">Statistical Tables</a>
  <a class="port-btn" href="{{ '/datasets' | relative_url }}">Datasets</a>
  <a class="port-btn" href="{{ '/sql-and-syntaxes' | relative_url }}">SQL & Syntax</a>
  <a class="port-btn" href="{{ '/data-dictionary' | relative_url }}">Data Dictionary</a>
  <a class="port-btn" href="{{ '/reproducibility' | relative_url }}">Reproducibility</a>
</div>

<style>
.page-content img{
  max-width: 100%;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 1px 2px rgba(0,0,0,.06);
  margin: .5rem 0 1rem 0;
}
</style>

---

## Introduction & Project Objective
The goal of this project was to determine whether long-horizon operational demand can be summarized into a planning-grade trend signal that leadership can act on. I aimed to answer the “So What?” for Work Support and Operations: Is service demand predictable enough to support proactive resourcing, how volatile is it year-to-year, and do segments show meaningful differences that should change how teams plan capacity?

## Methodology
**Data Acquisition:** Data was extracted in BigQuery and engineered into an executive trend dataset at the Year × Gender level. The final analytic file contains 42 rows because it spans 21 years and two segments, with one row per year–segment.  
**Data Engineering:** I used a GROUP BY aggregation to convert high-volume operational records into annual totals. Each row represents a full-year workload summary for a segment, which is the appropriate grain for executive trend reporting.  
**Statistical Framework:**  
**Linear Regression:** To quantify the direction and strength of the long-run trend and generate a forecast.  
**T-Test:** To test whether demand differs by segment.  
**Normality Test:** To evaluate whether annual totals behave like a planning-grade distribution.  
**YoY % Change:** To measure volatility and identify shock years that planning should treat as exceptions.

## Key Findings & Interpretation
### A. Predictable Long-Run Direction (Regression)
**Results:** R-squared = 0.9060, Slope = -741.97 units/year (p < 0.001).  
**Interpretation:** Time explains about 90.6% of the variance in aggregated annual workload, which indicates strong predictability at the annual planning level. The slope is negative, so the baseline trend is declining in this window.  
**Conclusion:** This is a “forecastable baseline” series rather than a noisy series. The planning implication is that leadership can anchor resourcing on a defensible baseline while treating volatility as the operational risk layer.

### Visual: Total operational load and trend
![National Grid MA: 20-Year Operational Load & Trend]({{ '/reports/figures/01_ng_ma_20yr_operational_load_growth_trend.png' | relative_url }})

### B. Segment Differences (T-Test)
**Results:** t-statistic = -5.6554, p-value = 0.000002.  
**Interpretation:** Because the p-value is far below 0.05, we reject the null hypothesis of equal means. In this dataset, the segment means are not practically identical.  
**Conclusion:** Segment differences are statistically meaningful and should not be ignored in reporting. If the segment definition reflects real routing, assignment, or territory mechanics, capacity planning should validate the operational driver behind the gap.

### Visual: Demand by segment
![Variance Analysis: Demand by Segment]({{ '/reports/figures/03_variance_analysis_demand_by_segment.png' | relative_url }})

### C. Planning-Grade Distribution (Normality)
**Results:** Shapiro-Wilk p-value = 0.0507.  
**Interpretation:** This sits just above the 0.05 threshold, which supports treating the annual totals as approximately normal for executive summaries and mean-based planning language.  
**Conclusion:** The distribution behaves like a planning-grade series, but leaders should still pair averages with volatility metrics because a “normal-ish” distribution can still contain shock years.

### Visual: Workload distribution
![Workload Distribution (Normality)]({{ '/reports/figures/04_workload_distribution_normality.png' | relative_url }})

## Visual Highlights
**Trend Compression (Executive View):** Annual totals provide a clean long-horizon signal that can be forecasted.  
**Volatility Envelope:** The YoY chart shows the risk envelope around the baseline, including swing years that would strain staffing and service levels if not planned for.

### Visual: Operational volatility (YoY % change)
![Operational Volatility: YoY % Change]({{ '/reports/figures/05_operational_volatility_yoy_pct_change.png' | relative_url }})

## Final Recommendations (The “So What?”)
**Forecast-Driven Staffing:** With a strong annual fit (R² = 0.9060), leadership can move away from reactionary scheduling and adopt a multi-year staffing baseline anchored on forecasted totals.  
**Segment-Aware Reporting:** Because segment means differ significantly (p ≈ 0.000002), I would report segment baselines alongside the pooled total to avoid planning from an average that hides structural differences.  
**Volatility Buffers:** Because YoY swings include both negative and positive shocks, planning should include surge playbooks and capacity buffers so service levels remain stable when demand diverges from the baseline.

## Dataset Profile & Data Quality Notes
The analytic file contains 42 observations at the Year × Gender level. This is not “small data” in the operational sense. It is an engineered executive summary of a much larger workload stream, where each row is an aggregated annual total.

Annual aggregation intentionally compresses within-year variation. That is appropriate for executive trend narratives. If leadership needs staffing rosters, the next drill-down should be monthly or weekly rollups, but the executive story begins correctly at annual totals.

## Additional Quantification of the Visual Story
The long-run pooled series supports a decline narrative in this window. The compound annual growth rate across pooled annual totals is -1.11%, which aligns with the downward direction in the trend view.

The forecast translates the model into a decision-ready number. The next-year estimated demand is 49,479, which can be used as the baseline for planning assumptions and budget conversations.

## Model Diagnostics & Robustness Checks
A straight-line regression is intentionally simple because the executive question is directional and planning-oriented. The high R² indicates the baseline is stable at the annual level, but the YoY volatility plot shows why planning needs buffers and exception-year reasoning.

## Practical Interpretation of the Forecast
A forecast is a baseline expectation, not a guarantee. Operational reality includes shocks that can move a year away from expectation even in a highly predictable series. That is why this report pairs trend, volatility, and segment differences to produce a decision-ready planning narrative.

## Contact & Links

<div class="contact-links">
   <a class="port-btn"
     href="https://www.linkedin.com/in/derrick-dzormeku-mba-75288644"
     target="_blank" rel="noopener">
    LinkedIn
  </a>

   <a class="port-btn"
     href="https://mail.google.com/mail/?view=cm&fs=1&to=d.double76@icloud.com&su=Portfolio%20inquiry%20%E2%80%93%20Derrick%20Dzormeku&body=Hi%20Derrick,%0D%0A%0D%0AI%27m%20reaching%20out%20about%20your%20analytics%20portfolio.%20Could%20we%20schedule%20a%20brief%20call%3F"
     target="_blank" rel="noopener">
    Email
  </a>

  <a class="port-btn"
     href="https://dertornam.github.io/higher-ed-analytics-portfolio/"
     target="_blank" rel="noopener">
    Other Portfolios
  </a>
  <a class="port-btn" href="{{ '/resume.pdf' | relative_url }}">View Resume</a>
</div>

<style>
.contact-links {
  margin-top: 0.75rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.port-btn {
  display: inline-block;
  background: #0066cc;
  color: #ffffff !important;
  padding: 0.75rem 1.75rem;
  border-radius: 12px;
  font-weight: 700;
  text-decoration: none;
  font-size: 1rem;
  text-align: center;
}

.port-btn:hover {
  background: #0053a6;
}
</style>

This project is designed as a portfolio.
