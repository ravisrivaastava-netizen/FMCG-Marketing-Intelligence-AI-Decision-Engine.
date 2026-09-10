# FMCG Marketing Intelligence & AI Decision Engine

> A portfolio-grade, decision-oriented analytics project for FMCG marketers.

## 1. Purpose

The **FMCG Marketing Intelligence & AI Decision Engine** is a synthetic-data project designed to demonstrate how a modern FMCG marketing leader can combine commercial analytics, customer analytics, marketing effectiveness measurement, forecasting, and AI-assisted decision support.

The goal is not to build a collection of disconnected notebooks.

The goal is to answer executive questions such as:

- **Why did sales change?**
- **Which categories, SKUs, channels and markets are driving the movement?**
- **Which customers or consumer segments deserve attention?**
- **Where should the next marketing rupee be invested?**
- **What happens if media spend, price, promotion or distribution changes?**
- **What should the marketing team do next?**

All company, consumer, sales, media and financial data in this project are **synthetic** and created for demonstration purposes.

---

## 2. Business Questions

### Growth diagnosis
- What is driving revenue and volume growth?
- Which categories and SKUs are growing or declining?
- Where are we gaining or losing distribution?
- Which channels are creating or destroying value?

### Consumer & customer
- Who are the highest-value customers?
- Which segments are growing?
- Which customers show signs of declining engagement?
- What products and categories are purchased together?

### Marketing effectiveness
- Which media channels contribute to incremental sales?
- What are ROI and marginal ROI by channel?
- How do adstock and saturation affect media response?
- How should the next marketing budget be allocated?

### Commercial planning
- What is likely to happen to demand next month/quarter?
- Which SKUs require intervention?
- What-if price, promotion or distribution scenarios can improve outcomes?

### Executive decision support
- What are the three biggest business issues?
- What evidence supports each issue?
- What action should the marketing leader take?
- What KPI should be monitored after the decision?

---

## 3. Decision Architecture

```text
                 SYNTHETIC FMCG DATA
                         |
       +-----------------+-----------------+
       |                 |                 |
     SALES             MEDIA           CUSTOMER
       |                 |                 |
       +-----------------+-----------------+
                         |
                  DATA FOUNDATION
                         |
       +-----------------+-----------------+
       |                 |                 |
  PERFORMANCE       SEGMENTATION       FORECASTING
   ANALYTICS             |                 |
       |                 CLV               |
       |                 |                 |
       +-----------------+-----------------+
                         |
                MARKETING EFFECTIVENESS
                         |
                  MMM / ROI / mROI
                         |
                  SCENARIO ENGINE
                         |
                AI DECISION LAYER
                         |
       +-----------------+-----------------+
       |                 |                 |
     WHY?             WHAT IF?         WHAT NEXT?
```

---

## 4. Project Modules

### Module 01 — Data Foundation
Build a clean, documented analytical model covering:

- markets
- channels
- categories
- brands
- SKUs
- customers
- transactions
- distribution
- pricing
- promotions
- media
- macro/seasonal factors

### Module 02 — Commercial Performance
Core KPIs:

- Revenue
- Units
- ASP
- Gross margin
- Volume growth
- Value growth
- Distribution
- Weighted distribution
- Price index
- Promotion intensity
- SKU productivity

### Module 03 — Consumer Segmentation
Build actionable segments using:

- RFM
- purchase frequency
- monetary value
- category breadth
- basket behaviour
- recency
- channel behaviour

The objective is not merely to create clusters. Each segment must have:

**Size → Value → Behaviour → Opportunity → Recommended action**

### Module 04 — Customer Lifetime Value
Estimate:

- historical customer value
- expected future value
- retention behaviour
- purchase frequency
- average order value

Use CLV to prioritize commercial actions.

### Module 05 — Basket & Cross-Sell Analytics
Identify:

- frequently co-purchased products
- category affinities
- basket-building opportunities
- cross-sell opportunities

### Module 06 — Demand Forecasting
Forecast:

- category demand
- SKU demand
- channel demand

Account for:

- seasonality
- promotions
- price
- distribution
- trend

### Module 07 — Marketing Mix Modeling
Evaluate marketing investment across:

- TV
- Digital
- Search
- Social
- Retail media
- OOH
- Influencers

Key outputs:

- incremental sales
- contribution
- ROI
- marginal ROI
- response curves
- saturation
- recommended budget allocation

This module is conceptually informed by open-source MMM approaches such as Meta's Robyn and Google's Meridian. Robyn supports adstock, saturation, model optimization and budget allocation; Meridian provides Bayesian MMM capabilities, ROI/mROI analysis and scenario planning.

### Module 08 — Scenario Engine

Example:

> Increase digital investment by 20%, reduce TV by 10%, increase distribution by 3%.

Estimate:

- expected sales impact
- incremental volume
- marketing ROI
- margin impact
- risk/uncertainty

### Module 09 — AI Marketing Copilot

Convert analytical outputs into an executive decision brief.

Example:

```text
BUSINESS ISSUE
Category revenue declined 4.2%.

KEY DRIVERS
1. MT volume decline: -6.1%
2. Distribution decline: -3.4%
3. Premium SKU mix weakened.

RECOMMENDED ACTION
Prioritize distribution recovery in the top 3 markets
and shift incremental activation toward high-velocity SKUs.

EXPECTED IMPACT
Potential recovery opportunity:
+2–3% category revenue, subject to execution.

WATCH KPI
Weighted distribution and weekly velocity.
```

The AI layer must **not invent facts**. Every recommendation should be traceable to analytical outputs.

---

## 5. Repository Structure

```text
fmcg-marketing-intelligence/
│
├── README.md
├── LICENSE
├── requirements.txt
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── dictionary/
│
├── notebooks/
│   ├── 01_data_quality.ipynb
│   ├── 02_commercial_performance.ipynb
│   ├── 03_customer_segmentation.ipynb
│   ├── 04_customer_lifetime_value.ipynb
│   ├── 05_basket_analysis.ipynb
│   ├── 06_demand_forecasting.ipynb
│   ├── 07_marketing_mix_model.ipynb
│   └── 08_scenario_planning.ipynb
│
├── src/
│   ├── data/
│   ├── analytics/
│   ├── segmentation/
│   ├── forecasting/
│   ├── mmm/
│   ├── scenarios/
│   └── decision_engine/
│
├── dashboards/
│   ├── executive/
│   ├── category/
│   └── consumer/
│
├── outputs/
│   ├── charts/
│   ├── tables/
│   └── executive_briefs/
│
├── tests/
│
└── docs/
    ├── data_dictionary.md
    ├── methodology.md
    └── decisions.md
```

---

## 6. Core Data Model

The project should use a star-schema-inspired model.

### Dimensions

- `dim_date`
- `dim_market`
- `dim_channel`
- `dim_category`
- `dim_brand`
- `dim_sku`
- `dim_customer`

### Facts

- `fact_sales`
- `fact_media`
- `fact_distribution`
- `fact_promotion`
- `fact_inventory`

### Example sales grain

One row represents:

> Customer × Date × SKU × Channel × Market

Important fields include:

```text
date
customer_id
market_id
channel_id
category_id
brand_id
sku_id
units
gross_sales
discount
net_sales
cogs
gross_margin
selling_price
promotion_flag
distribution
```

---

## 7. Synthetic Dataset Principles

The dataset should deliberately contain realistic commercial patterns:

### Seasonality
Demand varies by:

- month
- weekday
- festivals
- gifting periods

### Category differences
Different categories should have different:

- growth rates
- margins
- penetration
- price elasticity
- media responsiveness

### Channel differences

GT, MT, E-commerce, Q-commerce and HoReCa should behave differently.

### Market differences

Markets should vary in:

- size
- growth
- income
- channel mix
- category penetration

### Marketing response

Media should exhibit:

- carryover/adstock
- diminishing returns
- channel-specific effectiveness

### Commercial friction

The dataset should contain realistic imperfections:

- missing values
- outliers
- inconsistent distribution
- promotional spikes
- declining SKUs
- regional differences

This makes the analytical workflow more realistic.

---

## 8. KPI Framework

### Growth

`Value Growth %`

`Volume Growth %`

`Market Share %`

`Distribution Growth %`

### Consumer

`Active Customers`

`Repeat Rate`

`Purchase Frequency`

`Average Basket Value`

`Customer Lifetime Value`

### Marketing

`Incremental Sales`

`ROI`

`Marginal ROI`

`Cost per Incremental Customer`

### Commercial

`Gross Margin %`

`Net Revenue`

`Contribution`

`Price Index`

`SKU Productivity`

---

## 9. Technology Stack

Primary:

- Python
- Pandas
- NumPy
- Scikit-learn
- Statsmodels
- XGBoost / LightGBM where appropriate
- Matplotlib
- Plotly
- SQL

Analytics:

- RFM
- clustering
- regression
- forecasting
- causal/uplift methods where appropriate
- Marketing Mix Modeling

AI:

- LLM-based decision summarization
- structured prompts
- retrieval/grounding from analytical outputs
- recommendation traceability

Dashboard:

- Streamlit and/or Power BI

---

## 10. Analytical Philosophy

This project follows five rules.

### Rule 1 — Business before model

Do not build a model simply because a model is available.

Start with:

> **What decision are we trying to improve?**

### Rule 2 — Explainability matters

A sophisticated model that a Marketing Director cannot understand is not automatically useful.

### Rule 3 — Correlation is not causation

MMM, uplift modelling and experiments must be interpreted carefully.

### Rule 4 — Every insight must lead somewhere

The desired chain is:

> Observation → Diagnosis → Implication → Action → KPI

### Rule 5 — AI cannot replace evidence

The AI layer summarizes and reasons over validated analytical outputs. It should not manufacture numbers, causal claims or recommendations unsupported by the underlying analysis.

---

## 11. Portfolio Outcomes

The finished project should demonstrate that the author can operate at the intersection of:

**Marketing Strategy + FMCG Commercial Thinking + Analytics + AI**

A strong final portfolio should contain:

1. Executive dashboard
2. Consumer segmentation
3. CLV analysis
4. Basket analysis
5. Demand forecast
6. Marketing effectiveness model
7. Budget optimization
8. Scenario planner
9. AI-generated decision brief
10. Methodology and limitations

---

## 12. Suggested Executive Dashboard

### Page 1 — Business Pulse

- Revenue
- Growth
- Volume
- Margin
- Market share
- Distribution
- Top 5 risks
- Top 5 opportunities

### Page 2 — Category & SKU

- category growth
- SKU growth matrix
- price-volume decomposition
- distribution
- profitability

### Page 3 — Consumer

- segment size
- value
- frequency
- CLV
- category affinity

### Page 4 — Marketing

- spend
- incremental sales
- ROI
- mROI
- response curves

### Page 5 — Scenario Planner

Interactive inputs:

- total budget
- channel allocation
- price
- promotion
- distribution

Outputs:

- sales
- volume
- margin
- ROI
- incremental contribution

---

## 13. Research References

This project draws methodological inspiration from established open-source marketing analytics projects, including:

- Meta Robyn — Marketing Mix Modeling
- Google Meridian — Marketing Mix Modeling
- FMCG customer analytics projects
- Retail/customer segmentation projects

These repositories are learning references, not dependencies of this project.

---

## 14. Disclaimer

This repository is an educational and portfolio project.

All business data is synthetic.

No confidential Hershey, Savola, client, employer or third-party commercial data should be used in this repository.

The project does not represent the views, performance or strategies of any real company.

---

## 15. Roadmap

### Phase 1 — Foundation
- Define schema
- Generate synthetic dataset
- Data quality checks
- KPI layer

### Phase 2 — Commercial Intelligence
- Sales analysis
- Category analysis
- SKU analysis
- Channel analysis
- Market analysis

### Phase 3 — Consumer Intelligence
- RFM
- Segmentation
- CLV
- Basket analysis

### Phase 4 — Predictive Intelligence
- Forecasting
- Propensity
- Scenario modelling

### Phase 5 — Marketing Science
- MMM
- ROI
- mROI
- Budget optimization

### Phase 6 — AI Decision Engine
- Analytical grounding
- Executive summaries
- Recommendation engine
- Decision traceability

### Phase 7 — Portfolio Layer
- Dashboard
- Case study
- Architecture diagram
- Executive presentation

---

## 16. North Star

The ultimate objective is simple:

> **Turn FMCG data into better marketing decisions.**

The project should make it possible for a marketing leader to move from:

**"What happened?"**

to

**"Why did it happen?"**

to

**"What should we do?"**

to

**"What happens if we do it?"**

to

**"Did the decision work?"**
