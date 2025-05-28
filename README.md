# G-20 World Bank Analytics — Socio-Economic Insights

> **Purpose:** Turn raw World Bank API feeds into actionable, executive-ready Tableau dashboards that reveal how G-20 economies stack up on growth, trade, connectivity and human-development KPIs.

## Dashboard Preview

### Dashboard 1—Social & Economic Trends  
![dashboard 1](https://github.com/ndomah/G20-Bank-Data-Analytics-and-Dashboard/blob/main/Dashboard%201.png)

### Dashboard 2—Economic Dynamics  
![dashboard 2](https://github.com/ndomah/G20-Bank-Data-Analytics-and-Dashboard/blob/main/Dashboard%202.png)

> 🔗 **Interactive version:** [Tableau Public](https://public.tableau.com/app/profile/nilesh.domah4236/viz/WorldBankAnalytics_17156157559640/Dashboard2)


## Table of Contents
- [Project Background](#project-background)
- [Data Pipeline](#data-pipeline)
- [Executive Summary](#executive-summary)
- [Insights Deep Dive](#insights-deep-dive)
  - [Social & Labour Metrics](#social--labour-metrics)
  - [Macroeconomic Health](#macroeconomic-health)
  - [Trade & Globalisation](#trade--globalisation)
  - [Investment & Connectivity](#investment--connectivity)
  - [Dashboard Design Notes](#dashboard-design-notes)
- [Recommendations](#recommendations)
- [Assumptions & Caveats](#assumptions--caveats)
- [Next Steps](#next-steps)




## Project Background
Policy teams often grapple with siloed spreadsheets when benchmarking G-20 performance.  
This project delivers a **re-usable, code-driven workflow** that:

1. **Pulls live data** (2015 – 2020) from the World Bank API for 16 key indicators.  
2. **Cleans & models** the feed in Python, then ships a tidy dataset to Tableau.  
3. **Visualises** cross-country deltas so decision-makers can spot outliers in seconds.


## Data Pipeline
| Stage | Tooling | Key Tasks |
|-------|---------|-----------|
| **Extraction** | `wbdata`, `requests` | API calls for GDP, CPI, FDI, trade, health & education spend, etc. |
| **Preparation** | **Pandas / NumPy** | Datatype normalisation, missing-value imputation (forward-fill + median), ISO country mapping. |
| **Enrichment** | **SQL (SQLite)** | Generated `dim_date`, `dim_country`, calculated y-o-y deltas & growth rates. |
| **Visualisation** | **Tableau** | Two dashboards, 7 sheet types (line, bar, bubble, map, treemap, bullet, box-plot). |
| **Notebook** | [World Bank Analytics .ipynb](https://github.com/ndomah/G20-Bank-Data-Analytics-and-Dashboard/blob/main/World%20Bank%20Analytics.ipynb) | Reproducible EDA & export script. |


## Executive Summary
| KPI | Stand-out Insight |
|-----|------------------|
| **Inflation** | South Africa averages **6.6 %** (2016 peak) — 3 × higher than peer median. |
| **Unemployment** | South Africa maintains **22 – 25 %** unemployment vs. G-20 median < 7 %. |
| **Electricity Access** | All countries > 97 % except South Africa (~ 84 %), signalling infrastructure gap. |
| **Education Spend Efficacy** | UK & South Africa show weakest learning returns on spend. |
| **Trade Balance** | Canada & UK hover near equilibrium; US runs **$-2 T** import gap. |
| **FDI Volatility** | UK shows broadest FDI distribution (-0.6 % to 12 % of GDP). |


## Insights Deep Dive

### Social & Labour Metrics
* **Inflation vs. Employment:** Persistent double-digit unemployment in South Africa co-exists with the bloc’s highest CPI, amplifying cost-of-living stress.  
* **Electricity Equity:** Map layer flags sub-90 % household connectivity only in South Africa, guiding multilateral energy-financing priorities.

### Macroeconomic Health
* **GDP vs. Capital Formation:** Bubble plot reveals the **US** generating > \$21 T GDP with ~20 % capital-formation rate, while Canada punches above weight (balanced growth).  
* **Education ROI:** Treemap shading quantifies learning-outcome returns; high-spend/low-return nodes (UK, South Africa) merit efficiency audits.

### Trade & Globalisation
* **Exports-Imports Bullet:** Canada’s bars align to target line (~\$32 B), illustrating balanced trade; UK & SA exceed import thresholds indicating potential deficits.  
* **Mobile Subscriptions vs. GNI:** Positive correlation highlights digital adoption as GNI lever; U.S. & Australia lead, India & Indonesia lag.

### Investment & Connectivity
* **FDI Box-Plot:** UK’s wide whiskers denote policy-driven FDI swings; Australia & Canada enjoy stable 2 – 4 % inflows, attractive for long-term funds.

### Dashboard Design Notes
Four-quadrant layout keeps **trend** (top), **geospatial** (bottom-left), **composition** (treemaps) and **distribution** (box/bullet) visuals distinct.  
Colour-blind-safe palettes and direct-label annotations promote immediate comprehension for non-analyst stakeholders.


## Recommendations
1. **Targeted Price-Stability Programs** for South Africa: joint IMF-SARB roadmap to tame > 6 % inflation.  
2. **Energy-Access Financing**: World Bank & IFC to co-fund grid upgrades where electricity < 90 %.  
3. **Trade Policy Review**: US & UK to reassess tariff structures causing persistent import gaps.  
4. **Ed-Spend Efficiency Audits**: Deploy OECD-style benchmarking in UK & South Africa to tie budgets to outcomes.  
5. **FDI Risk-Mitigation Measures**: UK Treasury to stabilise capital inflows via bilateral investment treaties.


## Assumptions & Caveats
* Time window limited to **2015-2020**; pandemic-era anomalies partly captured, but 2021-2024 not included.  
* API snapshot taken May 2024 — subsequent WB data revisions not reflected.  
* Inflation & unemployment figures averaged across 12 monthly observations; may mask intra-year spikes.  
* Exchange-rate effects not adjusted when comparing GDP & trade metrics in USD.  
* Tableau dashboards optimised for 16 : 9 desktop; mobile layouts not configured.


## Next Steps
* Extend ETL to **auto-refresh quarterly** and push extracts to Tableau Server.  
* Incorporate **Purchasing Power Parity (PPP)** adjustments for truer cost comparisons.  
* Add **climate & sustainability metrics** (CO₂ per capita, renewables share) to enrich policy lens.  
* Build **predictive models** (e.g., ARIMA on inflation) to forecast 3-year outlooks.
