# Pharma-Sales-Data

# 💊 Pharmaceutical Portfolio & Commercial Performance Analytics | Power BI

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge)
![Data Modeling](https://img.shields.io/badge/Data_Modeling-Star_Schema-green?style=for-the-badge)

## 📌 Executive Summary
This repository contains an end-to-end **Power BI Advanced Business Intelligence** solution tailored for the pharmaceutical and life sciences sector. The interactive report addresses commercial operations, portfolio strategy, and financial performance by tracking key metrics across drug lines, therapeutic areas, sales channels, and geographical territories.

The solution transforms complex transactional data into executive-ready visual insights, empowering brand managers, finance leadership, and commercial directors to optimize pricing, identify high-margin indications, and accelerate portfolio growth.

---

## 📊 Key Report Features & Architecture

The Power BI report is structured into three dedicated interactive views:

1. **Executive C-Suite Overview:** High-level executive dashboard delivering core KPI cards, target vs. actual revenue trends, year-over-year (YoY) variance, and high-level market breakdown by Rx/OTC classification.
2. **Product & Portfolio Deep-Dive:** Strategic portfolio matrix evaluating volume vs. profitability (Scatter Plot analysis), margin heatmap by indication, and root-cause revenue expansion using Power BI's **Decomposition Tree**.
3. **Geographic & Channel Analytics:** Spatial visualization of international markets, performance across sales distribution channels (Direct Hospital, Wholesale, Retail Pharmacy), and specialty physician targeting.

---

## 🏗️ Data Architecture & Modeling

The project employs a robust **Star Schema** architecture to ensure optimal DAX evaluation speed, scalability, and seamless time-intelligence filtering.

### Data Model Layout
* **Fact Table:** `Fact_Sales` (Granular transaction-level revenue, unit sales, discounts, and manufacturing costs)
* **Dimension Tables:**
  * `Dim_Product` (Drug ID, Drug Name, Therapeutic Area, Category, Rx/OTC Type)
  * `Dim_Geography` (Country, Global Region)
  * `Dim_Customer` (Customer Account, Distribution Channel, Specialty)
  * `Dim_Date` (DAX-generated calendar table supporting multi-year reporting)

---

## 📐 DAX Implementation Highlights

The report utilizes custom **Data Analysis Expressions (DAX)** ranging from base aggregations to complex time-intelligence metrics:

### 1. Business Logic Columns & Base Measures
* **Net Revenue:** `Fact_Sales[Gross_Revenue] * (1 - Fact_Sales[Discount_Pct])`
* **Gross Margin %:** `DIVIDE([Total Gross Margin], [Total Net Revenue], 0)`
* **Average Selling Price (ASP):** `DIVIDE([Total Net Revenue], [Total Units Sold], 0)`

### 2. Time Intelligence & Performance Metrics
* **Prior Year Revenue:** `CALCULATE([Total Net Revenue], SAMEPERIODLASTYEAR(Dim_Date[Date]))`
* **YoY Revenue Growth %:** `DIVIDE([Total Net Revenue] - [PY Net Revenue], [PY Net Revenue], 0)`
* **Rolling 3-Month Moving Average:** `CALCULATE([Total Net Revenue], DATESINPERIOD(Dim_Date[Date], MAX(Dim_Date[Date]), -3, MONTH))`
* **YTD Net Revenue:** `TOTALYTD([Total Net Revenue], Dim_Date[Date])`

◉ Screenshot/Demo: 
Show what the Dashboard looks like: [Alt text](https://github.com/LoneWolfBarman)
Example: [Dashboard Preview](Pharma_Sales_Data.jpg)
