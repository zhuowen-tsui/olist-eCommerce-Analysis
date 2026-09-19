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

**Insights & recommendations**:
- The top‑3 southeast states contribute 66.5% of all customers. Heavy reliance on São Paulo creates concentration risk and unstability for the platform.
- State capital cities attract most local consumers, especially in Rio de Janeiro where over half of state‑level customers come from the capital city.
- Northern and northeastern states only occupy a small portion of users, showing untapped market potential.

Keep retaining customers in developed areas to ensure profits. Focus marketing and logistics investment on Southeast Brazil for short‑term performance.
In the long run, expand development in northern regions to acquire more customers and most importantly, to upgrade business stability.


    b) RFM customer segmentation

![RFM Dashboard](Paste_your_rfm_image_here)

RFM (Recency, Frequency, Monetary) scores are calculated for each customer.
A 4-point scoring threshold is used to classify customers into 7 segments:

| Segment | Recency Score | Frequency Score | Monetary Score |
|---------|--------------|-----------------|----------------|
| Important Client | ≥ 3 | ≥ 3 | ≥ 3 |
| Retaining Client | ≥ 3 | ≤ 2 | ≥ 3 |
| Losing Client | ≤ 2 | ≥ 3 | ≥ 3 |
| Potential Client | ≥ 3 | ≥ 3 | ≤ 2 |
| New Client | ≥ 3 | ≤ 2 | ≤ 2 |
| Ordinary Client | ≤ 2 | ≥ 3 | ≤ 2 |
| Lost Client | All other cases | — | — |

*Segment Distribution*

| Segment | Customer Count | Proportion |
|---------|---------------|------------|
| Lost Client | 86,313 | 89.8% |
| New Client | 9,479 | 9.9% |
| Ordinary Client | 205 | 0.2% |
| Retaining Client | 51 | 0.1% |
| Potential Client | 39 | 0.0% |
| Important Client | 3 | 0.0% |
| Losing Client | 5 | 0.0% |

**Insights**:

- **Extremely high porportion of one_off customers**: Over 89.8% of customers fall into the "Lost Client" segment, meaning they have not purchased for a long time and have low purchase frequency or spending. This confirms that Olist is essentially a one-time-purchase marketplace with very weak customer loyalty.
- **Almost no high-value repeat customers**: Only 3 customers qualify as "Important Clients" (high recency, high frequency, high monetary value). Combined with "Retaining" and "Losing" clients, the total repeat-purchasing customer base is negligible — well under 0.5% of all users. Oblist platform performs badly on acquiring consumers of hight quality.
- **New customer acquisition dominates**: New Clients (recent but low frequency and low spending) account for 9.9% of the base, which is the largest active segment. This indicates the platform heavily relies on continuous new-user acquisition rather than retention.

**Recommendations**:
-  The platform should invest in post-purchase services (e.g., personalized recommendations, membership programs, re-marketing campaigns) to convert new clients into repeat buyers. Gradually promote the porportion of hight value customers.
-  Even though numbers of important, retaining and potential clients are small, these customers should be prioritized with exclusive perks like early access and memebership discounts of grading system to protect revenue stability.
-  Re-engagement campaigns (discount coupons, win-back emails) targeting the 86k lost users could yield meaningful recovery at relatively low cost.

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

