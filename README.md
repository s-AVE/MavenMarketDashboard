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

Maven Market recorded 1,560 total orders generating $1.8M in total revenue and $1.05M in total profit, representing a profit 
margin of 58.3% an exceptionally healthy profitability ratio for a grocery retail operation. 

The business retains $0.58 of every $1.00 sold, confirming strong pricing power and cost discipline across the portfolio. 
A return rate of 0.99% below the 1% threshold further validates product quality consistency, 
indicating that less than 1 in 100 items purchased is returned across the entire catalog.

---

### B. Product Performance

**Revenue & Brand**
Hermanos leads all brands at $56.7K in revenue, with the top 10 brands clustering tightly between $40K and $57K a 
competitive mid-tier with no single dominant outlier. The average margin of 59.67% is consistent across all top brands,
confirming volume and profitability are aligned. However, a cluster of slow-moving brands averages 7 days on shelf 75%
slower than the 4-day portfolio average and the top 3 returned products all exceed the portfolio return rate by 3x.

---

### C. Store Performance

North West dominates at $847.8K - 48% of total revenue creating a significant concentration risk. Mexico collectively
contributes $479K across three regions, making it the second largest market but without a unified strategy. Central West
at $9.3K is effectively non-operational. Deluxe Supermarket consistently delivers the highest revenue per store, while 
Small Grocery contributes only 1.9% of total revenue.

### D. Customer Profile

Maven Market serves 10,281 customers with an average age of 54 years. Revenue is evenly distributed across all age groups
and near-equally split by gender confirming broad demographic appeal (peak segment 40-49 years old). However, 90.4% of revenue comes from Standard-priority
customers, revealing a critical loyalty program gap. The top customer generates only $2.2K from 270 orders at $8.15 per
transaction a high-frequency, low-basket profile that reflects a broadly distributed rather than premium-driven
revenue structure.


---

## 8. Conclusions

Maven Market is a profitable and growing business with strong fundamentals 58.3% profit margin, sub-1% return rate, and
110% revenue growth year-over-year. However, three structural challenges require attention to sustain this momentum:

**1. Geographic concentration**
48% of revenue depends on North West alone. Expanding Mexico as a unified market and activating underperforming regions
like Canada West will reduce risk and unlock new growth.

**2. Loyalty program underutilization**
With 90.4% of customers on Standard priority and a top customer averaging only $8.15 per transaction, Maven Market is leaving
premium revenue on the table. A tiered loyalty program targeting frequent buyers for upgrade to Priority or Golden membership
could materially increase average basket size.

**3. Product & store portfolio optimization**
Slow-moving brands at 7 days on shelf, Small Grocery stores contributing only 1.9% of revenue, and Store 5 at $4.9K all
represent drag on overall performance. Discontinuing underperforming products, converting Small Grocery locations
to Deluxe Supermarket format, and addressing the 34.8x store revenue gap would meaningfully improve portfolio efficiency.

---

## 9. Recommendations

### 1) Prioritize Bike Sales to Drive Profitability
Given that Bikes generate 25x more profit than Accessories per
category, an upselling strategy from Accessories to Bikes should
be strengthened. Customers who frequently purchase Accessories
particularly Tires and Tubes and Patch Kits are ideal candidates
to be introduced to entry-level Bikes such as the Mountain-200.

**Action:** Develop **bundle promotions** where the purchase of select
accessories includes a discount on entry-level Bike products to
drive category upgrades.

---

### 2) Localize Strategy by Continent
Differences in product preferences and return rates across continents
indicate that localized marketing and inventory strategies will
deliver better results than a unified global approach:

| Continent | Focus Product | Recommended Action |
|---|---|---|
| Europe | Road Tire Tube, AWC Logo Cap | Strengthen road cycling accessories stock |
| North America | Mountain Tire Tube, Patch Kit | Focus on mountain biking segment |
| Pacific | Road Bottle Cage, Patch Kit | Develop road cycling segment |
| Pacific | Vests (high returns) | Quality review & size guide improvement |

---


**Action:**


---

### Repository Contents
 - Power BI Dashboard File: The main PBIX File containing the analysis and visualizations.
 - Data Sources: [Raw Dataset](raw_data) used in the project.
 - Screenshots/Reports: [Exported visualizations](asset) for sharing insights.
 - README.md: Project documentation (this file)

---

_Source of Dataset: Maven Analytics_
