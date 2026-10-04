# Business Insights & Findings

This document presents business findings derived directly from the visible data and charts in the completed **Olist E-Commerce Sales & Customer Analytics** Power BI dashboard.

---

## 1. Executive Insights

### Observation 1: High Fulfillment Completion Rate
* **Data:** The dashboard displays **99.44K Total Orders**, of which **96.48K** are delivered (97.02% fulfillment rate on the order status donut visual). Canceled, unavailable, and in-process orders represent small proportions of historical volume.
* **Business Implication:** The core fulfillment pipeline functions reliably for the vast majority of orders. Operational disruptions that lead to outright non-delivery are rare.

### Observation 2: Revenue Expansion Trajectory
* **Data:** The Revenue Trend by Year visual shows steep top-line growth from 2016 through 2017, followed by a moderation in growth slope into 2018, culminating in **15.84M Total Revenue**.
* **Business Implication:** After rapid early growth across 2016–2017, the marketplace transitioned toward a mature volume run-rate in 2018, indicating that continued expansion requires expanding customer acquisition or improving seller recruitment.

---

## 2. Customer & RFM Insights

### Observation 3: High-Value Customer Concentration
* **Data:** The Customer & RFM Analysis page reveals **96.10K Total Customers** generating **15.84M Total Customer Revenue**, with an **Average Customer Value of 164.87**.
* **Business Implication:** In the RFM breakdown, the *Recent High-Spenders* and *Slipping High-Spenders* segments represent a substantial proportion of overall platform revenue, highlighting that revenue relies significantly on high-ticket buyers.

### Observation 4: Low Repeat Purchase Rate
* **Data:** The dashboard records **6,342 Repeated Customers**, representing a **6.38% Repeat Customer %**.
* **Business Implication:** Over 93% of customers only purchase once on Olist. The platform operates primarily as an acquisition-driven marketplace for durable goods rather than a high-frequency recurring subscription or repeat-grocery service. Marketing strategy must focus on acquisition unit economics (CAC vs. LTV).

---

## 3. Product & Sales Insights

### Observation 5: Diverse Catalog with Leading Anchor Categories
* **Data:** The catalog spans **32.95K Total Products** across **74 Product Categories**, with **98.67K Total Items Sold** and an **Average Item Value of 140.64**.
* **Business Implication:** Sales concentration is led by anchor categories: `health_beauty`, `watches_gifts`, and `bed_bath_table` generate the highest revenue. Other categories like `sports_leisure` and `computers_accessories` provide steady volume, giving the marketplace a diversified catalog base.

### Observation 6: Skew in Individual Product Revenue
* **Data:** The Top 10 Products by Revenue visual shows individual product items generating up to ~R$ 60K–70K each, while order volume across top products ranges between 300 and 500 units.
* **Business Implication:** Top-earning products combine moderate sales volume with higher unit price points, rather than relying strictly on hyper-volume low-cost goods.

---

## 4. Seller Insights

### Observation 7: Merchant Concentration
* **Data:** The platform comprises **3,095 Total Sellers**. The Top 10 Sellers by Revenue visual demonstrates that a concentrated group of top sellers generates between R$ 150K and R$ 230K each.
* **Business Implication:** Marketplace commercial health depends meaningfully on key merchant partners. Maintaining partner satisfaction and seller support programs for top merchants protects top-line revenue.

---

## 5. Delivery & Logistics Insights

### Observation 8: Strong Average Transit Times with Manageable Delays
* **Data:** Across **96.48K Delivered Orders**, the platform achieves an **Average Delivery Days of 12.6**, with a **Late Orders % of 7.87%**.
* **Business Implication:** Despite Brazil's vast geography, over 92% of orders arrive within the promised estimated delivery window.

### Observation 9: Geographic Concentration of Late Deliveries
* **Data:** The Top 10 States by Late Orders visual reveals that late deliveries are concentrated in major population centers, led by São Paulo (SP), Rio de Janeiro (RJ), Minas Gerais (MG), and Bahia (BA).
* **Business Implication:** While SP leads in late order counts due to sheer total volume, regional logistics friction in RJ and northeastern states like BA represents a higher relative share of delivery delays, indicating regional carrier routing bottlenecks.

---

## 6. Analytical Summary

| Analysis Dimension | Key Metric / Observation | Strategic Takeaway |
| :--- | :--- | :--- |
| **Top-Line Scale** | 99.44K Orders, 15.84M Revenue | Scaled e-commerce platform with steady 2018 run-rate. |
| **Customer Behavior** | 6.38% Repeat Rate, 164.87 ACV | Single-purchase acquisition model; high-spend segments drive majority of GMV. |
| **Catalog Performance** | 74 Categories, 140.64 Avg Item Value | Anchor categories (`health_beauty`, `watches_gifts`) anchor top revenue. |
| **Logistics Operations**| 12.6 Avg Days, 7.87% Late Rate | Solid baseline logistics; delays concentrated in specific state corridors. |
