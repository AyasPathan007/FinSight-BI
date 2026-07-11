# FinSight BI - System Architecture

## Overview

FinSight BI is a Business Intelligence platform designed for retail organizations. It consolidates transactional, customer, product, and financial data into a centralized analytics environment that supports executive reporting and operational decision-making.

---

## Architecture

Raw Data Sources
        │
        ▼
 PostgreSQL Database
        │
        ▼
 SQL Views & Business Logic
        │
        ▼
 Power BI Semantic Model
        │
        ▼
 Interactive Dashboards
        │
        ▼
 Business Users

---

## Technology Stack

| Layer | Technology |
|--------|------------|
| Database | PostgreSQL |
| Query Language | SQL |
| Data Modeling | Star Schema |
| Visualization | Power BI |
| Version Control | Git & GitHub |

---

## Data Flow

1. Business transactions are stored in PostgreSQL.
2. SQL queries transform raw data into analytical datasets.
3. Power BI imports the transformed data.
4. DAX measures calculate KPIs.
5. Dashboards provide business insights to stakeholders.
