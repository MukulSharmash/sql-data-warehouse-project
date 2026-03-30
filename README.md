# Sales & Customer Analytics Data Warehouse

This project is focused on building a SQL-based data warehouse for sales and customer analytics.

The idea behind this project was to take raw business data from different source-style files, clean and standardize it step by step, and then convert it into a final model that can be used for reporting and analysis.

I used a layered warehouse approach with Bronze, Silver, and Gold schemas so the data stays organized and each stage of transformation is easier to understand and manage.

---

## Project Objective

The main goal of this project was to practice how raw operational data can be transformed into analytics-ready data.

This warehouse can be used to answer business questions like:

- Which products are generating the most revenue?
- Which customers are contributing the most sales?
- How are sales changing over time?
- Which product categories are performing better or worse?
- How can raw source data be prepared for reporting use?

---

## Architecture Used

This project follows a 3-layer warehouse design:

- **Bronze Layer** → stores raw data exactly as received from source files
- **Silver Layer** → stores cleaned and standardized data
- **Gold Layer** → stores final analytics-ready tables for reporting and business analysis

This structure helped me separate raw ingestion, cleaning logic, and final reporting logic in a more organized way.

---

## Tools / Technologies

- SQL Server
- SQL Server Management Studio (SSMS)
- CSV files as source data
- Git & GitHub

---

## Data Flow

The project flow is divided into 3 main stages:

1. Raw CRM and ERP-style data is loaded into the **Bronze** layer
2. Data is cleaned and standardized in the **Silver** layer
3. Final fact and dimension tables are created in the **Gold** layer for analytics and reporting

---

## Project Structure

datasets/         --> raw source files  
scripts/bronze/   --> raw data loading scripts  
scripts/silver/   --> cleaning and transformation scripts  
scripts/gold/     --> final analytical model scripts  
tests/            --> data quality and validation queries  

- More validation checks
- Power BI dashboard on top of the Gold layer
- Performance optimization for larger datasets
