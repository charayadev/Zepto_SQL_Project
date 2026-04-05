# Zepto SQL Data Analysis Project

A complete SQL project built on Zepto's grocery product dataset.
Covers database creation, data cleaning, and 8 business analysis queries
to extract pricing, discount, stock, and revenue insights.

---

## 📊 Project Overview

| Phase | What Was Done |
|---|---|
| Database Setup | Created table, imported CSV data |
| Data Exploration | Null checks, category discovery, stock overview |
| Data Cleaning | Removed zero-price products, converted paise to rupees |
| Data Analysis | 8 business questions answered using SQL |

---

## 🗄️ Table Structure
```sql
CREATE TABLE zepto (
    sku_id                 SERIAL PRIMARY KEY,
    category               VARCHAR(120),
    name                   VARCHAR(150) NOT NULL,
    mrp                    NUMERIC(8,2),
    discountPercent        NUMERIC(5,2),
    availableQuantity      INTEGER,
    discountedSellingPrice NUMERIC(8,2),
    weightInGms            INTEGER,
    outOfStock             BOOLEAN,
    quantity               INTEGER
);
```

---

## 🧹 Data Cleaning Steps

- Checked all columns for NULL values
- Removed products where `mrp = 0` (invalid records)
- Converted prices from **paise to rupees** by dividing by 100
- Identified duplicate product names across SKUs

---

## ❓ Business Questions Answered

**Q1. Top 10 best-value products by discount percentage**
> Which products give customers the highest discount?

**Q2. High MRP products that are out of stock**
> Premium products (MRP > ₹250) currently unavailable — restocking priority list.

**Q3. Estimated revenue per category**
> `discountedSellingPrice × availableQuantity` grouped by category.

**Q4. Products with MRP > ₹500 but discount < 10%**
> Expensive products with low discounts — pricing strategy review candidates.

**Q5. Top 5 categories by average discount percentage**
> Which categories are most aggressively discounted?

**Q6. Price per gram for products above 100g**
> Best value-for-weight products sorted for cost-conscious buyers.

**Q7. Products grouped by weight category**
> Classified as Low (< 1000g), Medium (< 5000g), or Bulk (5000g+).

**Q8. Total inventory weight per category**
> `availableQuantity × weightInGms` — identifies heaviest stocked categories.

---

## 💡 Key Insights

- **Prices were stored in paise** — cleaning step critical before any analysis
- **Out-of-stock premium products** identified for urgent restocking
- **Category-level revenue** shows which segments contribute most
- **Price-per-gram metric** built using CTE for clean, reusable logic
- **Weight segmentation** enables logistics and packaging planning

---

## 🛠️ Tools Used

- PostgreSQL
- pgAdmin 4
- SQL — DDL, DML, Aggregations, CTEs, CASE WHEN, Window logic

---


## ▶️ How to Run

1. Open **pgAdmin** or any PostgreSQL client
2. Run `zepto_create_import.sql` to create the table and load data
3. Run `zepto_cleaning.sql` to clean the data
4. Run `zepto_analysis.sql` to execute all 8 business queries
5. Each query is commented with the business question it answers

---

## 👤 Author

**Dev Charaya**
Data Analyst Learner | SQL • Excel • Python
[charayadev](https://github.com/charayadev)
