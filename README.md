# simranpreetkaur_2511852_part4_tableau_dashboard

# Part 4: Tableau Executive Dashboard — README

## 1. Business Problem Summary

The retail leadership team needs an executive dashboard to monitor sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns. The goal is to identify business opportunities and risks to support data-driven decision-making.

---

## 2. Dataset Description

**File:** `data/dashboard_sales_data.xlsx`  
**Total Records:** 4,200 rows | 20 columns  
**Each row** represents one unique retail order.  
**Date Range:** January 1, 2024 – December 31, 2025 (2 full calendar years)  
**Geography:** 19 Indian states across 4 regions (North, South, East, West)

### Field Inventory

| Field | Type | Description | Notes |
|---|---|---|---|
| `order_id` | ID | Unique order identifier | Primary key — 4,200 unique values |
| `customer_id` | ID | Unique customer identifier | 4,096 unique customers |
| `order_date` | Date | Date order was placed | Range: 2024-01-01 to 2025-12-31 |
| `ship_date` | Date | Date order was shipped | Range: 2024-01-03 to 2026-01-06 |
| `customer_segment` | Categorical | Consumer, Corporate, Home Office | 3 unique values |
| `region` | Geographic | North, South, East, West | 4 regions |
| `state` | Geographic | Indian state | 19 unique states |
| `city` | Geographic | City of delivery | Multiple cities per state |
| `category` | Categorical | Furniture, Office Supplies, Technology | 3 unique values |
| `sub_category` | Categorical | Product sub-category | 13 unique values |
| `product_name` | Categorical | Individual product name | Multiple products |
| `ship_mode` | Categorical | Standard Class, Second Class, First Class, Same Day | 4 values |
| `campaign_channel` | Categorical | Organic, Social, Paid, Email, Referral | 24 null values |
| `sales` | Numerical | Revenue per order (₹) | Range: ₹72.91 – ₹4,27,418 |
| `quantity` | Numerical | Units ordered | Range: 1–10 |
| `discount` | Numerical | Discount rate applied | Values: 0, 0.05, 0.10, 0.15, 0.20, 0.25, 0.30, 0.35 |
| `profit` | Numerical | Profit per order (₹) | Can be negative (loss-making orders) |
| `delivery_days` | Numerical | Days from order to ship | Range: 0–9 |
| `customer_rating` | Numerical | Customer satisfaction score | Range: 2.1–5.0 | 32 null values |
| `return_flag` | Binary/Flag | 0 = Not returned, 1 = Returned | 191 returns (~4.5% return rate) |

---

## 3. Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`

The packaged workbook contains:
- 7 supporting worksheet views (Sales Trend, Regional Performance, Category Profitability, Customer Segment, Shipping Performance, Discount vs Profit, Return Analysis)
- 1 Executive Dashboard combining all key views
- 5 calculated fields (Profit Margin, Cost, Average Order Value, Return Rate, Shipping Delay Bucket)
- Interactive filters for Region, Category, Customer Segment, Date, Ship Mode, and Campaign Channel

---

## 4. Calculated Fields Created

| Calculated Field | Formula | Purpose |
|---|---|---|
| `Profit Margin` | `SUM([Profit]) / SUM([Sales])` | Measures what % of sales becomes profit |
| `Cost` | `SUM([Sales]) - SUM([Profit])` | Derives cost since it is not directly available |
| `Average Order Value` | `SUM([Sales]) / COUNTD([Order Id])` | Average revenue per unique order |
| `Return Rate` | `SUM([Return Flag]) / COUNT([Order Id])` | % of orders that were returned |
| `Shipping Delay Bucket` | `IF [Delivery Days] = 0 THEN "Same Day" ELSEIF [Delivery Days] <= 2 THEN "Fast (1-2 days)" ELSEIF [Delivery Days] <= 4 THEN "Standard (3-4 days)" ELSEIF [Delivery Days] <= 6 THEN "Slow (5-6 days)" ELSE "Very Slow (7+ days)" END` | Groups delivery speed into meaningful categories |

---

## 5. Dashboard Components

The Executive Dashboard includes:
- **KPI Cards:** Total Sales, Total Profit, Overall Profit Margin, Return Rate, Average Order Value
- **Sales Trend View:** Monthly sales and profit line chart over time (2024–2025)
- **Regional Performance View:** Sales and profit by region and state (map + bar chart)
- **Category Profitability View:** Profit by category and sub-category (bar/highlight table)
- **Customer Segment View:** Sales and profit comparison across Consumer, Corporate, Home Office
- **Shipping Performance View:** Delivery delay by ship mode and Shipping Delay Bucket
- **Discount vs Profit View:** Scatter plot showing discount rate vs profit relationship
- **Return Analysis View:** Return rate by category, segment, and region

---

## 6. Filters and Interactions Used

The following interactive filters are applied to the dashboard:
- **Region** — Filter all views by North/South/East/West
- **Category** — Filter by Furniture / Office Supplies / Technology
- **Customer Segment** — Filter by Consumer / Corporate / Home Office
- **Order Date** — Date range filter (year/quarter/month level)
- **Ship Mode** — Filter by Standard Class / First Class / Second Class / Same Day
- **Campaign Channel** — Filter by Organic / Social / Paid / Email / Referral

Action filters are set so clicking a region on the map filters all other charts on the dashboard.

---

## 7. Key Business Insights

1. **Technology drives the highest profit margins** despite not always having the highest sales volume.
2. **Furniture sub-categories (Tables, Bookcases) show negative profit** when discounts exceed 20%, indicating a pricing risk.
3. **West region leads in total sales** but margin analysis reveals profitability varies significantly by state.
4. **Consumer segment has the highest return rate**, suggesting a product-fit or expectation gap.
5. **Heavy discounts (30–35%) consistently result in losses** — discount strategy needs review.
6. **Standard Class shipping has the longest average delivery time** but is used most frequently.
7. **Q4 shows the highest sales peak** across both years, indicating a seasonal demand pattern.
8. **Home Office segment has the lowest average order value** but reasonable profit margins.

---

## 8. Dashboard Story Summary

The dashboard tells the story of a retail business that is growing in revenue but facing margin pressure from aggressive discounting and category-level losses. The West region leads sales, but profitability is uneven. Technology products are the star performers. Furniture, particularly Tables and Bookcases with high discounts, are loss leaders. The Consumer segment, while the largest by volume, carries the highest return risk. Leadership should focus on tightening discount policies for Furniture, doubling down on Technology in high-margin regions, and investigating return drivers in the Consumer segment.

---

## 9. Assumptions and Limitations

**Assumptions:**
- Each row represents one unique order (`order_id` is the primary key)
- Currency is Indian Rupees (₹) based on geography (Indian states and cities)
- `delivery_days` = `ship_date` − `order_date`; a value of 0 means same-day shipment
- `return_flag` = 1 means the order was returned; 0 means not returned
- Negative profit values are valid and represent loss-making orders
- 32 null `customer_rating` values are excluded from rating-based analysis
- 24 null `campaign_channel` values are shown as "Unknown" or excluded from channel analysis

**Limitations:**
- No cost breakdown available (cost is derived, not directly measured)
- Customer-level repeat purchase behavior cannot be fully analyzed (limited customer history)
- Return reasons are not captured — only a binary return flag
- Campaign channel has missing data (~0.6%) which may affect channel ROI analysis
- The dataset covers only 2 years (2024–2025); longer trend analysis is not possible

---

## 10. Screenshots Included

| File | Description |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard view |
| `screenshots/sales_trend_view.png` | Monthly sales and profit trend chart |
| `screenshots/regional_performance_view.png` | Regional and state-level sales/profit map |
| `screenshots/category_profitability_view.png` | Category and sub-category profitability breakdown |
| `screenshots/filter_interaction_view.png` | Dashboard showing active filter interaction |
