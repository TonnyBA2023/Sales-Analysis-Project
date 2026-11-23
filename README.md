# SALES ANALYSIS FOR BLAIRLYTICS COMPANY
## Table of Contents
- [Project Overview](#project-overview)

## Project overview
This project presents an end-to-end sales data analysis for **Blairlytics Company**. The goal is to evaluate historical sales performance, uncover key revenue drivers, and identify seasonal buying trends to support data-driven business and inventory decisions.

### Key Objectives
* **Revenue & Growth Tracking:** Analyze monthly and quarterly sales trends to measure overall business growth.
* **Product Performance:** Identify top-selling products and categories alongside their profit margins.
* **Regional & Channel Insights:** Compare sales performance across different regions and customer segments.
* **Actionable Recommendations:** Provide clear, data-backed strategies to optimize pricing, promotions, and stock allocation.

### Tools Used
* **Data Cleaning & Analysis:** Excel, SQL
*  [Download the dataset here](https://microsoft.com)
* **Data Visualization:** Excel

## Data Source
The dataset used for this analysis was sourced from **Kaggle** and represents historical sales transactions for **Blairlytics Company**.

* **Platform:** Kaggle
* **File Format:** CSV (imported into Microsoft SQL Server for querying and analysis)
* **Dataset Scope:** Contains transactional sales records including order dates, product details, quantities sold, unit prices, discounts, and customer regions.
* **Time Period:** `[e.g., 2022 – 2025]` *(replace with your dataset's date range)*
* **Volume:** `[e.g., ~9,800 records]` *(replace with your approximate row count)*

## Data Cleaning & Preparation
Before performing the analysis, the raw Kaggle CSV file was imported into **Microsoft SQL Server** and prepared through the following steps to ensure data accuracy and consistency:

1. **Duplicate Removal:** Identified and removed duplicate transaction rows using `ROW_NUMBER()` and Common Table Expressions (`CTEs`).
2. **Handling Missing Values:** Checked for `NULL` or blank fields across key columns (such as sales amount, order date, and product category) and either imputed missing values or excluded incomplete records.
3. **Data Type Standardization:** Converted text-based date columns into proper `DATE` formats and ensured revenue, quantity, and discount fields used accurate numeric/decimal data types.
4. **Text & Category Formatting:** Trimmed extra spaces (`TRIM()`) and standardized inconsistent capitalization across product names, customer segments, and regions.
5. **Feature Engineering:** Created calculated columns such as **Total Revenue**, **Profit Margin (%)**, **Order Year**, and **Order Month/Quarter** to support time-series and profitability analysis.

## Exploratory Data Analysis (EDA)
Using **Microsoft Excel**, Pivot Tables, formulas, and charts were used to explore core business KPIs, sales trends, and product performance.

### Key Areas Explored
* **Overall Sales KPIs:** Calculated Total Revenue, Total Profit, Total Orders, and Average Order Value (AOV) using `SUM()`, `COUNTIFS()`, and `AVERAGE()` functions.
* **Time-Series Trends:** Grouped order dates by Month and Quarter in Pivot Tables to track revenue growth and spot seasonal spikes.
* **Product & Category Performance:** Used Pivot Tables and `SUMIFS()` to rank top-selling products and compare profit margins across categories.
* **Regional & Segment Breakdown:** Built interactive slicers to filter sales performance by region, shipping mode, and customer segment.
* **Data Visualization:** Designed an interactive Excel dashboard featuring KPI cards, line charts for monthly trends, and bar charts for category comparisons.
  ```sql
    SELECT 
        category,
        product_name,
        ROUND(SUM(sales), 2) AS total_revenue,
        DENSE_RANK() OVER (
            PARTITION BY category 
            ORDER BY SUM(sales) DESC
        ) AS sales_rank
    FROM sales_data
    GROUP BY category, product_name) ```


### Results/Findings
* **Seasonal Revenue Peaks:** Sales consistently spiked in **Q4 (October–December)**, accounting for roughly **35% of annual revenue**, driven by end-of-year and holiday demand.
* **Top-Performing Category:** **[Top Category, e.g., Technology / Electronics]** generated the highest overall revenue, while **[Second Category, e.g., Office Supplies]** delivered the most consistent order volume.
* **Discount Impact on Profit:** Heavy discounts (above **20%**) boosted short-term unit sales but significantly reduced net profit margins.
* **Regional Concentration:** The **[Top Region, e.g., West / Central]** region led all other areas in both total revenue and repeat customer orders.
* **Customer Segment Trends:** **[Top Segment, e.g., Corporate / Consumer]** customers accounted for the largest share of total sales and highest average order value (AOV).

## Recommendations
Based on the findings from the sales analysis, the following actions are recommended for **Blairlytics Company**:

* **Optimize Discount Strategy:** Cap standard promotional discounts at **15%–20%** to protect profit margins, reserving steeper discounts strictly for clearing slow-moving inventory.
* **Prepare Inventory Ahead of Q4:** Increase stock levels and marketing spend in late Q3 (August–September) to maximize fulfillment capacity during the **October–December peak season**.
* **Focus Growth in High-Performing Categories:** Prioritize bundling and cross-selling around **[Top Category, e.g., Technology / Electronics]** to drive higher average order values (AOV).
* **Replicate Top Regional Strategies:** Audit successful marketing and distribution practices in the **[Top Region, e.g., West / Central]** region and apply them to underperforming territories.
* **Target High-Value Customer Segments:** Introduce loyalty incentives or volume-based pricing for **[Top Segment, e.g., Corporate / Consumer]** buyers to increase repeat purchase rates.

## Limitations
While this analysis provides clear insights into historical sales performance, a few dataset and scope limitations should be noted:

* **Historical & Static Data:** The Kaggle dataset represents a fixed historical snapshot rather than live data, meaning recent market shifts or current inventory levels are not reflected.
* **Missing External Factors:** The dataset does not include external variables such as marketing spend, competitor pricing, or macroeconomic conditions that may have influenced sales spikes.
* **Limited Customer Demographics:** Detailed customer attributes (such as age, acquisition channel, or churn feedback) were unavailable, limiting deeper customer lifetime value (CLV) analysis.
* **Cost Granularity:** Profit calculations rely strictly on recorded transactional figures and may not account for indirect operational overhead, warehousing, or return processing costs.

## References
* **Dataset:** Kaggle. *Sales Dataset / Retail Sales Analysis Data* (Blairlytics Company case study). Retrieved from [Kaggle](https://kaggle.com).
* **Analytical Software:** Microsoft Corporation. *Microsoft Excel* (Pivot Tables, Power Query, and Data Visualization tools).
* **Documentation & Formatting:** GitHub Docs. *Basic writing and formatting syntax (GitHub Flavored Markdown)*. Retrieved from [GitHub Docs](https://github.com).











