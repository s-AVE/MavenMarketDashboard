# AdventureWorksCompany-PowerBI-Dashboard 

![](image.jpg)


## Introduction
Maven Market operates 24 grocery stores across Canada, United States, and Mexico, serving over 10,000 customers with a catalog of 111 product brands. Maven Market operated across 24 stores serving 10,281 unique customers throughout the 1997–1998 period. 

This analysis covers three dimensions of business performance overall sales health, product portfolio efficiency, and customer and store behavior 
drawing from the Executive Summary, Product Performance, and Customer & Store Detail dashboards.

> [!IMPORTANT]
**Data Cutoff:**
Data ends on **December 31st, 1998**

---

## Table of Content
📁 1. [Problem Statement](#1-problem-statement)  

📁 2. [Skills Demonstrated](#2-skills-demonstrated)  

📁 3. [Data Sourcing](#3-data-sourcing)  

📁 4. [Data Transformation](#4-data-transformation)  

📁 5. [Data Modeling](#5-data-modeling)  

📁 6. [Data Visualization](#6-data-visualization)

📁 7. [Data Analysis](#7-data-analysis)  

📁 8. [Conclusions](#8-conclusions)  

📁 9. [Recommendations](#9-recommendations)  

---
## 1. Problem Statement
As the business completes its second year of operations, management needs clarity on three core questions:

1. Is Maven Market financially healthy and sustainable in terms of profitability and returns?
2. Is revenue growth consistent or dependent on specific periods?
3. Is revenue and profitability concentrated in a small set of brands or evenly distributed?
4. Is the product portfolio aligned with modern consumer preferences?
5. Is revenue geographically balanced or overly concentrated?
6. Do store formats perform consistently across the portfolio?
7. Is the loyalty program effective in driving premium customer conversion?
8. Which store formats should be prioritized for expansion?
   
---

## 2. **Skills Demonstrated**
- **Data Transformation** - converting raw, unstructured data from multiple sources into a clean, standardized format
- **Data Modeling** - star schema design with fact and dimension tables
- **Data Visualization** - creating KPI cards, gauge charts, line charts, donut charts, and matrix tables
- **Data Analysis** - discover actionable insights, support critical decision-making, and validate hypotheses

---

## 3. **Data Sourcing**
The dataset is based on the AdventureWorks sample database provided by Microsoft. It consists of 8 tables:

| Table | Description |
|---|---|
| Transaction | Transaction-level fact table |
| Return | Return transaction-level fact table |
| Customer Lookup | Customer demographics and attributes |
| Product Lookup | Product names, categories, and pricing |
| Stores Lookup | Stores type, address, and area |
| Regions Lookup | Sales region and continent |
| Calendar Lookup | Date dimension table |
| Product Brand Lookup | Brand average in shelf, performance zone, and margin brand |

---

## 4. **Data Transformation**  
Data was **cleaned** and transformed using Power Query (M Language):
- Standardized tables name
  - ![](asset/change_name.png)
- Appending transaction table
  - ![](asset/appending_tables.png)
- Removing duplicate, null, or error rows from all Data
  - ![](asset/checking_error_column.png)
- Replacing values
  - ![](asset/replace_value.png)
- Standardized date formats across all tables and creating column for every date element
  - ![](asset/change_format_column.png)
- Creating calculated column
  - ![](asset/adding_new_column2.png)
  - ![](asset/adding_new_column.png)
- Defining key column
  - ![](asset/define_keycolumn.png)
    --- 
- Customing calculation (DAX Measure)
  - Data Analysis Expression that used in this project
    - ![](asset/dax.png)

  - Additional DAX for the highlight revenue trending
    - ![](asset/dax_highlight_revenue_trending.png)

---

## 5. **Data Modeling**
![](asset/data_modelling.png)
- **Fact Table**: Sales Data (transactions), Return Data (transaction)
- **Dimension Tables**: Customer, Product, Territory, Calendar, Category Product, and Subcategory Product
- All relationships are **single-direction** (one-to-many)
- A dedicated **measure table** (`Measures`) stores all DAX calculations separately from raw data tables
- No bi-directional relationships to maintain query performance
- Unrelated table: there are measure table (for grouping DAX calculation), transaction 1997 & 1998 (unused table, use only for appending table, 
date slicer (for slicer in highlight revenue trending), target parameter and trendline selection (use for brand positioning in product performance)

---

## 6. **Data Visualization**  
![](asset/0dashboard.png)
The dashboard consists of 3 report pages:
- **Executive Summary**
  ---
  - ![](asset/1executive_summary.jpg)
- **Product Performance**
  ---
  - ![](asset/2product_performance.jpg)
- **Customer & Store Detail**
  ---
  - ![](asset/3custnstore_detail.jpg)

---

## 7. Data Analysis

### A. Business Performance

Maven Market recorded 1,560 total orders generating $1.8M in total revenue and $1.05M in total profit, representing a profit margin of 58.3% an exceptionally healthy profitability ratio for a grocery retail operation. The business retains $0.58 of every $1.00 sold, confirming strong pricing power and cost discipline across the portfolio. A return rate of 0.99% below the 1% threshold further validates product quality consistency, indicating that less than 1 in 100 items purchased is returned across the entire catalog. Revenue grew approximately 110% year-over-year, with December 1998 peaking at $120.16K driven by seasonal demand while October 1997 recorded the lowest point at $42.34K.

### B. Product Performance

Hermanos leads all brands at $56.7K in revenue, with the top 10 brands clustering tightly between $40K and $57K a competitive mid-tier with no single dominant outlier. The average margin of 59.67% is consistent across all top brands, confirming that volume and profitability are aligned for the strongest performers. Brand positioning analysis confirms that Zone 1 brands (High Revenue + High Margin) dominate the top performers, while Zone 4 brands (Low Revenue + Low Margin) represent a drag on portfolio efficiency.

However, a cluster of slow-moving brands averages 7 days on shelf 75% slower than the 4-day portfolio average tying up inventory capital without proportional return. The top 3 returned products Hermanos Red Pepper (2.83%), Shady Lake Spaghetti (2.93%), and Walrus Merlot Wine (2.79%) all exceed the portfolio return rate of 0.99% by nearly 3x, signaling
product-specific quality issues. Additionally, 55.96% of products remain non-recyclable, presenting a sustainability gap as consumer preferences increasingly favor eco-friendly
options.

### C. Store & Regional Performance

North West dominates at $847.8K - 48% of total revenue creating a significant geographic concentration risk. Mexico collectively contributes $479K across three separate regions
(Mexico Central $330.4K, Mexico South $87.3K, Mexico West $61.3K), making it the second-largest market at 27.1% of revenue but operating without a unified strategy. Canada West underperforms at $107.7K relative to its market potential, and Central West at $9.3K is effectively non-operational.

Of 24 stores, 13 exceed the average revenue of $73,522.8 while 11 fall below it. Store 5 is severely underperforming at $4.9K a 34.8x gap compared to the top store at $170.4K. Deluxe Supermarket consistently delivers the highest revenue per store and per sqft, while Small Grocery contributes only 1.9% of total revenue ($34K) the lowest of all store formats.

### D. Customer Profile

Maven Market serves 10,281 customers with an average age of 54 years. Revenue is evenly distributed across all age groups peaking at the 40–49 segment ($271.6K) with only a 10.8% decline to the 80–89 segment ($242.2K) confirming strong cross-generational appeal. Gender split is near-equal: female $891.7K vs male $872.8K a healthy diversification with no concerning skew.

However, 90.4% of revenue comes from Standard priority customers, revealing a critical loyalty program gap. The top individual customer, Mr. Ida Rodriguez, generates $2.2K from 270 orders at an average of $8.15 per transaction a high frequency, low-basket pattern that reflects a broadly distributed rather than premium-driven revenue structure. On the occupation side, Professional customers dominate at $574.0K (31.9% of revenue), while Clerical at $30.6K is significantly underrepresented pointing to a pricing or accessibility gap for lower-income segments.

---

## 8. Conclusions

Maven Market demonstrates strong business fundamentals with 58.3% profit margin, sub-1% return rate, and 110% YoY revenue growth. The business has a well-diversified customer base, consistent product margins, and a clear top-performing store format in Deluxe Supermarket. However, three structural challenges directly threaten the sustainability of this growth and must be addressed:

**1. Geographic concentration risk**
With 48% of revenue dependent on North West alone, the business is structurally vulnerable to regional disruption. Mexico the second-largest market at $479K combined is fragmented across three regions without a unified strategy, limiting its growth potential. Central West at $9.3K and Canada West at $107.7K represent further underperformance that reduces overall portfolio resilience.

**2. Loyalty program underutilization**
90.4% of customers remain on Standard priority with an average transaction value of only $8.15. This indicates that Maven Market's existing loyalty structure is not successfully
converting frequent buyers into higher-value members leaving significant premium revenue unrealized. The gap between Priority customers (9.6%) and Standard customers (90.4%)
confirms that the current program lacks sufficient incentive for tier upgrading.

**3. Product and store portfolio drag**
Slow-moving brands at 7 days on shelf, top returned products exceeding portfolio rate by 3x, Small Grocery at only 1.9% of revenue, and Store 5 at $4.9K all represent inefficiencies that compress overall performance. The 34.8x revenue gap between the best and worst store signals structural variance that goes beyond normal store-to-store variation pointing to systemic issues in underperforming locations.

---

## 9. Recommendations

The following recommendations directly address the three structural challenges identified in the conclusions, ordered by priority and expected business impact.

---

### 1) Reduce Geographic Concentration Risk
**Problem:** North West contributes 48% of total revenue. Central West at $9.3K is non-operational. Mexico's $479K potential is fragmented across three regions.

**Recommendation:**
- Develop a **unified Mexico market strategy** consolidating Mexico Central ($330.4K), Mexico South ($87.3K), and Mexico West ($61.3K) under one regional structure the combined $479K warrants dedicated management and investment
- **Investigate Canada West underperformance** at $107.7K audit store locations, product mix, and pricing alignment with local consumer preferences
- Conduct an **immediate review of Central West** at $9.3K determine whether a viable growth path exists or whether resources should be reallocated to stronger markets
- Set a target to **reduce North West dependency from 48% to below 35%** within 2 years through regional activation

---

### 2) Upgrade Loyalty Program Convert Standard to Priority
**Problem:** 90.4% Standard-priority customers. Top customer averages only $8.15 per transaction despite 270 total orders.

**Recommendation:**
- Launch a **tiered loyalty upgrade campaign** targeting Standard customers with 50+ orders offer Bronze or Silver membership with tangible benefits such as exclusive discounts, early product access, and priority checkout
- Introduce a **minimum basket incentive** reward customers who exceed $15 per transaction with points or discounts to shift behavior from low-basket frequent visits toward higher-value transactions
- Target **Golden membership conversion** for high-frequency buyers like Mr. Ida Rodriguez (270+ orders) through personalized outreach with exclusive offers
- Benchmark: converting 10% of Standard customers to Priority at a modest 20% higher spend could generate an estimated **$32K+ in incremental annual revenue**

---

### 3) Optimize Product Portfolio Remove Drag, Protect Stars
**Problem:** Slow movers at 7 days on shelf. Top 3 returned
products exceed return rate by 3x. 55.96% non-recyclable.

**Recommendation:**
- **Give slow movers a 90-day promotional window** brands averaging 7+ days on shelf (ADJ, American, Applause, Atomic, BBB Best) should be promoted aggressively before removal. Freed shelf space should be reallocated to Zone 1 brands
- **Quality audit for top returned products** Hermanos Red Pepper, Shady Lake Spaghetti, and Walrus Merlot Wine allrequire supplier review. Hermanos Red Pepper is the highest priority given its parent brand is the #1 revenue driver
- **Increase recyclable product mix** from 44.04% toward 55%+ in the next catalog cycle prioritize Zone 1 brands that are also recyclable for marketing and shelf placement
- **Protect Zone 1 brands** (Hermanos, Tell Tale, Ebony) with consistent stock availability and prime shelf positioning

---

### 4) Expand Deluxe Supermarket Phase Out Small Grocery
**Problem:** Small Grocery at 1.9% of revenue ($34K). Store 5 at $4.9K - 34.8x below the top store. Deluxe Supermarket delivers the highest revenue per sqft consistently.

**Recommendation:**
- **Convert Small Grocery locations to Deluxe Supermarket format** where feasible Store 13 ($170.4K) and Store 17 ($157.7K) confirm this format can deliver 5x+ the revenue of a Small Grocery location
- **Conduct urgent operational audit of Store 5** at $4.9K if no viable recovery path exists within 6 months, proceed with closure or relocation
- **Standardize the 11 below-average stores** using best practices from top Deluxe Supermarket locations covering product assortment, shelf layout, promotional cadence, and staff training
- **Default all new store openings to Deluxe Supermarket format** the data consistently supports this as the highest-return expansion vehicle

---

### 5) Capitalize on Seasonal Demand
**Problem:** December 1998 peaked at $120.16K while mid-year plateaued at $92–101K. Tell Tale generated 87.5% of its annual revenue in December alone.

**Recommendation:**
- **Build a formal Q4 seasonal strategy** develop dedicated holiday promotions, seasonal bundles, and pre-positioned inventory starting October each year
- **Position Tell Tale as the seasonal anchor brand** for holiday campaigns bundle it with year-round performers like Hermanos to drive cross-sell during peak season
- **Address the mid-year revenue plateau** with a targeted May–June promotional event a loyalty double-points campaign or limited seasonal product launch could create a second revenue peak and reduce annual revenue volatility

---

### 6) Target High-Value Customer Segments
**Problem:** Clerical at $30.6K is severely underrepresented. Graduate Degree holders at $93.6K are underperforming relative to their likely disposable income.

**Recommendation:**
- **Protect the Professional segment** at 31.9% of revenue align product assortment, store experience, and loyalty rewards to this group's preferences
- **Investigate the Clerical gap** value bundles and entry-level loyalty incentives designed for lower-income segments could unlock this underserved group
- **Test premium product lines in high-education catchment areas** Graduate Degree customers likely have higher disposable income; organic or premium ranges could unlock a new revenue tier without alienating the core base
- **Maintain accessible pricing for the working-class core** Partial High School ($533.2K) and High School Degree ($521.7K) customers are the revenue backbone and must not be displaced by any premium repositioning

---

## Priority Action Summary

| Priority | Action | Expected Impact |
|---|---|---|
| 🔴 Immediate | Audit Store 5 ($4.9K) | Recover or reallocate |
| 🔴 Immediate | Quality review top 3 returned products | Protect brand equity |
| 🔴 Immediate | Review Central West ($9.3K) | Recover or exit |
| 🟡 Short-term | Launch loyalty upgrade campaign | Increase avg basket size |
| 🟡 Short-term | Promote or remove 7-day slow movers | Improve shelf velocity |
| 🟡 Short-term | Build Q4 seasonal strategy | Maximize December peak |
| 🟢 Medium-term | Convert Small Grocery to Deluxe format | Higher revenue per sqft |
| 🟢 Medium-term | Unify Mexico regional strategy | Unlock $479K market |
| 🟢 Medium-term | Increase recyclable product mix to 55%+ | Sustainability positioning |
| 🟢 Long-term | Reduce North West dependency to <35% | Geographic risk reduction |

---

### Repository Contents
 - Power BI Dashboard File: The main PBIX File [Maven Market](Maven_Market) containing the analysis and visualizations.
 - Data Sources: [Raw Dataset](raw_data) used in the project.
 - Screenshots/Reports: [Exported visualizations](asset) for sharing insights.
 - README.md: Project documentation (this file)

---

_Source of Dataset: Maven Analytics_
