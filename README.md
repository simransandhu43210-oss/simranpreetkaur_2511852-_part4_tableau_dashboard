# simranpreetkaur_2511852_part4_tableau_dashboard

# Retail Executive Dashboard — Tableau Project
## Part 4: Tableau Executive Dashboard & Data Storytelling

---

## 1. Business Problem Summary

The retail leadership team required an executive dashboard to monitor and analyze sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns across 2024–2025. The objective was to build a Tableau dashboard that helps leadership identify business opportunities and risks, and supports data-driven decision-making. The dashboard is designed to tell a clear business story — not a collection of random charts — connecting insights across sales, margins, customers, and operations.

---

## 2. Dataset Description

**File:** `data/dashboard_sales_data.xlsx`
**Records:** 4,200 rows | 20 columns
**Each row:** One unique retail order
**Date Range:** January 1, 2024 – December 31, 2025 (2 full years)
**Geography:** 19 Indian states across 4 regions (North, South, East, West)
**Total Sales:** ₹21,70,17,652 | **Total Profit:** ₹3,33,06,313 | **Overall Margin:** 15.35%

### Field Reference

| Field | Type | Description |
|---|---|---|
| order_id | ID | Unique per row — primary key |
| customer_id | ID | 4,096 unique customers |
| order_date | Date | Jan 2024 – Dec 2025 |
| ship_date | Date | Jan 2024 – Jan 2026 |
| customer_segment | Categorical | Consumer, Corporate, Home Office |
| region | Categorical | North, South, East, West |
| state | Geographic | 19 Indian states |
| city | Geographic | City of delivery |
| category | Categorical | Furniture, Office Supplies, Technology |
| sub_category | Categorical | 13 sub-categories |
| product_name | Categorical | Individual product |
| ship_mode | Categorical | Standard Class, Second Class, First Class, Same Day |
| campaign_channel | Categorical | Organic, Social, Paid, Email, Referral (24 nulls) |
| sales | Numerical | Revenue (₹) — Range: ₹72.91 – ₹4,27,418 |
| quantity | Numerical | Units per order — Range: 1–10 |
| discount | Numerical | Rate: 0 to 0.35 (0% to 35%) |
| profit | Numerical | Can be negative for high-discount orders |
| delivery_days | Numerical | Days from order to ship — Range: 0–9 |
| customer_rating | Numerical | 2.1–5.0 (32 nulls) |
| return_flag | Binary | 0 = Not returned, 1 = Returned |

---

## 3. Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`

The packaged workbook contains:
- **8 worksheet views** — Sales Trend, Regional Map, Regional Bar, Category Profitability, Customer Segment, Shipping Performance, Discount vs Profit, Return Analysis
- **3 KPI sheets** — Total Sales, Total Profit, Profit Margin
- **1 Executive Dashboard** — combining all views with filters and action interactions
- **6 calculated fields** — Profit Margin, Cost, Average Order Value, Return Rate, Return Rate Avg, Shipping Delay Bucket

---

## 4. Calculated Fields Created

| Field | Formula | Purpose |
|---|---|---|
| Profit Margin | `SUM([profit]) / SUM([sales])` | % of revenue that becomes profit — shows 15.35% overall |
| Cost | `SUM([sales]) - SUM([profit])` | Derived cost since not directly available in data |
| Average Order Value | `SUM([sales]) / COUNTD([order_id])` | Average revenue per unique order |
| Return Rate | `SUM([return_flag]) / COUNT([order_id])` | % of total orders returned — shows ~4.55% overall |
| Return Rate Avg | `AVG([return_flag])` | Used in Return Analysis view for correct per-group rates |
| Shipping Delay Bucket | IF/ELSEIF on [delivery_days] | Groups: Same Day / Fast 1-2 / Standard 3-4 / Slow 5-6 / Very Slow 7+ |

---

## 5. Dashboard Components

### KPI Row (top of dashboard)
- **Total Sales:** ₹21,70,17,652
- **Total Profit:** ₹3,33,06,313
- **Profit Margin:** 15.35%

### Chart Views

| View | Chart Type | Key Finding |
|---|---|---|
| Sales Trend View | Dual axis line chart | Sales volatile ₹63L–₹1.09Cr monthly; no clear seasonal peak |
| Regional Performance View | India filled map | South leads with ₹6.47Cr sales; East has best margin 15.55% |
| Regional Bar View | Horizontal bar chart | South > North > West > East by total sales |
| Category Profitability View | Horizontal bar with hierarchy | Technology = 84% of profit; Furniture margin only 6.9% |
| Customer Segment View | Grouped bar chart | All 3 segments roughly equal ~₹7Cr each |
| Shipping Performance View | Highlight table heatmap | Standard Class = 58% of orders; avg 4.71 day delivery |
| Discount vs Profit View | Scatter plot with trend lines | Negative correlation -0.27; 27% of 30%+ discount orders lose money |
| Return Analysis View | Stacked horizontal bar | Furniture 7.67% return rate; Home Office segment 5.67% |

---

## 6. Filters and Interactions Used

### Dashboard Filters (visible on dashboard)
- **Region** — filters all views by North/South/East/West
- **Category** — filters by Furniture / Office Supplies / Technology
- **Customer Segment** — filters by Consumer / Corporate / Home Office
- **Order Date** — year/date range filter
- **Ship Mode** — filters by shipping type

### Action Filter (interactivity)
- **Click Region to Filter All** — clicking any region on the map or regional bar chart filters all other charts on the dashboard simultaneously
- Source: Regional Performance View
- Target: All sheets on dashboard
- Clearing selection: Shows all values (resets dashboard)

---

## 7. Key Business Insights

1. **Technology dominates profitability** — generates ₹2.80Cr (84%) of total ₹3.33Cr profit at 18%+ margins across all sub-categories
2. **Furniture is a margin drain** — ₹5.16Cr in sales but only 6.9% profit margin; Tables and Bookcases at 5.7% each
3. **South region leads sales** at ₹6.47Cr but East has the best margin at 15.55%
4. **High discounts destroy profit** — 161 of 592 orders with 30%+ discounts result in negative profit (27.2% loss rate)
5. **Standard Class shipping dominates** (58% of orders, avg 4.71 days) with 201 orders taking 7+ days
6. **Furniture has highest return rate** at 7.67% vs Technology's 3.03%
7. **Home Office segment has highest returns** at 5.67% despite highest total sales
8. **All customer segments nearly equal** in sales — ₹7.45Cr (Home Office), ₹7.19Cr (Consumer), ₹7.06Cr (Corporate)

---

## 8. Dashboard Story Summary

The business is profitable at 15.35% overall margin but faces concentration risk — Technology generates 84% of profit. Furniture underperforms with 6.9% margins driven by excessive discounting. The South region leads sales while the East region is most efficient. All three customer segments contribute equally to revenue, showing a healthy diversified base. The key risks are: uncapped discounts eroding Furniture margins, Standard Class delivery delays generating return risk, and over-reliance on Technology for profitability. Priority actions are discount governance policy implementation and a Furniture margin recovery program.

---

## 9. Assumptions and Limitations

### Assumptions
- Each row = one unique order (order_id is primary key)
- Currency = Indian Rupees (₹) based on Indian state geography
- delivery_days = ship_date − order_date; 0 = same-day shipment
- return_flag = 1 means returned; 0 means not returned
- Negative profit values are valid (loss-making orders due to high discounts)
- 32 null customer_rating values excluded from any rating analysis
- 24 null campaign_channel values excluded from channel analysis
- Region field (North/South/East/West) treated as text dimension — not a Tableau geographic role

### Limitations
- No return reason data — only binary return flag captured
- Cost is derived (Sales − Profit), not actual COGS
- Campaign channel has 24 missing values — channel ROI analysis incomplete
- Customer repeat purchase behavior cannot be reliably determined
- Only 2 years of data — long-term trends and seasonality cannot be confirmed

---

## 10. Screenshots Included

| File | Shows |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard with all views, KPIs, and filters |
| `screenshots/sales_trend_view.png` | Monthly Sales & Profit dual axis line chart (2024–2025) |
| `screenshots/regional_performance_view.png` | India state map colored by Sales with regional filter |
| `screenshots/category_profitability_view.png` | Category and sub-category profit horizontal bar chart |
| `screenshots/filter_interaction_view.png` | Dashboard showing active filter/action interaction applied |



