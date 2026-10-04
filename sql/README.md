# SQL Processing Artifacts

SQL processing was part of the project workflow. Original SQL scripts are not included in this GitHub package because they were not available as standalone files at packaging time.

## Workflow Overview

* **Data Preparation & Ingestion:** The project workflow utilized an embedded SQLite database environment (`olist.db`) during exploratory data analysis, data transformation, and data quality validation.
* **Aggregations & Modeling:** Intermediate SQL queries were executed to profile fulfillment statuses, aggregate category sales, deduplicate records, precompute delivery latency, and validate KPIs before importing clean dimensional tables into Power BI.
