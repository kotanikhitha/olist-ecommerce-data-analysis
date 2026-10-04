# Project Methodology

This document outlines the end-to-end analytical workflow executed to develop the **Olist E-Commerce Sales & Customer Analytics** project.

---

## 1. Data Collection & Profiling
* **Source:** Official Olist Brazilian E-Commerce dataset from Kaggle comprising 9 relational CSV files (99,441 orders spanning 2016–2018).
* **Initial Inspection:** Data structures, row counts, null values, and candidate keys were audited to identify technical challenges:
  * Difference between transactional `customer_id` and unique human `customer_unique_id`.
  * Geolocation duplicate rows and coordinate bounds.
  * Untranslated Portuguese product category strings.
  * Duplicate survey submissions in reviews.

---

## 2. Data Cleaning & Transformation
* **Customer Entity Resolution:** Maintained `customer_id` for order-level linkages while computing customer order counts on `customer_unique_id` to establish the `is_repeat_customer` flag.
* **Product Catalog Standardization:** Enriched product catalog with English translations; mapped untranslated categories (`pc_gamer`, `portateis_cozinha_e_preparadores_de_alimentos`) and imputed missing catalog dimensions with median values.
* **Geolocation Deduplication:** Filtered coordinate records falling outside Brazil; grouped by postal code prefix using median coordinates to prevent Cartesian explosions.
* **Operational Metric Derivation:** Precalculated delivery transit duration (`order_delivered_customer_date` minus `order_purchase_timestamp`), estimated duration, delivery delay vs. estimate, and late delivery flags (`is_late = 1` if delivered after estimate).
* **Review Deduplication:** Retained the most recent review survey submission per order by `review_answer_timestamp`.

---

## 3. Data Modeling
* Organized cleaned entities into a Star-style analytical model featuring core transactional fact tables (`fact_orders`, `fact_order_items`, `fact_order_payments`, `fact_order_reviews`) surrounded by dimension tables (`dim_customers`, `dim_products`, `dim_sellers`, `dim_geolocation`).
* Loaded tables into Power BI and established relational links.

---

## 4. Advanced Customer Analytics (RFM & Cohorts)
* **RFM Segmentation:**
  * **Recency (R):** Days between last purchase and the dataset snapshot date.
  * **Frequency (F):** Total order count per unique customer. Because 97% of customers purchased once, custom thresholds were applied (1 order, 2 orders, 3+ orders).
  * **Monetary (M):** Total lifetime customer spend (`price + freight`).
  * Mapped customers into business segments: *Champions*, *Loyal Customers*, *Recent High-Spenders*, *Slipping High-Spenders*, *Promising / Developing*, *New Active Shoppers*, and *Hibernating / One-Time Lost*.
* **Cohort Analysis:** Grouped customers by acquisition month (first purchase) to evaluate subsequent monthly return rates over 6-month windows.

---

## 5. DAX & Analytical Metric Development
* Implemented core business measures using DAX:
  * `Average Order Value`: Total item value divided by distinct order count.
  * `Late Orders %`: Distinct count of late delivered orders divided by total orders.
  * `Average Customer Value`: Total item value divided by distinct human customers.
  * `Total Customer Revenue`: Sum of total item value.
  * `Average Item Value`: Mean value of individual order items.
  * `Average Delivery Days`: Mean duration in days from purchase to delivery.
  * `Late Orders`: Absolute count of late orders.
* Documented visual-level aggregations (`Distinct Count`, `Count`, `Average`) used directly on Power BI Card visuals.

---

## 6. Power BI Visualization Design
* Built an interactive four-page dashboard structure:
  1. *Executive Overview*: High-level executive KPIs, annual revenue trajectory, order status breakdown, category demand.
  2. *Customer & RFM Analysis*: Customer valuation, repeat buyer share, and segment profiles across R, F, and M dimensions.
  3. *Product & Sales Analysis*: Catalog coverage, category revenue contributions, top products by revenue and volume.
  4. *Seller & Delivery Analysis*: Delivery days, order status durations, seller leaderboard, and regional late-order distribution.

---

## 7. Business Interpretation & Storytelling
* Synthesized dashboard findings into non-causal, objective business implications across executive, customer, product, merchant, and logistics dimensions.
