# Market Profitability Dashboard 

This project showcases a Power BI dashboard built using a public dataset from Kaggle to simulate market profitability analysis across regions and product categories. It features advanced DAX metrics, SQL-based data cleaning, and interactive visuals for margin and pricing insights.

<sub>This dashboard was created using sample data from Kaggle to represent a real-world business case.</sub>

---
## Problem Statement

- The company needed a clear way to evaluate profit margins and pricing efficiency across different regions and product segments.  
- Existing static reports lacked visibility into Gross Margin %, AUR (Average Unit Retail), and AUC (Average Unit Cost).  
- Business users struggled to identify low-performing areas and compare category-level trends over time.

---

## Tools Used
- **Power BI**
- **SQL** (Joins, Cleaning)
- **DAX** (`CALCULATE()`, `TREATAS()`, Conditional Formatting)
- **Data Modeling** (Calendar Table, Relationships)

---





## 🔄 Process Overview

### 1. **Data Source**
- Used a Kaggle dataset representing transactional sales data, pricing, and cost information.

### 2. **Data Preparation (SQL)**
- Removed missing and inconsistent records.
- Performed joins between sales, region, and product datasets.

-- Remove records with missing Sales or Cost values -
`SELECT *
FROM sales_data
WHERE Sales IS NOT NULL AND Cost IS NOT NULL;`

-- Join Sales data with Region and Product tables-
`SELECT 
    s.Sale_ID,
    s.Date,
    s.Region_ID,
    r.Region_Name,
    s.Product_ID,
    p.Product_Name,
    s.Units_Sold,
    s.Sales,
    s.Cost
FROM sales_data s
JOIN region_data r ON s.Region_ID = r.Region_ID
JOIN product_data p ON s.Product_ID = p.Product_ID;`


### 3. **Data Modeling**
- Created a star schema with a fact table and related dimension tables.  
- Built a custom calendar table to support dynamic time filtering in Power BI.

### 4. **DAX Calculations**
- Key metrics included:
  - `GM%` = (Sales – Cost) / Sales  
  - `AUR` = Sales / Units  
  - `AUC` = Cost / Units  
  - `PPP` = Units Sold / Units Available  
- Used `TREATAS()` and `CALCULATE()` to apply time-based and slicer filters dynamically.

### 5. **Dashboard Features**
- Map visualization showing regional GM%  
- Matrix with conditional formatting by category  
- KPI cards for Sales, Profit, AUR, AUC  
- Slicers for Year, Region, and Product Category  
- Trend charts and drill-down capabilities

---

## Solution

- Built an interactive Power BI dashboard using a Kaggle dataset to simulate sales, cost, and pricing scenarios.  
- Cleaned and joined multi-source data using SQL for accuracy.  
- Created a star schema data model and implemented a calendar table for time-based analysis.  
- Developed DAX measures like GM%, AUR, AUC, and Price Penetration % using `CALCULATE()` and `TREATAS()`.  
- Applied conditional formatting to matrix tables to easily highlight performance trends.  
- Enabled filtering by year, region, and product group for focused insights.

---



