# Olist Ecommerce Data Analysis and Hypothesis Testing
This project analyzes Olist e-commerce data (orders, order_items, customers, payments, reviews, geolocation, and leads) from 2016–2018 to extract business insights about sales patterns, customer behaviour, and operational issues. I used SQL to build clean, reproducible datasets and Python (pandas, matplotlib/seaborn, pingouin/scipy/statsmodels) for exploration, visualization, and statistical testing. Key methods included time-series aggregation, RFM-style customer segmentation, category-level revenue/volume analysis, and robustness checks (Welch ANOVA, pairwise tests, Welch t-tests, nonparametric tests and bootstrap CIs).

# Introduction
Understanding the dynamics of e-commerce operations is crucial for strategic decision-making. This project leverages data from Olist, a Brazilian e-commerce platform, to analyze sales over time, payment methods, and top categories. By integrating SQL for data manipulation and Python for visualization, the analysis offers a comprehensive view of the business's strengths and areas for improvement.

The dataset is sourced from Kaggle's Olist Brazilian E-commerce Dataset, encompassing transactions from March 2016 to August 2018. The data is loaded into an SQLite database with the following key tables:

- Orders: Details of each order, including timestamps for various stages.
- Customers: Anonymized customer information and locations.
- Products: Product specifications and categories.
- Product Category Name Translation: English translation of the product category
- Sellers: Information on sellers, their locations, and performance metrics.
- Order Items: Breakdown of items within each order, including pricing and shipping costs.
- Order Payments: Payment details of Orders

# Main Deliverables
- Cleaned datasets and reproducible SQL queries / notebook cells.
- Visuals and tests showing temporal patterns (weekday > weekend revenue), category performance (price-driven vs volume-driven categories), and payment behaviours (installment usage associated with higher order totals).
- A one-page set of prioritized, actionable recommendations for marketing, payments, inventory and analytics
This analysis is designed to be operational: it includes concrete SQL recipes, robustness checks for statistical claims, and next steps (A/B experiments and regression controls) so stakeholders can validate and act on the findings.

# Key Insights 
1. Seasonality and Trends:
    - There are significant variations in total revenue based on the month and day of the week.
    - Although some months show higher revenue, the evidence is not strong enough to confirm specific months are better than others.
    - For days however, there is a statistically significant evidence that Weekdays (Monday-Thursday) have a higher revenue than Weekends (Friday- Sunday)
2. Top Products and Categories:
    - Top products by revenue : Health and Beauty, Watches Gift, Bed Bath Table
    - Top products by number of orders : Bed Bath Table, Health and Beauty, Sports Leisure
    - Top products by number of units sold : Bed Bath Table, Health and Beauty, Sports Leisure
    - The difference of rankings between performance by revenue and by quantities shows some categories generate revenue more one the price premium while some generate revenue by volume 
3. Order Payments Behaviour
    - The average payment for an order is 160.99 with a 95% confidence interval between 160.4 and 161.5
    - There is a strong evidence that orders paid in installments have a higher total payment than orders paid in single payment
    - There is a weak evidence showing that orders

# Actionable Recommendations
1. Exploit weekday strength
    - Run targeted promotional campaigns Monday–Thursday. Weekdays show reliably higher daily revenue → higher chance promotions convert and produce incremental revenue.
    - Create weekday-only promo codes (e.g., time-limited discounts, email pushes, flash bundles). and baseline campaign on weekends
2. Tailor strategy per category
    - Differentiate interventions based on whether category is price-driven (health_beauty, watches_gifts) or volume-driven (bed_bath_table).
    - Price-driven categories: focus on premium merchandising, bundles, warranty/upsell (higher margin).
    - Volume-driven categories: focus on cross-sell, volume discounts, buy-1-get-1, shipping thresholds to increase AOV (Average order value).
3. Payments and Conversions 
    - Leverage installments to increase AOV. Customers who use installments spend more, consider promoting installment options for mid/high value carts.
    - Multiple payment methods are used for some orders and show a small difference in order value. ensure reconciliation & fraud controls.
