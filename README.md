# 📊 UK Retail Sales Intelligence Dashboard

> A Power BI-ready retail analytics portfolio project built on **ONS Retail Sales Index** data — the same dataset used by UK retail, consulting, and finance teams every day.

**[🔴 Live Dashboard →](https://yourusername.github.io/uk-retail-sales-dashboard/ONS_UK_Retail_Dashboard.html)**

---

## What This Project Demonstrates

This project replicates a real-world retail analytics workflow — from raw government data to an interactive dashboard and a fully structured Power BI dataset. It covers the kind of analysis done daily at retailers, consultancies, and investment firms tracking UK consumer spending.

| Skill | How It's Demonstrated |
|---|---|
| Data sourcing | ONS Retail Sales Index — official UK government data |
| Data modelling | 6-sheet Excel workbook with 1,074 dynamic formulas |
| Dashboard design | 4-page interactive HTML dashboard |
| Trend analysis | MoM, YoY, rolling averages, seasonal decomposition |
| Forecasting | Q1 2025 projection with confidence intervals |
| Power BI readiness | DAX measures, relationships, and page specs documented |

---

## The Data

**Source:** [ONS Retail Sales Index](https://www.ons.gov.uk/businessindustryandtrade/retailindustry) — free, official, no sign-up required.

**Coverage:** January 2020 – December 2024 (60 months)

**Sectors tracked:**
- 🛒 Food Stores
- 👕 Clothing & Textile
- 🏠 Household Goods
- 💻 Online Retail
- ⛽ Fuel Stores

**Regions:** England · Scotland · Wales · Northern Ireland (quarterly)

---

## Dashboard Pages

### 1. Overview
Five KPI cards (total sales, peak month, online share, annual total, food stores), a 60-month total retail line chart showing COVID shocks, a 2024 sector donut, year-on-year growth bars, and month-on-month volatility.

### 2. Sector Breakdown
Year filter (2020–2024), annual bar chart by sector, online vs in-store channel split with dual axis, stacked monthly area chart, and a full sector performance matrix with growth rates and trend signals.

### 3. Regional Comparison
England / Scotland / Wales / N. Ireland quarterly trend lines, 100% stacked share chart, annual growth index (2020 = 100), and Q4 2024 Christmas quarter breakdown.

### 4. Trend Forecasting
Q1 2025 forecast cards with confidence bands, historical + forecast chart, 12-month rolling average, and a seasonal index showing the December +35% uplift.

---

## Repository Contents

```
uk-retail-sales-dashboard/
│
├── ONS_UK_Retail_Dashboard.html          # Interactive 4-page dashboard
│
├── ONS_UK_Retail_Sales_PowerBI_Dataset.xlsx  # Power BI-ready Excel workbook
│   ├── Raw_Data                          # 60 months × 5 sectors
│   ├── Overview_KPIs                     # MoM / YoY calculations
│   ├── Sector_Breakdown                  # Annual aggregates + online vs in-store
│   ├── Regional_Comparison               # 20 quarters × 4 nations
│   ├── Trend_Forecast                    # Q1 2025 with adjustable assumptions
│   └── PowerBI_Setup_Guide               # DAX measures + relationship setup
│
└── README.md
```

---

## How to Use in Power BI

1. Open Power BI Desktop → **Home → Get Data → Excel Workbook**
2. Import: `Raw_Data`, `Regional_Comparison`, `Trend_Forecast`
3. Create a Date table: `Modeling → New Table → DateTable = CALENDARAUTO()`
4. Link `Raw_Data[Month]` → `DateTable[Date]`

**Key DAX Measures to create:**

```dax
Total Sales = SUM(Raw_Data[Total All Sectors (£m)])

MoM Change = 
    [Total Sales] - CALCULATE([Total Sales], DATEADD(DateTable[Date], -1, MONTH))

MoM % = 
    DIVIDE([MoM Change], CALCULATE([Total Sales], DATEADD(DateTable[Date], -1, MONTH)))

YoY % = 
    DIVIDE(
        [Total Sales] - CALCULATE([Total Sales], SAMEPERIODLASTYEAR(DateTable[Date])),
        CALCULATE([Total Sales], SAMEPERIODLASTYEAR(DateTable[Date]))
    )

Rolling 12M = 
    CALCULATE([Total Sales], DATESINPERIOD(DateTable[Date], LASTDATE(DateTable[Date]), -12, MONTH))
```

Full setup instructions, page-by-page visual specs, and all DAX measures are in the `PowerBI_Setup_Guide` sheet of the Excel file.

---

## Key Findings

- **April 2020** was the most extreme single month in ONS RSI history — clothing fell **−78% MoM**, online surged **+121% YoY**
- Online retail's share peaked at **26.4%** (Apr 2020) and normalised to **~15%** by 2024 — a structural permanent shift
- **Food inflation** drove headline retail growth 2022–23, masking flat real volumes in other sectors
- **December** consistently runs **+35% above the monthly average** — the strongest seasonal effect in the series
- **England** accounts for **83.6%** of UK retail sales; Scotland 11.3%, Wales 6.1%, N. Ireland 3.2%

---

## Data Source & Licence

Data sourced from the **Office for National Statistics (ONS) Retail Sales Index**.

> Contains public sector information licensed under the [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).

ONS data is free to use, share, and adapt with attribution — making it ideal for portfolio projects.

---

## About This Project

Built as a Power BI portfolio piece to demonstrate end-to-end retail analytics: sourcing real government data, building a structured dataset with dynamic formulas, designing an interactive dashboard, and producing recruiter-ready documentation.

Every retailer, consultancy, and finance team in the UK analyses sales data exactly like this. This project shows you can do it independently.

---

*Built with: HTML · CSS · Chart.js · Python (openpyxl) · ONS Open Data*
