# AdventureWorksCompany-PowerBI-Dashboard 

![](image.jpg)


## Introduction
This time I'll be working with data from Maven Market, a multi-national grocery chain with locations in Canada, Mexico and the United States.

I worked through the entire business intelligence workflow: connecting and shaping the data, building a relational model, adding calculated fields, and designing an interactive report.


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

**Challenge Key Questions to Explore**

1. How do total revenue, profit, and order volume trend over time across the 2020–2022 period?

---

## 2. **Skills Demonstrated**
- **Data Transformation**  
- **Data Modeling** — star schema design with fact and dimension tables
- **Data Visualization** — KPI cards, gauge charts, line charts, donut charts, and matrix tables
- **Data Analysis** — discover actionable insights, support critical decision-making, and validate hypotheses

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

Maven Market recorded 1,560 total orders generating $1.8M in total revenue and $1.05M in total profit representing an impressive profit margin of 58.3% at the overall business level. The return rate of 0.99% confirms strong product quality consistency across the entire catalog.
The overall profit of $1.05M on $1.8M revenue means Maven Market retains $0.58 of every $1.00 sold an exceptionally healthy profitability ratio for a grocery retail operation.
The return rate of 0.99% is below 1% a strong quality indicator suggesting that less than 1 in 100 items purchased is returned across the entire business

---

### B. Product Performance

**Revenue & Brand**
Maven Market generated $1.8M in total revenue across 1,560 orders
with Hermanos leading at $56.7K, followed closely by Tell Tale
($51.6K) and Ebony ($49.7K). The top 10 brands cluster tightly
between $40K–$57K, indicating a competitive mid-tier with no
single dominant outlier.

**Profitability**
The business maintains a strong average margin of 59.67% with a
healthy return rate of 0.99% both well within acceptable ranges.
Brand positioning analysis reveals that the majority of high revenue
brands also sit above the margin threshold, confirming that volume
and profitability are largely aligned for the top performers.

**Inventory**
Products sell at an average of 4 days on shelf. However, a cluster
of brands averages 7 days 75% slower than the portfolio average
indicating slow movers that require promotion intervention or
discontinuation review.

**Sustainability & Health**
64.62% of products are low fat, reflecting a health-conscious
assortment. However, 55.96% of products are non-recyclable
a sustainability gap that may become a competitive disadvantage
as consumer preferences shift toward eco-friendly options.

**Returns**
The top 3 returned products Hermanos Red Pepper (2.83%),
Shady Lake Spaghetti (2.93%), and Walrus Merlot Wine (2.79%)
all exceed the portfolio average by nearly 3x, signaling product
specific quality or expectation issues requiring immediate review.

---

### C. Customer & Store Detail

**Customer Base**
Maven Market serves 10,281 unique customers with an average age
of 54 years. Revenue is well-distributed across all age groups,
with the 40–49 segment peaking at $271.6K and the 80–89 segment
still contributing $242.2K confirming strong cross-generational
appeal with only a 10.8% decline from peak to oldest bracket.

**Gender & Priority**
Revenue is near-equally split between female ($891.7K) and male
($872.8K) customers a healthy diversification. However, 90.4%
of revenue comes from Standard-priority customers, indicating that
Maven Market's loyalty program has not yet successfully converted
its mass customer base into higher-value priority members.

**Top Customer**
Mr. Ida Rodriguez (age 57, Skilled Manual) is the top revenue
customer at $2.2K from 270 orders averaging only $8.15 per
transaction. This high-frequency, low-basket pattern suggests
Maven Market lacks high-ticket individual buyers, with revenue
broadly distributed rather than concentrated in VIP customers.

**Education & Occupation**
Customers with lower formal education (Partial High School:
$533.2K, High School Degree: $521.7K) drive the most revenue,
reflecting Maven Market's working-class community positioning.
On the occupation side, Professional customers dominate at $574.0K
(31.9% of total), while Clerical at $30.6K is significantly
underrepresented pointing to either a pricing or accessibility
gap for this segment.

**Store Performance**
Of 24 stores, 13 exceed the average revenue of $73,522.8 while
11 fall below it with Store 5 severely underperforming at $4.9K.
The 34.8x revenue gap between the highest store ($170.3K) and
lowest store ($4.9K) indicates structural performance variance
that requires standardization. Deluxe Supermarket format
consistently outperforms all other store types, generating the
highest revenue per sqft making it the highest-priority format
for future expansion.

---

## 8. Conclusions

Maven Market demonstrated solid business performance across
1997–1998, generating $1.8M in revenue at a 59.67% average
margin and a near-zero return rate of 0.99%. The top brand
Hermanos leads at $56.7K with a tightly competitive mid tier
group, though a cluster of slow-moving brands at 7 days on
shelf signals inventory efficiency gaps. The customer base of
10,281 is well-diversified across age, gender, and occupation,
with the Professional segment driving 31.9% of revenue and the
40–49 age group peaking at $271.6K. However, 90.4% Standard
priority dominance reveals an underdeveloped loyalty program,
and the top customer generating only $2.2K highlights a broadly
distributed rather than VIP-concentrated revenue structure.
Store performance varies dramatically with a 34.8x gap between
the best and worst locations, and the Deluxe Supermarket format
consistently delivers the highest revenue per sqft pointing
to a clear expansion priority for future growth.

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
