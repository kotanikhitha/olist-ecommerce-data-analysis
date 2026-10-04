# Power BI Dashboard

This folder contains the compiled Power BI workbook for the **Olist E-Commerce Sales & Customer Analytics** project.

## Primary File

* **`Olist_Ecommerce_Dashboard.pbix`**: The interactive Power BI report file.

## Dashboard Architecture

The dashboard consists of four completed analytical report pages:

1. **Executive Overview**: High-level KPI monitoring, annual revenue trajectory, order status breakdown, customer segment split, and category demand.
2. **Customer & RFM Analysis**: Customer lifetime valuation, repeat buyer behavior, and deep-dive RFM segment metrics (recency, frequency, monetary value).
3. **Product & Sales Analysis**: Product catalog coverage, category revenue contributions, top products by revenue and volume.
4. **Seller & Delivery Analysis**: Logistics performance, transit duration across order statuses, late delivery hotspots across Brazilian states, and top seller contributions.

> [!NOTE]
> **Data Connection Notice:**
> The `.pbix` file contains cached data model tables and visualizations. If refreshing data from an external folder or database on a new machine, file path connections in Power Query (`Data source settings`) will need to be updated to match the local system paths where the analytical CSV files reside.
