# Dataset & Analytical Tables

This project analyzes the **Olist Brazilian E-Commerce Public Dataset**, covering 99,441 commercial orders placed between 2016 and 2018 across Brazil.

To keep this GitHub repository lightweight and comply with repository hosting best practices, the large raw dataset files are not duplicated here. The raw dataset is publicly accessible via Kaggle: [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

---

## Analytical Tables Used in Power BI

The project data pipeline cleaned, structured, and exported the following 10 analytical tables:

### Dimension Tables
1. **`dim_customers`**: Master customer profile table. Links order transactions (`customer_id`) to unique human buyers (`customer_unique_id`), geographic city/state, and repeat customer flags (`is_repeat_customer`).
2. **`dim_products`**: Product catalog metadata, packaging dimensions (weight, length, height, width), photo counts, and standardized English category translations.
3. **`dim_sellers`**: Merchant partner directory containing seller identifiers, city, and state locations.
4. **`dim_geolocation`**: Brazilian postal code coordinate lookup, deduplicated by 5-digit zip code prefix using median latitude and longitude coordinates.

### Fact Tables
5. **`fact_orders`**: Transaction header table recording order lifecycle milestones (purchase, approval, carrier handover, customer delivery, estimated delivery) and computed transit durations.
6. **`fact_order_items`**: Sales line-item grain recording product IDs, seller IDs, item price, freight cost, and total item value (`price + freight_value`).
7. **`fact_order_payments`**: Financial transaction table recording payment methods (`credit_card`, `boleto`, `voucher`, `debit_card`), installment counts, and payment amounts.
8. **`fact_order_reviews`**: Customer feedback survey data recording review scores (1 to 5) and timestamps, deduplicated per order.

### Analytical Reference Tables
9. **`rfm_customer_segments`**: Customer-level analytical segmentation dataset mapping each unique customer to their Recency, Frequency, and Monetary scores and behavioral segments.
10. **`cohort_retention_matrix`**: Monthly cohort retention table tracking the percentage of acquired customers who returned to place subsequent orders across monthly intervals.
