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
