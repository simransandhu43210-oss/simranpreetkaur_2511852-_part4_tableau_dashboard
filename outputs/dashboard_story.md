# Dashboard Story
## Retail Executive Dashboard — Sales & Business Intelligence (2024–2025)
### Written for Leadership Audience

---

## Executive Summary

Our retail business generated **₹21.7 crore in total sales** and **₹3.33 crore in profit** across 2024–2025, maintaining a steady overall profit margin of **15.35%**. While these headline numbers reflect a stable business, the dashboard reveals a more nuanced story beneath the surface — one of category imbalance, discount risk, and untapped regional opportunity that leadership must address to sustain and accelerate growth.

The central finding is this: **Technology is carrying the business.** It contributes 84% of total profit despite being one of three product categories. Furniture — our second-largest category by sales — generates margins of only 6.9%, dragged down by aggressive discounting and high return rates. If we do not course-correct on Furniture pricing and discount policy, it will continue to dilute our overall profitability.

---

## What Is Performing Well

**Technology is our profit engine.** Copiers, Accessories, Phones, and Machines all achieve consistent margins around 18% — well above the company average of 15.35%. These four sub-categories alone contribute ₹2.80 crore of the ₹3.33 crore total profit. The South region leads all regions in total sales at ₹6.47 crore, demonstrating strong market penetration. The East region, while smaller in revenue at ₹4.89 crore, achieves our best profit margin at 15.55% — suggesting disciplined pricing practices worth replicating.

Customer segment performance is well-balanced across Consumer, Corporate, and Home Office — each contributing approximately ₹7 crore in sales. This diversification is a strategic strength that protects the business from over-reliance on any single customer group. The shipping heatmap confirms that Same Day and First Class options are performing as expected, with near-zero delayed deliveries for premium shipping tiers.

---

## What Is Underperforming

**Furniture is a margin drain.** With ₹5.16 crore in sales but only ₹35.6 lakh in profit — a 6.9% margin — Furniture is significantly pulling down our overall profitability. The sub-categories Tables and Bookcases are the weakest performers, each achieving only 5.7% margins. The scatter plot confirms the root cause: Furniture orders receive the steepest discounts, and those discounts are directly destroying margin. 27.2% of orders with discounts above 30% result in outright losses.

**Standard Class shipping is a customer experience risk.** With 2,435 orders (58% of total) using Standard Class and an average delivery time of 4.71 days, we have 201 orders taking 7 or more days to ship — a category that risks customer dissatisfaction and returns. This is visible in the shipping heatmap where the Standard Class + Very Slow cell has 201 orders.

**The Home Office segment has the highest return rate at 5.67%**, nearly double Technology's return rate of 3.03%. Furniture's category-level return rate of 7.67% is the highest across all categories — more than twice Technology's. These returns represent lost revenue, reverse logistics costs, and potential reputational damage.

---

## What Risks Are Visible

**Discount policy is the most immediate financial risk.** There is a confirmed negative correlation (-0.27) between discount rates and profit. Of 592 orders with discounts of 30% or more, 161 generated negative profit — meaning the business lost money on those transactions. Without a formal discount governance policy, this erosion will continue.

**Revenue concentration in Technology creates fragility.** While Technology's performance is outstanding, generating 84% of profit from one category means any supply chain disruption, price competition, or demand shift in Technology would severely impact overall business health.

**Monthly sales volatility makes planning difficult.** Sales ranged from ₹63 lakh (August 2024) to ₹1.09 crore (August 2025) month-to-month with no clear seasonal pattern. This volatility suggests the business is heavily influenced by a small number of large orders, making forecasting unreliable.

---

## What Opportunities Are Visible

**East region's margin discipline is replicable.** East achieves the best profit margin (15.55%) despite lower sales volume. Understanding and applying East's pricing and discount practices to the West region — our lowest margin at 15.14% — could improve overall profitability without any new sales effort.

**Office Supplies is an underinvested category.** With only ₹1.14 crore in sales but a 14.9% margin and the lowest return rate (3.65%), Office Supplies represents a low-risk, healthy-margin category that could be scaled with targeted marketing investment.

**Premium shipping tiers are underutilized.** Only 241 orders (5.7%) use Same Day shipping. Promoting premium shipping options for high-value orders — particularly Technology products — could improve customer satisfaction and potentially justify price premiums.

---

## Recommended Business Actions

1. **Implement a discount governance policy immediately.** Cap Furniture discounts at 20% and require management approval for any discount above 25% across all categories. This single action could recover significant margin on the 592 high-discount orders.

2. **Investigate and resolve Standard Class delivery delays.** The 201 orders taking 7+ days on Standard Class need root cause analysis — whether these are specific states, product types, or logistics partner failures.

3. **Replicate East region's pricing discipline business-wide.** Conduct a detailed analysis of East's discount patterns and apply learnings to West and North regions.

4. **Launch a Furniture return reduction program.** Add detailed product imagery, accurate dimensions, and customer reviews to Furniture listings. Consider quality checks for Tables and Bookcases before dispatch.

5. **Invest in growing Office Supplies.** With a strong 14.9% margin and low return rate, this category can be scaled with minimal risk through targeted B2B campaigns aimed at the Corporate segment.

---

## Limitations of the Dashboard

- **No return reason data** — the dataset only captures whether an order was returned (binary flag), not why. This limits root cause analysis for return reduction.
- **No customer lifetime value** — with 4,096 unique customers across 4,200 orders, most customers appear to have placed only one order. Whether they are repeat customers cannot be reliably determined.
- **Derived cost only** — the Cost calculated field (Sales minus Profit) is a derived metric, not actual cost data. True COGS, logistics costs, and overhead are not captured.
- **Campaign channel has 24 missing values** — ROI analysis by marketing channel is incomplete.
- **Two-year dataset limits long-term trend analysis** — seasonal patterns and multi-year growth trends cannot be confirmed with only 24 months of data.

---

## Suggested Next Analysis

1. **Discount ROI Analysis** — quantify exactly how much profit is lost per percentage point of discount by category to build the business case for discount caps.
2. **Customer Cohort Analysis** — identify repeat customers and compare their lifetime value and return rates against one-time buyers.
3. **State-Level Deep Dive** — within the South region, identify which specific states drive the highest sales and margins to focus field sales resources.
4. **Return Reason Survey** — implement return reason capture at the point of return to enable root cause analysis for Furniture and Home Office returns.
5. **Shipping Cost vs Revenue Analysis** — quantify the cost of Standard Class delays in terms of returns and customer churn to build the case for shipping investment.
