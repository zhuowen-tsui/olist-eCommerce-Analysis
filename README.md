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
**1. Overall Business Overview**
  (*User-Goods-Scenario*)

**1) User**
**dashboard link:https://public.tableau.com/views/olist_Ecommerce_user/user**

**a)customer geographic distribution**
    
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


**b)RFM Customer Segmentation**
   
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
-  

**c) Customer Repurchase Behavior**

We analyze repurchase behavior from three dimensions, which are 
- Average time gap between any two consecutive orders of repurchasing customers
- Average days between a customer’s first order and second order
- Percentage of customers who placed more than one order on the platform

After calculation, we can find that customers apply the nect purchase after 78 days on average, of which T2P is 80 days. However, only 3% of consumers on Olist platformed placed a second purchase.

**Insights**:

- **Extremely low repurchase rate.** Only 3% of customers make more than one purchase on Olist. The vast majority of users are one-time buyers, which is consistent with the large "Lost Client" group discovered in the RFM segmentation. It indicates the platform’s revenue heavily depends on continuously acquiring new customers, which drives high customer acquisition cost and unstable long-term revenue.
- **Long latency before the second purchase.** For customers who do repurchase, the average time between their first and second purchase is 80.35 days, close to the overall average repurchase interval of 78.23 days. This means even satisfied customers do not return quickly. The long interval creates a high risk of customer churn: users may forget the platform, switch to competitors, or lose interest before they make a second purchase.
- **Weak customer stickiness.** The low repurchase rate paired with a long repurchase window proves low platform loyalty. Customers view Olist mostly as a one-off shopping channel instead of a regular destination. There is little recurring consumption habit formed among buyers.

**Recommendations**:

- Trigger personalized reminder campaigns around the 60–70 day window after a customer’s first purchase, before the 80-day average second-purchase threshold. Coupons, product recommendations and after-sales follow-ups can shorten the repurchase interval and increase the chance of a second order before users fully churn.
-  Improve post-order experience, including logistics transparency, after-sales support and product review incentives. Better first-order experience can shorten the waiting time for the next purchase and lift repurchase rate.
- Combine repurchase metrics with RFM customer segments: prioritize re-engagement resources on the `New Client` group, which is the largest pool of recently active one-time buyers, as they have the highest potential to convert into repeat customers.
- Track repurchase rate and purchase interval as core long-term KPIs to scheme future business campaigns.


**2) Goods** 
**dashboard link:https://public.tableau.com/views/olist_Ecommerce_goods/goods**

**a)Pareto analysis by product category**

This Pareto analysis applies the classic 80/20 principle to product categories. It helps identify which product categories contribute the majority of order volume and revenue, so we can distinguish core high-impact categories from long-tail niche categories.

**Chart Explanation**

The descending bar chart shows revenue of each product category, while the curve represents cumulative percentage of total revenue. The chart shows that a small number of top categories contribute 79.62% of total revenue, nearly matching the Pareto 80/20 rule. A few dominant categories carry almost all transaction volume, while most remaining categories belong to the long tail with very small sales.


**Insights & recommendations**:

- **Sales follow the Pareto principle closely**. Around 80% of sales volume comes from a small number of top-selling categories, such as `relogios_presentes` (watches/gifts), `esporte_lazer` (sports leisure), `moveis_decoracao` (furniture & decoration). The long tail contains dozens of categories but collectively accounts for only ~20% of total volume.
-**Prioritize resource allocation for top categories**. Concentrate marketing budget, inventory stocking and logistics optimization on the small set of categories that drive ~80% of volume. These categories are the platform’s core business foundation.


**b) price tier**

As we try to find out products of which price range contribute the most revenue. Products are classified into four tiers by product price:
| Tier | Price Range |
|------|-------------|
| low | price < 50 |
| medium | 50 ≤ price < 100 |
| high | 100 ≤ price < 150 |
| premium | price ≥ 150 |

**Insights & recommendations**:

From the donut chart, we can see that premium products occupy the largest proportion of revenue, followed by high-priced, medium and low-priced goods.Although low-tier items may contribute to transaction volume, they generate relatively little revenue. This reveals that Olist’s revenue structure is heavily reliant on higher-value merchandise.
- **Cross-selling strategy**: When customers purchase low/medium-priced items, recommend premium or high-tier related products in the checkout page and post-purchase emails. For example, suggest premium accessories after customers buy low-priced watches or sports goods, lifting average order value.
- **Tiered promotion design**: Avoid heavy discounting on premium products, which erodes profit margin. Instead, apply coupons and promotions mainly to low and medium-tier items to attract new shoppers, while offering exclusive services (extended warranty, priority delivery) for premium products to retain high-value buyers.
- **Product enriching within top categories**: For core categories like watches & gifts and sports leisure, maintain a balanced mix: keep low-price SKUs for entry-level customer acquisition, while continuously enriching premium product selections to sustain high-margin revenue streams.


**c) intra-category price structure**

We consider price structures within top 5 categories to see wether expensive or cheap-priced categories are more likely to gain more revenue.

**Insights**:

While premium products dominate overall platform revenue, the weight of each price tier differs substantially from category to category. Some categories rely heavily on premium SKUs to drive most of their revenue, while others have a more balanced mix across medium and high price ranges.
- **Premium products are the dominant revenue component inside most top categories**. Even within categories with large transaction volumes, premium items capture the biggest portion of category revenue. Medium and low-price products only make up a smaller supplementary share of revenue within each category. Low-priced goods may bring order volume, but they contribute little revenue proportionally inside the category.

**Recommendations**:

- **Customize product portfolio by category**. For categories where premium products already make up most revenue, continue enriching high-end SKUs and focus on quality and after-sales service.For categories with higher medium/low tier revenue share, keep affordable entry-level items to attract new customers, and add a small selection of premium alternatives for upselling.
- **Design category-specific upsell and cross-sell campaigns**. In categories with strong premium revenue proportion, recommend upgraded premium versions when customers add medium-tier items to cart. In categories dominated by medium-priced products, use premium accessories to lift order value without forcing customers to buy expensive main goods.
- **Set differentiated promotion rules per category**. Avoid universal discount strategies across all categories. For categories with high premium revenue share, protect premium profit margin by limiting discounts on high-value products; use promotions only on medium/low tier SKUs to draw traffic.
- **Combine intra-category price structure with RFM customer segments**. Promote premium goods within categories that naturally perform well in high-price tiers to high-value customers (`Important Client`, `Retaining Client`), as these buyers have higher acceptance of premium products in these categories.


**d)category volume VS revenue**

The bubble chart visualizes the relationship between transaction volume and total sales revenue for selected product categories. The size and colour of each bubble further distinguish groups: `top6` (dark purple), `medium` (light purple), and `bottom` (pale pink).

**Insights & recommendations**:

Top categories deliver both large transaction volume and the majority of platform revenue. These core categories are the dual engine of Olist’s business. 
While Bottom long-tail categories show low revenue despite relatively higher average unit price.It implies these long-tail categories cannot scale up revenue even when individual product prices are higher, because their overall transaction scale is limited.
Compared with medium and bottom groups, top6 categories convert sales volume into revenue most effectively. They have stable demand and sufficient order density, which can spread logistics and operational fixed costs over more orders and achieve better operational efficiency.
- **Priority resources for top6 categories.** Continue investing in inventory management, logistics capacity and marketing campaigns for the top six categories, as they create the largest volume and revenue. These categories deserve priority allocation of warehouse space and customer service manpower.
- **Reassess the bottom long-tail categories.** Bottom categories bring little total revenue. Evaluate whether to shrink SKU diversity or adopt drop-shipping to reduce holding cost. Only keep niche products with high profit margin and loyal small customer groups.
- **Replicate top-category success.** Study product selection, pricing and promotion strategies from top6 categories, and replicate proven tactics in medium-sized categories to expand their volume and revenue.
- **Combine with intra-category price structure.** For top6 categories that already have high volume and revenue, use upsell strategies within the category’s price tiers to lift average order value and further boost profit.


**3)Scenario**
**dashboard link:https://public.tableau.com/views/olist_Ecommerce_scenario/scenario**

**a)factors influencing review scores**

This section investigates what drives customer satisfaction on the platform, by comparing good reviews (review score >3) against bad reviews (review score <=3) across order value, delivery timeliness and freight cost.

| Dimensions | High Review | Low Review |
|--------|-------------|------------|
| Avg. Payment Value (BRL) | 161.66 | 202.98 |
| Avg. Days Ahead of Delivery Estimate (days) | 13.19 | 8.40 |
| Avg. Freight Value (BRL) | 19.76 | 20.78 |
| Freight Ratio (freight / order value) | 44.7% | 29.8% |

**Insights**:

- **Faster delivery is the strongest driver of positive reviews.** Customers with high reviews receive their orders an average of 13.19 days ahead of the estimated delivery date, while low-review customers receive theirs only 8.40 days early. This gap of nearly 5 days shows that earlier-than-expected delivery strongly boosts satisfaction. Conversely, any delay or near-estimate delivery significantly drags down review scores.
- **Low-review orders have higher order value.** Bad reviews are associated with higher average payment value (BRL 202.98) than good reviews (BRL 161.66). This suggests customers who spend more tend to have higher expectations. When expensive orders are delivered late or poorly handled, the dissatisfaction is amplified, leading to worse ratings.
- **Freight cost is similar in absolute terms, but matters more for low-value orders.** Average freight value is nearly identical across both groups (~BRL 20). However, because high-review orders have lower payment value, freight accounts for a much larger share (44.7%) of the total order. This means customers who place smaller orders are more sensitive to shipping cost relative to their purchase.
- **Delivery timeliness matters more than product price for satisfaction.** The largest differentiator between high and low reviews is not the product itself but delivery speed. Even customers who spend less leave good reviews when their order arrives early. This confirms logistics performance is the core lever for improving customer ratings.

**Recommendations**:

- **Prioritize on-time and early delivery.** Since delivery earliness is the strongest predictor of review score, the platform should set internal delivery targets well ahead of the public estimate, especially for high-value orders where customer expectations are higher.
- **Proactively communicate delays.** For orders at risk of late delivery, send early notifications with updated estimates and compensation (discounts, free shipping) to lower the negative impact on reviews.
- **Monitor freight ratio on low-value orders.** Since freight consumes 44.7% of low-order-value purchases, consider offering free-shipping thresholds or bundling recommendations to reduce shipping cost sensitivity among smaller buyers.
- **Combine with geography analysis.** Earlier findings show customers are concentrated in the Southeast. Strengthening local warehousing and last-mile delivery in SP, RJ and MG can directly improve delivery earliness across the majority of orders and lift overall review scores.


**b)factors influencing delivery delay**

Order delays may be caused by two key dimensions: product size and geographic remoteness.
Here we consider products whose weight >10000g as big-size products; customers' address not in SP, RJ, MG, ES as remote regions.

| Factor | On-Time Orders | Delayed Orders |
|--------|---------------|----------------|
| Big-size products | 4.5% | 6.2% |
| Remote-area orders | 30.8% | 35.8% |

**Insights**:

- **Remote areas are the biggest source of delays.** Orders from remote regions account for 35.8% of all delayed orders, compared to 30.8% of on-time orders. This 5-percentage-point gap shows that geographic distance and limited logistics coverage are the primary drivers of late delivery. Customers in remote areas face longer transit routes and fewer distribution centers, making delays far more likely.
- **Big-size products are slightly more responsible for delay.** Large or heavy items account for 6.2% of delayed orders versus 4.5% of on-time orders. Big-size products require special handling, larger vehicles and more careful packaging, which adds complexity to the delivery chain and increases the chance of scheduling delays.
- **Remote area impact outweighs product size.** The gap between delayed and on-time orders is much larger for remote areas (+5.0 pp) than for big-size products (+1.7 pp). Geographic remoteness is therefore a stronger predictor of delay than product size.

**Recommendations**:

- **Expand warehouse and distribution center coverage in remote regions.** Since remote-area orders have the highest delay rate, adding local fulfillment centers in under-served states (e.g., northern and northeastern Brazil) would shorten transit distance and reduce late deliveries.
- **Set realistic delivery estimates for remote and big-size orders.** Instead of promising aggressive delivery times, provide conservative estimates that account for longer transit and handling. This manages customer expectations and reduces negative reviews even when delivery takes longer.
- **Optimize logistics for big-size products.** Partner with specialized freight carriers for big-size items, and improve packaging and loading processes to reduce handling delays.
- **Prioritize delay prevention in high-value remote orders.** Combine delivery delay data with order value: high-value orders going to remote areas carry both higher revenue risk and higher expectation. Flag these for extra tracking and proactive customer communication.

    
**c)order time periods**    
    
    
- **Cross Analysis**
  - cross-state shipment & low reviews
  - delivery delay & categories
  - RFM & categories  


 

## Key Business Insights
1. Most customers are one-time purchasers; platform repurchase rate is low with high customer churn risk.
2. Southeast Brazil (São Paulo, Rio de Janeiro) contributes most of platform orders and revenue.
3. Home, beauty and health-related categories generate the highest revenue.
4. Delivery delay has strong negative correlation with review scores; logistics timeliness is the core factor of customer satisfaction.

