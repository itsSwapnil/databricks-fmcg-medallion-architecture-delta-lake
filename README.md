# databricks-fmcg-medallion-architecture-delta-lake
End-to-end FMCG data engineering project on Databricks using Medallion Architecture and Delta Lake. Ingests CSV data from Volumes/S3, processes Bronze–Silver–Gold layers with PySpark, supports incremental loads, Delta MERGE operations, and SCD Type 2 to deliver secure, analytics-ready datasets for business reporting.

---
## Problem statement

Design a unified Lakehouse ETL pipeline in the FMCG domain to process historical and incremental data for a child company, align it with an existing parent company pipeline, and consolidate both into a single analytics-ready platform while ensuring data consistency and historical accuracy.


## Architecture

```text
Raw CSV Data
s3 / Volumes
   ↓
Bronze Layer (Raw Delta Tables)
   ↓
Silver Layer (Cleaned & Conformed Data)
   ↓
Gold Layer (Business-Ready Dimensions & Facts)
```


## Project Structure

```text
databricks-fmcg-medallion-architecture-delta-lake/
│
├── 1_fmcg_dimension_data_processing/
│   ├── 1_customers_data_processing.py
│   ├── 2_products_data_processing.py
│   └── 3_pricing_data_processing.py
│
├── 2_fmcg_fact_data_processing/
│   ├── 1_full_load_fact.py
│   └── 2_incremental_load_fact.py
│
├── child_company_raw_data/
│   ├── orders/
│   │   ├── landing/
│   │   │   └── orders.csv
│   │   └── processed/   # Files moved here after successful processing
│   │
│   ├── gross_price/
│   │   └── gross_price.csv
│   │
│   ├── customers/
│   │   └── customers.csv
│   │
│   └── products/
│       └── products.csv
│
├── setup/
│   ├── dim_date_table_creation.py
│   ├── fmcg_catalog_schema.sql
│   └── schema_import.py
│
└── README.md
```


