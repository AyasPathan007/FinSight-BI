# FinSight BI - Data Dictionary

## Overview

This document defines the data model for FinSight BI. It describes each table, its purpose, and the columns used for analytics and reporting.

---

# Dimension Tables

## dim_date

| Column | Data Type | Description |
|---------|-----------|-------------|
| date_id | INT | Primary key in YYYYMMDD format |
| full_date | DATE | Calendar date |
| day | INT | Day of month |
| month | INT | Month number |
| month_name | VARCHAR(20) | Month name |
| quarter | VARCHAR(5) | Quarter |
| year | INT | Calendar year |

---

## dim_store

| Column | Data Type | Description |
|---------|-----------|-------------|
| store_id | INT | Unique store identifier |
| store_name | VARCHAR(100) | Store name |
| city | VARCHAR(100) | City |
| state | VARCHAR(100) | State |
| region | VARCHAR(50) | Business region |
| opening_date | DATE | Store opening date |

---

## dim_product

| Column | Data Type | Description |
|---------|-----------|-------------|
| product_id | INT | Product identifier |
| product_name | VARCHAR(150) | Product name |
| category | VARCHAR(100) | Product category |
| sub_category | VARCHAR(100) | Product subcategory |
| brand | VARCHAR(100) | Brand |
| unit_price | DECIMAL(10,2) | Selling price |
| cost_price | DECIMAL(10,2) | Purchase cost |

---

## dim_customer

| Column | Data Type | Description |
|---------|-----------|-------------|
| customer_id | INT | Customer identifier |
| first_name | VARCHAR(50) | First name |
| last_name | VARCHAR(50) | Last name |
| gender | VARCHAR(10) | Gender |
| age | INT | Customer age |
| city | VARCHAR(100) | City |
| state | VARCHAR(100) | State |
| membership_type | VARCHAR(50) | Loyalty tier |

---

# Fact Tables

## fact_sales

| Column | Data Type | Description |
|---------|-----------|-------------|
| sales_id | BIGINT | Sales transaction ID |
| date_id | INT | Date key |
| store_id | INT | Store key |
| product_id | INT | Product key |
| customer_id | INT | Customer key |
| quantity | INT | Quantity sold |
| sales_amount | DECIMAL(12,2) | Sales amount |
| discount | DECIMAL(10,2) | Discount |
| cost_amount | DECIMAL(12,2) | Product cost |
| profit | DECIMAL(12,2) | Profit |
| payment_method | VARCHAR(30) | Payment type |

---

## fact_inventory

| Column | Data Type | Description |
|---------|-----------|-------------|
| inventory_id | BIGINT | Inventory record ID |
| product_id | INT | Product key |
| store_id | INT | Store key |
| stock_quantity | INT | Available stock |
| reorder_level | INT | Minimum stock threshold |
| last_updated | DATE | Last inventory update |

---

## fact_returns

| Column | Data Type | Description |
|---------|-----------|-------------|
| return_id | BIGINT | Return transaction ID |
| sales_id | BIGINT | Original sales transaction |
| return_date | DATE | Return date |
| return_reason | VARCHAR(100) | Reason for return |
| refund_amount | DECIMAL(12,2) | Refund issued |

---

## Relationships

- fact_sales → dim_date
- fact_sales → dim_store
- fact_sales → dim_product
- fact_sales → dim_customer
- fact_inventory → dim_product
- fact_inventory → dim_store
- fact_returns → fact_sales
