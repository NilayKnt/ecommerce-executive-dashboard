# 🛒 E-Commerce Executive Sales Analytics Dashboard (Power BI)

## 📌 Executive Summary
This project presents an end-to-end Business Intelligence (BI) solution designed to evaluate sales performance, customer purchasing behavior, and inventory trends for an online retail business. 

Starting from a raw, unorganized e-commerce transaction dataset, the data was thoroughly transformed using **Power Query**, structured into a robust **Star Schema** dimensional model, and visualized through an interactive **Power BI** dashboard powered by advanced **DAX** calculations and **Natural Language Querying (Q&A)** capabilities.

---

## 📊 Interactive Dashboard Overview

<img width="1563" height="805" alt="Ekran Resmi 2026-10-05 23 07 53" src="https://github.com/user-attachments/assets/9160e1a4-f0cc-4e82-ba9d-afc3e565bd13" />


---

## 🏗️ Data Architecture & Star Schema Modeling
To eliminate redundant attributes, optimize analytical performance, and enable accurate time-intelligence analysis, the transactional flat file was normalized into a classic **Star Schema** architecture:

```text
    [DimCustomer] (1) ─── (*) [FactSales] (*) ─── (1) [DimProduct]
                                   │
                                   │ (*)
                                   │
                                  (1)
                               [DimDate]
FactSales (Fact Table): Contains granular transactional records including Quantity, UnitPrice, InvoiceNo, and foreign keys referencing dimension tables.
DimProduct (Dimension Table): Stores unique product identifier records (StockCode) cleansed of hidden spaces and case anomalies.
DimCustomer (Dimension Table): Contains unique CustomerID entries and geographic attributes (Country), filtered for valid customer identifiers.
DimDate (Dimension Table): A dedicated calendar table engineered to support seamless date aggregations and trend analysis.

📐 Key DAX Measures
Core KPI calculations were organized within a dedicated _Measures table to power dashboard visuals:
Kod snippet'i
// Total Revenue Calculation
Total Revenue = SUMX( FactSales, FactSales[Quantity] * FactSales[UnitPrice] )

// Unique Order Count
Total Orders = DISTINCTCOUNT( FactSales[InvoiceNo] )

// Active Unique Customer Count
Total Customers = DISTINCTCOUNT( FactSales[CustomerID] )

💡 Key Business Insights
Revenue Concentration: A significant portion of total revenue is driven by the Top 10 performing stock items, indicating critical inventory management priorities.
Geographic Distribution: The domestic market (United Kingdom) holds the primary market share, while key European markets show distinct demand patterns.
Self-Service & Q&A Integration: Integrated natural language Q&A interface allowing stakeholders to query ad-hoc metrics dynamically on demand.

🛠️ Tech Stack & Methods
Power BI Service / Desktop — Dashboard UI & Interactive Data Visualization
Power Query (ETL) — Data Cleaning, Text Standardization (Trim/Uppercase), & Deduplication
DAX (Data Analysis Expressions) — Dimensional Modeling & Aggregation Measures
Star Schema Architecture — Relational Data Modeling (1:∗ Cardinality)

