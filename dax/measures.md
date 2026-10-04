# DAX Measures & KPI Calculations Documentation

This document records the exact DAX measures and Power BI visual-level calculations used across the **Olist E-Commerce Sales & Customer Analytics** dashboard.

---

## 1. Explicit DAX Measures

These calculations are defined as formal DAX measures in Power BI.

---

### 1. Average Order Value
* **DAX Formula:**
  ```dax
  Average Order Value =
  DIVIDE(
      SUM(fact_order_items[total item value]),
      DISTINCTCOUNT(fact_order_items[order_id])
  )
  ```
* **Business Purpose:** Calculates the average value of an order based on total item value (combining merchandise item price and allocated freight).
* **Current Dashboard Value:** `160.58`

---

### 2. Late Orders %
* **DAX Formula:**
  ```dax
  Late Orders % =
  DIVIDE(
      CALCULATE(
          DISTINCTCOUNT(fact_orders[order_id]),
          fact_orders[is_late] = 1
      ),
      DISTINCTCOUNT(fact_orders[order_id])
  )
  ```
* **Business Purpose:** Measures the percentage of orders delivered past the estimated delivery date out of all orders.
* **Current Dashboard Value:** `7.87%`

---

### 3. Average Customer Value
* **DAX Formula:**
  ```dax
  Average Customer Value =
  DIVIDE(
      SUM(fact_order_items[total item value]),
      DISTINCTCOUNT(dim_customers[customer_unique_id])
  )
  ```
* **Business Purpose:** Measures the average revenue generated per unique human customer.
* **Current Dashboard Value:** `164.87`

---

### 4. Total Customer Revenue
* **DAX Formula:**
  ```dax
  Total Customer Revenue =
  SUM(fact_order_items[total item value])
  ```
* **Business Purpose:** Calculates total customer-related top-line revenue derived from item value.
* **Current Dashboard Value:** `15.84M`

---

### 5. Average Item Value
* **DAX Formula:**
  ```dax
  Average Item Value =
  AVERAGE(fact_order_items[total item value])
  ```
* **Business Purpose:** Calculates the average monetary value of an individual order item.
* **Current Dashboard Value:** `140.64`

---

### 6. Average Delivery Days
* **DAX Formula:**
  ```dax
  Average Delivery Days =
  AVERAGE(fact_orders[delivery_duration_days])
  ```
* **Business Purpose:** Calculates the average number of days taken for delivery from order purchase to customer handover.
* **Current Dashboard Value:** `12.6`

---

### 7. Late Orders
* **DAX Formula:**
  ```dax
  Late Orders =
  CALCULATE(
      DISTINCTCOUNT(fact_orders[order_id]),
      fact_orders[is_late] = 1
  )
  ```
* **Business Purpose:** Counts the distinct number of orders classified as late.

---

## 2. Customer Retention & Repeat Metric Implementation

### 8. Repeat Customer %
* **Implementation Details:**
  The final dashboard uses the customer-level field:
  ```
  dim_customers[is_repeat_customer]
  ```
  This is a pre-calculated binary flag (`1` for customers who placed more than one order, `0` for single-order customers).
* **Power BI Card Visual Configuration:**
  * **Field:** `dim_customers[is_repeat_customer]`
  * **Aggregation:** `Average of dim_customers[is_repeat_customer]`
  * **Format:** Percentage (`0.00%`)
* **Current Dashboard Value:** `6.38%`
* **Business Purpose:** Measures the percentage of customer profiles that represent repeat buyers.

---

## 3. Visual-Level KPI Aggregations

The dashboard also contains the following KPI calculations created directly through Power BI visual-level aggregation rather than standalone DAX measures:

| KPI Card Title | Visual Aggregation Expression | Table & Field | Filter Context | Dashboard Value |
| :--- | :--- | :--- | :--- | :---: |
| **Total Orders** | `Distinct Count` | `fact_orders[order_id]` | None (All Orders) | `99.44K` |
| **Total Customers** | `Distinct Count` | `dim_customers[customer_unique_id]` | None (All Customers) | `96.10K` |
| **Total Revenue** | `Sum` | `fact_order_items[total_item_value]` | None (All Items) | `15.84M` |
| **Repeated Customers** | `Sum` | `dim_customers[is_repeat_customer]` | None (All Customers) | `6,342` |
| **Total Products** | `Distinct Count` | `dim_products[product_id]` | None (All Products) | `32.95K` |
| **Product Categories** | `Distinct Count` | `dim_products[product_category_name_english]` | None (All Categories) | `74` |
| **Total Items Sold** | `Count` | `fact_order_items[order_item_id]` | None (All Line Items) | `98.67K` |
| **Total Sellers** | `Distinct Count` | `dim_sellers[seller_id]` | None (All Sellers) | `3,095` |
| **Delivered Orders** | `Distinct Count` | `fact_orders[order_id]` | Visual filter: `order_status = "delivered"` | `96.48K` |

---

## Technical Architecture Distinction

* **Explicit DAX Measures:** Used for ratio calculations (`DIVIDE`), filtered aggregations (`CALCULATE`), and measures requiring consistent cross-visual filtering.
* **Visual Aggregations:** Applied for standard counts and distinct counts directly inside Power BI Card visuals to maintain model simplicity and execution efficiency.
