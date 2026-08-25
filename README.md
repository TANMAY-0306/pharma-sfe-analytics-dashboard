# Pharma Sales Force Effectiveness (SFE) Analytics Dashboard

🚧 **Status: In Progress** — data pipeline and SQL layer in development, Power BI dashboard coming soon.

## Problem Statement

Pharma companies rely heavily on field sales reps who visit doctors to promote drugs — it's one of the highest-cost sales channels in the industry. Leadership often struggles to answer:

- Are reps spending time on the **right** doctors (high-value / high-prescribing)?
- Are there **coverage gaps** — high-value doctors being under-visited?
- Does higher call frequency actually **correlate with prescription/sales growth**?

This project builds an end-to-end BI solution to answer these questions — simulating the kind of Sales Force Effectiveness (SFE) and commercial analytics work delivered for pharma clients in real consulting engagements.

## Approach

1. **Sales data (real):** Pharmaceutical sales transactions (2014–2019, 600K+ records across 57 drugs / 8 ATC categories), sourced from [Kaggle](https://www.kaggle.com/datasets/milanzdravkovic/pharma-sales-data).
2. **Rep activity data (synthetic):** Field rep call/visit data is proprietary and not publicly available, so a synthetic dataset (rep ID, doctor ID, doctor tier, call date, call outcome, territory) was generated in Python — clearly labeled as synthetic throughout this repo.
3. **Doctor segmentation:** Doctors bucketed into High/Medium/Low prescriber tiers based on sales volume.
4. **Analysis:** SQL (run in BigQuery) used to compute call frequency vs. target by tier, identify coverage gaps, and measure the relationship between visit frequency and sales trends.
5. **Visualization:** Power BI dashboard, connected directly to BigQuery, summarizing rep performance, territory coverage gaps, and tier-level ROI.

## Tech Stack & Data Flow

```
Python (synthetic data generation)
        │
        ▼
CSV files (real sales data + synthetic rep data)
        │
        ▼
Google BigQuery (cloud data warehouse — storage + SQL transformation)
        │
        ▼
Power BI (connected via native BigQuery connector — dashboard & visuals)
        │
        ▼
GitHub (scripts, SQL, README, dashboard file — version control & portfolio)
```

- **Cloud data warehouse:** Google BigQuery
- **Data processing & querying:** SQL (native BigQuery SQL editor)
- **Synthetic data generation:** Python (pandas, Faker)
- **Visualization:** Power BI Desktop (BigQuery connector)
- **Version control:** Git / GitHub

## Repository Structure

```
├── data/          # Raw and processed datasets (sales + synthetic rep activity CSVs)
├── scripts/       # Python scripts for synthetic data generation & cleaning
├── sql/           # SQL queries run in BigQuery for transformation and analysis
├── dashboard/     # Power BI file (.pbix) and exported screenshots
└── docs/          # Architecture diagram and technical notes
```

## Key Questions This Dashboard Answers

- Which doctor tiers are under-visited relative to target call frequency?
- Which territories show the largest coverage gaps?
- Is there a measurable link between call frequency and prescription growth by segment?

## Roadmap

- [x] Define problem statement and architecture
- [ ] Generate synthetic rep-activity dataset (Python)
- [ ] Load real + synthetic data into BigQuery
- [ ] Write SQL transformation and analysis queries
- [ ] Connect Power BI to BigQuery and build dashboard
- [ ] Document key business insights and findings

## Business Insight (to be updated)

*Findings and quantified impact (e.g., estimated revenue opportunity from closing coverage gaps) will be added here once analysis is complete.*
