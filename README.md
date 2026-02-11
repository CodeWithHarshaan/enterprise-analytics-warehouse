# Enterprise Analytics Warehouse (Extended dbt Implementation)

## Overview

This project is an extended implementation of the open-source dbt "jaffle_shop" demo project. I enhanced the base structure to simulate an enterprise-style analytics warehouse using SQL and dbt.

The objective of this project is to demonstrate modern analytics engineering practices including data modeling, incremental batch processing, data governance, and KPI-driven reporting.

---

## Architecture

The project follows a layered data modeling approach:

- **Raw Layer (Seeds)** – Simulated transactional source data (customers, orders, payments)
- **Staging Layer** – Standardization, column renaming, data type correction, and validation
- **Marts Layer** – Fact and dimension models for analytics-ready reporting
- **KPI Layer** – Aggregated business metrics for operational and financial tracking

An ERD is included to illustrate table relationships and grain definition.

---

## Enhancements Beyond Base jaffle_shop

The original open-source project was extended with the following improvements:

- Implemented **incremental materialization** for scalable batch processing
- Built a **monthly KPI aggregation model** for revenue and operational tracking
- Added enterprise-style **data validation tests** (not_null, unique, relationships, accepted values)
- Designed and included an **ERD definition**
- Structured models into staging and marts layers to reflect production data architecture
- Implemented dynamic SQL generation using Jinja templating

---

## Data Modeling

### Fact Model
- `orders` (order-level grain)
  - Payment method breakdown
  - Total revenue calculation
  - Incremental processing enabled

### Dimension Model
- `customers`
  - First order date
  - Most recent order
  - Number of orders
  - Customer lifetime value

### KPI Model
- `kpi_monthly_metrics`
  - Monthly revenue
  - Average order value
  - Active customers
  - Revenue per customer

---

## Data Governance

The project includes automated validation tests:

- Primary key uniqueness
- Not null constraints
- Referential integrity between fact and dimension tables
- Accepted values validation for order status and payment methods

---

## Scalability Considerations

In a production environment, this pipeline would be:

- Orchestrated using tools like Apache Airflow
- Deployed on scalable infrastructure (e.g., EMR or EKS)
- Executed using distributed compute frameworks such as Spark for large datasets

---

## Technologies Used

- dbt
- SQL
- Jinja templating
- Dimensional data modeling
- Data validation & testing

---
