# ☕ Monday Coffee – Market Expansion Analysis with SQL

A SQL-driven market research project to identify the best Indian cities for **Monday Coffee** — an online coffee retailer — to open its first physical stores, based on consumer demand, sales performance, and cost-to-revenue ratios.

![SQL](https://img.shields.io/badge/SQL-MS%20SQL%20Server-orange)
![Data Analysis](https://img.shields.io/badge/Domain-Market%20Expansion-brown)

---

## 📌 Project Overview

Monday Coffee has sold its products online across India since January 2023 but has never operated a physical store. This project analyzes 10,388 sales records to answer: **which three cities should Monday Coffee enter first?**

The analysis combines population-based demand estimates, real sales performance, and commercial rent data to rank cities not just by revenue, but by revenue *relative to cost* — producing a data-backed shortlist of expansion targets.

---

## 🗂️ Dataset

A relational dataset spanning 4 tables:

| Table | Rows | Description |
|---|---|---|
| `city` | 14 | City name, population, estimated commercial rent, city rank |
| `customers` | 497 | Customer name linked to their city |
| `products` | 28 | Coffee products and prices (beans, brews, merchandise, subscriptions) |
| `sales` | 10,388 | Transaction-level sales: date, product, customer, total, rating |

**Relationships:** `sales` → `customers` (via `customer_id`) → `city` (via `city_id`); `sales` → `products` (via `product_id`).

---

## 🔧 Analysis Approach (SQL)

All analysis was performed in **MS SQL Server** using joins, CTEs, window functions, and date functions. 10 business questions were answered:

1. **Coffee Consumer Estimate** — Estimated coffee drinkers per city (25% of population)
2. **Q4 2023 Revenue by City** — Total revenue generated in the last quarter of 2023
3. **Product Sales Volume** — Units sold per product across the catalog
4. **Average Sales per City** — Revenue and customer count per city
5. **Demand vs. Customer Base** — Estimated consumers vs. actual unique customers per city
6. **Top 3 Products by City** — Best-selling products per city using `DENSE_RANK()`
7. **Customer Segmentation** — Unique customers transacting per city
8. **Sales vs. Rent Ratio** — Average sale per customer vs. average rent burden per customer
9. **Monthly Sales Growth** — Month-over-month % growth using `LAG()` window function
10. **Market Potential Ranking** — Composite view of revenue, rent, customer base, and demand to surface the top 3 expansion cities

---

## 📊 Key Findings

- **Pune leads on every metric that matters:** highest total revenue (₹12.58L), highest average sale per customer (₹24,198), and the *lowest* average rent per customer (₹294) — the strongest revenue-to-cost ratio in the dataset.
- **Delhi has the largest addressable market:** an estimated 7.7 million coffee consumers (by far the highest), the largest customer base (68 customers), and rent per customer (₹330) still comfortably under the ₹500 threshold.
- **Jaipur combines scale with affordability:** the highest customer count (69), very low rent per customer (₹156), and strong average sales per customer (₹11.6K) — making it a low-risk, high-upside market.
- **High-rent cities don't always pay off:** Mumbai and Hyderabad carry some of the highest rent-per-customer figures (₹1,166 and ₹1,071 respectively) despite mid-tier revenue — a warning sign against expanding there first.
- **Cold Brew and Espresso dominate the catalog:** Cold Brew Coffee Pack (1,326 units) and Ground Espresso Coffee (1,271 units) are the top two sellers nationally, but product preference varies by city.

---

## 💡 Recommendation: Top 3 Cities for Expansion

| Rank | City | Why |
|---|---|---|
| 1 | **Pune** | Highest revenue, high sales-per-customer, lowest rent burden |
| 2 | **Delhi** | Largest estimated consumer base (7.7M), most customers, rent still within budget |
| 3 | **Jaipur** | Largest customer count, very low rent per customer, strong average spend |

These three cities offer the best balance of **proven demand, existing customer traction, and manageable real-estate cost** — minimizing risk for Monday Coffee's first physical locations.

---

## 🛠️ Tech Stack

| Component | Tool |
|---|---|
| Database & Querying | MS SQL Server (T-SQL) |
| Techniques used | JOINs, CTEs, Window Functions (`DENSE_RANK`, `LAG`), Date functions, Aggregations |

---

## 📁 Repository Contents

```
├── city.csv                              # City population, rent, and rank data
├── customers.csv                         # Customer-to-city mapping
├── products.csv                          # Product catalog with pricing
├── sales.csv                             # 10,388 transaction records
├── Monday_Coffiee_Analysis.sql           # Full SQL analysis (10 business questions)
├── Monday_Coffee_Expansion_With_SQL.pdf  # Full write-up with query outputs
└── README.md                             # Project documentation
```

---

## 🚀 How to Explore This Project

1. Load `city.csv`, `customers.csv`, `products.csv`, and `sales.csv` into a SQL Server database (or any RDBMS with minor syntax tweaks).
2. Run `Monday_Coffiee_Analysis.sql` to reproduce all 10 analyses end-to-end.
3. Refer to the PDF report for the full set of query outputs and the final expansion recommendation.

---

## 🙋 About

This project demonstrates SQL-first market analysis — turning raw transactional and demographic data into a clear, defensible business recommendation using joins, CTEs, and window functions.

Feel free to connect if you'd like to discuss the query logic or the city-ranking methodology.
