# Zepto_SQL_Data_Analysis_Project| Real-World SQL Portfolio Project

This is a complete, real-world **Data Analyst Portfolio Project** based on an e-commerce inventory dataset scraped from **Zepto** – one of India’s fastest-growing quick-commerce startups. This project simulates real analyst workflows using SQL, from raw data exploration to deriving business-focused insights.

## 📌 Project Objective
To simulate how data/business analysts in the e-commerce or retail sector use SQL to:

- Set up a **messy, real-world e-commerce inventory database**
- Perform **Exploratory Data Analysis (EDA)** to explore product categories, availability, and pricing inconsistencies
- Apply **Data Cleaning** to handle nulls, remove invalid entries, and standardize pricing
- Write **business-driven SQL queries** to derive insights around pricing, inventory, stock availability, revenue, and more

---

## 🗃️ Dataset Overview

The dataset was originally scraped from Zepto’s product listings and is available on [Kaggle](https://www.kaggle.com). It mimics what analysts face in real e-commerce environments.

Each row represents a **unique SKU (Stock Keeping Unit)**. Duplicate product names exist due to different package sizes, weights, or discounts — similar to real-world catalogs.

**Columns:**
- `sku_id`: Unique identifier (synthetic primary key)
- `name`: Product name
- `category`: Product category (e.g., Fruits, Snacks, Beverages)
- `mrp`: Maximum Retail Price (originally in paise, converted to ₹)
- `discountPercent`: Discount on MRP
- `discountedSellingPrice`: Final selling price (in ₹)
- `availableQuantity`: Inventory units available
- `weightInGms`: Product weight in grams
- `outOfStock`: Boolean flag for stock status
- `quantity`: Package quantity or mixed units (for loose produce)

---

## 🧭 Project Workflow

### 1️⃣ Database & Table Creation
```sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
2️⃣ Data Import
Used pgAdmin's import feature to load the CSV file into PostgreSQL.

3️⃣ 🔍 Data Exploration
Counted total records in the dataset

Viewed sample records to understand structure

Checked for null values across all columns

Identified unique product categories

Compared in-stock vs out-of-stock products

Detected duplicate product names with different SKUs

4️⃣ 🧹 Data Cleaning
Removed rows with MRP = 0 or discountedSellingPrice = 0

Converted mrp and discountedSellingPrice from paise to ₹ for consistency

5️⃣ 📊 Business Insights & Analysis
Top 10 Best Value Products based on highest discount %

High-MRP Products Currently Out of Stock

Estimated Revenue potential per product category

Expensive, Low Discount Products (MRP > ₹500 and discount < 10%)

Top 5 Categories with Highest Average Discount

Price per Gram analysis to find value-for-money products

Weight-Based Grouping:

Low: <250g

Medium: 250g–500g

Bulk: >500g

Total Inventory Weight per product category

📎 Tools Used
PostgreSQL

pgAdmin

SQL (DDL, DML, Aggregations, Joins, CASE, Window Functions)

