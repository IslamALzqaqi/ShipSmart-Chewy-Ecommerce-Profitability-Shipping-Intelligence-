# ShipSmart-Chewy-Ecommerce-Profitability-Shipping-Intelligence-
Power BI E-commerce Analytics Project focused on Sales, Profitability, Shipping Optimization, Customer Behavior, and What-if Analysis.
# ShipSmart: Ecommerce Profitability & Shipping Intelligence

**Power BI case study analyzing sales, customer behavior, and shipping cost optimization for an online pet-retail e-commerce business.**

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-217346?style=flat)
![Power Query](https://img.shields.io/badge/Power%20Query-0078D4?style=flat)

---

## 📌 Overview

This project transforms raw e-commerce transactional data into a decision-ready Power BI dashboard. It answers a core business question:

> **How can the business improve sales and profitability while better understanding product performance, customer behavior, geographic demand, and shipping costs?**

The analysis follows a full BI workflow — **Descriptive → Diagnostic → What-if → Prescriptive** — moving from *what happened* to *why*, to *what if we changed something*, to *what we should do about it*.

---

## 🎯 Business Objectives

| # | Objective |
|---|---|
| 01 | Sales & Profitability Analysis |
| 02 | Product Performance |
| 03 | Customer Analysis |
| 04 | Geographic Analysis |
| 05 | Purchasing Behavior (Market Basket Analysis) |
| 06 | Shipping Cost Analysis |
| 07 | What-If Analysis |
| 08 | Decision Support (actionable recommendations) |

---

## 🧱 Analytical Workflow

Business Understanding
↓
Data Exploration
↓
Data Cleaning & Preparation
↓
Data Modeling
↓
DAX & KPI Development
↓
Exploratory Analysis
↓
Power BI Visualization
↓
What-If Analysis
↓
Insights
↓
Recommendations


---

## 🗂️ Data Model

The model consists of the following tables, linked in a star-schema style layout:

- **Sales** — core transactional fact table (Transaction Date, Customer ID, Description, Stock Code, Invoice No, Quantity, Sales, Unit Price, Shipping Cost, COGS, Profit)
- **Products** — product/category attributes and per-mile shipping cost
- **Customers** — customer location details
- **State Mapping** — maps order states to regions
- **Market Basket** — supports affinity/cross-sell analysis
- **Invoice Totals** — order-level aggregates
- **What-if quantity** — a What-if parameter table driving shipping scenario analysis

---

## 📊 Key Metrics (KPIs)

| Metric | Value |
|---|---|
| Total Sales | **$1,553,909.82** |
| Total COGS | $741,424.50 |
| Total Profit | **$427,335.62** |
| Profit Margin | **27.5%** |
| Unique Customers | 3,141 |
| Total Invoices | 11,427 |
| Product Catalog Size | 20 SKUs |
| Data Period | Dec 2020 – Dec 2021 |
| Shipping Cost (Baseline) | **$385,149.70** — 24.8% of Sales, ~90% of Profit |

---

## 🔍 Key Insights

1. **Shipping is a top profitability driver** — shipping cost equals ~90% of total profit, so small efficiency gains have outsized bottom-line impact.
2. **Bulk shipping could save up to $118.19K (30.7%)** — the What-if model shows shipping cost dropping from $385.15K to $266.96K when order quantities scale to 11+ units per shipment.
3. **58% of order lines are single-unit** — most orders currently fall outside the quantity range needed to unlock shipping discounts.
4. **Category profitability ≠ category volume** — Electronics has the highest margin (44.3%) despite the lowest average order quantity (1.38), while Pet Food has the highest average quantity (5.31) but the lowest margin (20.6%).
5. **~21% of sales value has no linked Customer ID** — a data-quality gap that limits customer-level analysis (LTV, cohorts, geography).

---

## 🧮 What-If Analysis: Shipping Cost Simulation

A dynamic **What-if parameter** (`What-if quantity`, range 1–20) drives a blended shipping-cost-factor measure, letting stakeholders simulate the impact of shipping larger quantities per order:

| Shipment Quantity | Cost Multiplier | Shipping Cost | Savings vs. Baseline |
|---|---|---|---|
| 1 | 1.0 | $473.8K | –$88.6K |
| 5 (default) | 0.5 | $326.1K | $59.1K (15.3%) |
| 9 | 0.4 | $296.5K | $88.6K (23%) |
| **11+ (max)** | **0.3** | **$266.96K** | **$118.19K (30.7%)** |

If fully realized, **profit could rise from $427K to ~$546K**, lifting the profit margin from **27.5% to ~35%**.

Core DAX pattern:

```dax
Shipping (Baseline) =
SUMX(
    Sales,
    IF(
        Sales[Quantity] = 1,
        Sales[Shipping Cost],
        Sales[Shipping Cost] + ((Sales[Quantity] - 1) * Sales[Shipping Cost] * 0.7)
    )
)

Shipping (What-if) =
SUMX(
    Sales,
    IF(
        Sales[Quantity] = 1,
        Sales[Shipping Cost],
        Sales[Shipping Cost] + ((Sales[Quantity] - 1) * Sales[Shipping Cost] * [Blended Shipping Cost Factor])
    )
)

Shipping (Difference) = [Shipping (Baseline)] - [Shipping (What-if)]
```

---

## ✅ Recommendations

| # | Recommendation | Priority |
|---|---|---|
| 1 | Negotiate tiered/bulk shipping rates with carriers based on shipment quantity | High |
| 2 | Introduce quantity-based incentives (bundles, multi-unit discounts) to grow average order size | High |
| 3 | Prioritize the Electronics category for marketing investment and cross-sell placement | Medium |
| 4 | Reassess pricing/cost structure for Food and Pet Food categories | Medium |
| 5 | Improve Customer ID capture at checkout to close the 21% sales-tracking gap | Low |

---

## 📁 Dashboard Pages

| Page | Contents |
|---|---|
| **Data Clean Up** | Data preparation and quality checks |
| **Customer Info** | Customer contribution and purchasing behavior |
| **Product Info** | Product/category performance, shipping cost by product |
| **Quantity Info** | Order quantity distribution and cumulative sales |
| **Shipping Metrics** | Baseline vs. What-if shipping cost, running totals, regional shipping map |
| **Market Basket Analysis** | Frequently purchased-together products |
| **Executive Summary** | Top-line KPIs, profitability by category, geographic sales overview |

---

## 🛠️ Tools Used

- **Power BI Desktop** — data modeling, DAX, visualization
- **Power Query** — data cleaning and transformation
- **DAX** — KPI measures, running totals, What-if parameter logic

---

## 📎 Notes

- This project uses a fictitious/simulated e-commerce dataset in the pet-retail space for case-study purposes.
- Built as a self-directed extension of a guided Power BI case study, with all insights, recommendations, and the What-if shipping model developed independently.

---

## 📬 Contact

Feel free to connect or reach out with questions/feedback about this project.
