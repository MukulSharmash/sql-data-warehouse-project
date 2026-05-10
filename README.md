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

## Architecture

```mermaid
graph LR
    %% Data Source
    Source[Yelp JSON Data]:::source --> |5GB+ / ~7M Rows| PyScript[Python Chunking Script]:::script

    %% Storage Layer
    subgraph DataLake ["Cloud Storage"]
        PyScript --> |Chunked JSON| S3[Amazon S3]:::storage
    end

    %% Warehouse Layers
    subgraph SnowflakeDW ["Snowflake Data Warehouse"]
        S3 --> |COPY INTO| Bronze[(Snowflake Bronze: Raw)]:::db
        Bronze --> |ELT Flattening| Silver[(Snowflake Silver: Cleansed & Sentiment)]:::db
        Silver --> |Dimensional Modeling| Gold[(Snowflake Gold: Star Schema)]:::db
    end

    %% Consumption Layer
    Gold --> |DirectQuery| PBI[Power BI Dashboard]:::viz

    %% --- STYLING (The code below makes it colorful) ---
    classDef source fill:#f9f,stroke:#333,stroke-width:2px;
    classDef script fill:#ff9,stroke:#333,stroke-width:2px;
    classDef storage fill:#f96,stroke:#333,stroke-width:2px,color:white;
    classDef db fill:#69c,stroke:#333,stroke-width:2px,color:white;
    classDef viz fill:#d4af37,stroke:#333,stroke-width:2px,color:black;
