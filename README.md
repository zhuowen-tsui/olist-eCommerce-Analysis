# Olist Brazilian E-Commerce Data Analysis

## Project Background
This is a Brazilian ecommerce public dataset of orders made at Olist Store.
The anonymised dataset has information of 100k orders from 2016 to 2018
made at multiple marketplaces in Brazil.
Its features allows viewing an order from multiple dimensions:
from order status, price, payment and freight performance
to customer location, product attributes and reviews written by customers.

**Analysis Workflow**:
Data Understanding →  SQL Multi-table Exploration (QGS Overview + Cross analysis) → Tableau Visualization → Business Insights & Recommendations

## Dataset Introduction
The dataset is a relational multi-table dataset published on Kaggle, containing Brazilian order records.
Core tables:
- `olist_orders_dataset`: order status, purchase & delivery timestamps
- `olist_customers_dataset`: customer geographic information and user ID
- `olist_order_items_dataset`: product items within each order
- `olist_products_dataset`: product category and attribute information
- `olist_order_reviews_dataset`: customer review scores and comments
- `olist_geolocation_dataset`: city geographic coordinates

## Analysis Framework
1. **Overall Business Overview**
  (*User-Goods-Scenario*)

1) **User**

    a) Customer geographic distribution
      
![User Dashboard: Geo Distribution & RFM & Repurchase](Paste_your_image_link_here)

Olist’s customer base shows strong geographic concentration in Southeast Brazil.
São Paulo (SP) accounts for 41.90% of total customers, followed by Rio de Janeiro (RJ, 12.90%) and Minas Gerais (MG, 11.70%). Those three states occupy 66.5% of all customers of Olist in Brazil.

Within these three core states:
- In SP, São Paulo dominates, followed by Campinas and Guarulhos.
- In RJ, the largest city is Rio de Janeiro, with Niterói and Nova Iguaçu ranking second and third.
- In MG, Belo Horizonte is the leading city, but shows not much advantage over Contagem and Juiz de Fora.

**Insights and recommendations**:
- The top‑3 southeast states contribute 66.5% of all customers. Heavy reliance on São Paulo creates concentration risk and unstability for the platform.
- State capital cities attract most local consumers, especially in Rio de Janeiro where over half of state‑level customers come from the capital city.
- Northern and northeastern states only occupy a small portion of users, showing untapped market potential.

Keep retaining customers in developed areas to ensure profits. Focus marketing and logistics investment on Southeast Brazil for short‑term performance.
In the long run, expand development in northern regions to acquire more customers and most importantly, to upgrade business stability.

      - RFM customer segmentation
        - Recency
        - Frequency
        - Monetary  
      - Customer repurchase behavior
        - average repurchase interval
        - repurchase ratio
        - T2P
    - **Goods**
      - Pareto analysis by product category
      - price tier analysis
      - intra-category price structure
        - five top categories
      - category volume VS revenue
        - top/ medium/ bottom three parts
    -**Scenario**
     - review scores
     - delivery
       - whether big size
       - whether remote area
     - order time period
       - daily
       - weekly  
       - monthly
    
- **Cross Analysis**
  - cross-state shipment & low reviews
  - delivery delay & categories
  - RFM & categories  

## Dashboard Introduction
> Note: Due to Tableau Public cross-origin CSP restriction, embedded viz may fail to load on GitHub Pages. Please click the link to open interactive dashboards in new browser tabs.
1. **Dashboard 1: User Analysis**
   Customer geographic distribution, RFM segmentation, repurchase rate and order frequency distribution.
2. **Dashboard 2: Goods Analysis**
   Sales volume & revenue by product category, top-selling products, product size & weight distribution.
3. **Dashboard 3: Order & Logistics Analysis**
   Regional delivery performance, delivery cycle and late delivery rate.
4. **Dashboard 4: Review & Satisfaction Analysis**
   Review score distribution, correlation between delivery delay and customer rating.

## Key Business Insights
1. Most customers are one-time purchasers; platform repurchase rate is low with high customer churn risk.
2. Southeast Brazil (São Paulo, Rio de Janeiro) contributes most of platform orders and revenue.
3. Home, beauty and health-related categories generate the highest revenue.
4. Delivery delay has strong negative correlation with review scores; logistics timeliness is the core factor of customer satisfaction.

