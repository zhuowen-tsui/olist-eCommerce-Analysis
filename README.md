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

**1. Hourly Distribution**
Sales are lowest in the early morning and peak during daytime working hours.

| Hour Range | Avg. Sales/Hour | Pattern |
|------------|-----------------|---------|
| 00:00–06:00 | 187–2,378 | Very low (midnight to early morning) |
| 07:00–09:00 | 1,223–4,735 | Rapid ramp-up |
| 10:00–12:00 | 5,947–6,528 | Entering peak |
| 13:00–17:00 | 6,397–6,628 | **Peak window** (highest volume around 11:00 and 16:00) |
| 18:00–21:00 | 5,731–6,177 | Sustained high |
| 22:00–23:00 | 4,094–5,792 | Gradual decline |

**Insight:**
- Order volume is extremely low between midnight and 6:00 AM, with the trough at 4:00–5:00 AM (fewer than 200 orders).
- Shopping activity rises steadily from 7:00 AM and stabilizes at a high plateau from 10:00 AM through 9:00 PM.
- The absolute peak occurs around 11:00 AM (6,528 orders) and 4:00 PM (6,628 orders), suggesting customers browse during mid-morning and afternoon breaks.

**2. Weekday vs Weekend**

| Period | Total Orders | Total Revenue (BRL) | Avg. Orders/Day | Avg. Revenue/Day (BRL) |
|--------|-------------|---------------------|-----------------|------------------------|
| Weekday | 75,965 | 10,498,346 | 15,193 | 2,099,669 |
| Weekend | 22,701 | 3,093,297 | 11,351 | 1,546,649 |

**Insight:**
- Weekdays generate ~34% more orders per day than weekends (15,193 vs. 11,351).
- This is consistent with Brazilian e-commerce behavior: customers predominantly shop on weekdays during work or study breaks rather than on weekends.
- Revenue per day also follows the same pattern, confirming that weekday shopping is the primary revenue engine.

3. Monthly Seasonality

| Month | Orders | Revenue (BRL) |
|-------|--------|---------------|
| Jan | 8,009 | 1,070,343 |
| Feb | 8,427 | 1,091,482 |
| Mar | 9,829 | 1,357,558 |
| Apr | 9,325 | 1,356,575 |
| May | 10,513 | 1,502,589 |
| Jun | 9,377 | 1,298,163 |
| Jul | 10,242 | 1,393,539 |
| Aug | 10,745 | 1,428,658 |
| Sep* | 4,247 | 624,814 |
| Oct* | 4,876 | 713,727 |
| Nov | 7,451 | 1,010,271 |
| Dec | 5,625 | 743,925 |

*\*Note: September and October figures are partial-month data due to dataset coverage.*

**Insight**:

- Orders grow steadily from January to a peak in May (10,513 orders) and August (10,745 orders), which are the strongest months.
- November and December show a decline, though this may partially reflect dataset completeness rather than true seasonal weakness.
- The first half of the year (March–August) consistently outperforms the end of the year, indicating a H1 seasonal peak for the platform.

**Recommendations**:

- **Time push notifications and promotions around 10:00 AM–5:00 PM.** This is the highest-conversion window. Sending discount alerts, email campaigns and app notifications during these hours maximizes click-through and order volume.
- **Schedule logistics and customer service staffing on weekdays.** Since weekdays carry ~34% more daily orders, warehouse picking, packing and delivery dispatch should be fully staffed Monday–Friday, with lighter weekend operations.
- **Plan major promotions for March–August.** This H1 window shows consistently high demand and revenue. Align seasonal sales events, inventory restocking and marketing campaigns with this peak period.
- **Avoid heavy promotion spend in early morning hours (0:00–6:00).** Conversion is at its lowest; shift marketing budget to the daytime peak window instead.

    
**4.Cross Analysis**
**dashboard link:https://public.tableau.com/views/olist_Ecommerce_cross_analysis/crossanalysis**

**1)cross-state shipment & low reviews**

Products shipped across different states face longer transit routes, higher handling complexity and greater risk of damage or delay. This analysis identifies which product categories suffer the highest low-review rates, and links the pattern to cross-state logistics challenges.

**Product Categories with the Highest Low-Review Ratio**

| Rank | Category (PT) | English Meaning | Low Review Ratio |
|------|---------------|----------------|-----------------|
| 1 | portateis_cozinha_e_preparadores_de_alimentos | Portable kitchen & food prep appliances | 57.1% |
| 2 | artigos_de_festas | Party supplies | 51.7% |
| 3 | pc_gamer | Gaming PCs | 50.0% |
| 4 | moveis_colchao_e_estofado | Mattresses & sofas | 50.0% |
| 5 | seguros_e_servicos | Insurance & services | 50.0% |
| 6 | telefonia_fixa | Landline phones | 49.3% |
| 7 | moveis_escritorio | Office furniture | 49.0% |
| 8 | casa_conforto_2 | Home comfort | 47.1% |

**Product Categories with the Lowest Low-Review Ratio**

| Rank | Category (PT) | English Meaning | Low Review Ratio |
|------|---------------|----------------|-----------------|
| 1 | flores | Flowers | 9.5% |
| 2 | construcao_ferramentas_ferramentas | Construction tools | 10.5% |
| 3 | livros_interesse_geral | General interest books | 12.4% |
| 4 | cds_dvds_musicais | CDs & music DVDs | 12.5% |
| 5 | fashion_roupa_infanto_juvenil | Children's clothing | 12.5% |
| 6 | fashion_calcados | Shoes | 16.1% |
| 7 | malas_acessorios | Luggage & accessories | 17.7% |
| 8 | eletroportateis | Small home appliances | 19.6% |

**Insights**:

- **Bulky, fragile and high-electronics categories dominate the low-review list.** The top categories with the worst review scores — portable kitchen appliances, gaming PCs, mattresses/sofas, office furniture and landline phones — are all physically large, heavy or electronic. These products are highly susceptible to transit damage, require special handling, and are typically shipped across long distances (cross-state), increasing the chance of delayed delivery or product damage.
- **Small, light, non-fragile categories have the lowest dissatisfaction.** Books, shoes, luggage, flowers and general-interest products have low low-review ratios (9.5%–17.7%). These items are compact, durable and less prone to shipping damage, regardless of distance.
- **Cross-state shipping amplifies the risk for fragile goods.** When bulky or electronic products travel across state borders, they face multiple handovers, longer transit times and rougher handling. This directly links back to the delivery-delay analysis: remote-area and cross-state orders are already more likely to be late, and when the product itself is fragile, dissatisfaction compounds.
- **Party supplies and insurance/services are outliers.** Categories like party supplies (51.7%) and insurance/services (50.0%) are not physical shipping-heavy products, yet they show high low-review rates. This suggests dissatisfaction in these categories is driven by product quality, expectation mismatch or service issues rather than logistics alone.

**Recommendations**:

- **Improve packaging for high-risk cross-state categories.** For furniture, mattresses, kitchen appliances and gaming PCs, invest in stronger packaging materials, foam protection and fragile-item labeling to reduce in-transit damage.
- **Prioritize local fulfillment for bulky items.** Store high-return-bulky products in regional warehouses closer to major customer hubs (SP, RJ, MG) to shorten cross-state shipping distance and lower damage risk.
- **Set realistic delivery expectations for cross-state orders.** Display longer delivery estimates for inter-state shipments of large/fragile items, so customers are not surprised by extended transit times.


**2)delivery delay & categories**

 ### 🚚 Delivery Delay by Product Category
As different categories sell different kinds of products, it may influence supplementary services. Here we would like to discover which categories suffer the longest delivery delays, and links the pattern to product type and logistics characteristics.

**Top 10 Categories with the Longest Average Delay**

| Rank | Category (PT) | English Meaning | Avg. Delay (days) |
|------|---------------|----------------|-------------------|
| 1 | seguros_e_servicos | Insurance & services | 17.0 |
| 2 | cds_dvds_musicais | CDs & music DVDs | 16.9 |
| 3 | la_cuisine | La Cuisine (kitchen brand) | 16.4 |
| 4 | fashion_roupa_infanto_juvenil | Children's clothing | 15.7 |
| 5 | artigos_de_festas | Party supplies | 15.1 |
| 6 | fashion_calcados | Shoes | 14.8 |
| 7 | telefonia_fixa | Landline phones | 14.7 |
| 8 | market_place | Marketplace items | 14.6 |
| 9 | musica | Music | 14.3 |
| 10 | climatizacao | Air conditioning | 14.2 |

**Top 10 Categories with the Shortest Average Delay**

| Rank | Category (PT) | English Meaning | Avg. Delay (days) |
|------|---------------|----------------|-------------------|
| 1 | artes_e_artesanato | Arts & crafts | 6.8 |
| 2 | moveis_colchao_e_estofado | Mattresses & sofas | 7.2 |
| 3 | casa_conforto_2 | Home comfort | 8.4 |
| 4 | portateis_cozinha_e_preparadores_de_alimentos | Kitchen appliances | 9.5 |
| 5 | pc_gamer | Gaming PCs | 9.6 |
| 6 | casa_conforto | Home comfort | 9.8 |
| 7 | alimentos | Food | 9.9 |
| 8 | audio | Audio equipment | 10.1 |
| 9 | fashion_underwear_e_moda_praia | Underwear & beachwear | 10.9 |
| 10 | eletronicos | Electronics | 11.1 |

**Insights**:

- **Wide delay gap across categories.** Average delivery delay ranges from 6.8 days (arts & crafts) to 17.0 days (insurance & services) — a gap of more than 2.5×. This indicates that product category is a significant factor in delivery speed.
- **Surprisingly, bulky furniture delivers faster than small lightweight goods.** Mattresses & sofas (7.2 days) and other furniture categories rank among the fastest-delivering products. This is counterintuitive but likely because bulky items use dedicated freight carriers with scheduled routes, whereas small items (clothing, media) may be consolidated and wait for batch shipping.
- **Apparel and media categories are the slowest.** Children's clothing (15.7), shoes (14.8), CDs/DVDs (16.9) and music (14.3) all show long delays. These are typically lightweight items shipped through regular postal/courier channels that handle high volume but slower sorting.
- **Insurance & services have the longest "delay" (17.0 days).** As a non-physical service category, this may reflect processing time for policy issuance or service activation rather than physical shipping.

**Recommendations**:

- **Investigate logistics for slow apparel and media categories.** Children's clothing, shoes and CDs/DVDs take 15–17 days on average. Review the last-mile partners for these categories and consider switching to faster courier services or local stocking.
- **Leverage furniture logistics as a model.** Mattresses and sofas deliver in only 7.2 days despite being bulky. Study the dedicated freight model used for furniture and apply similar practices to slow categories.
- **Set category-specific delivery estimates.** Instead of a generic delivery promise, show customers a more accurate estimate based on product category. This manages expectations and reduces negative reviews caused by over-promising.


**3)RFM & categories**

Cross-analyze RFM customer segments with their most frequently purchased product categories. It reveals what each customer group actually buys, so that marketing and product strategies can be tailored to segment-specific preferences.

**Top Category by RFM Segment**

| RFM Segment | Top Product Category | English Meaning | Customer Count |
|-------------|---------------------|----------------|----------------|
| Important Client | telefonia | Telecommunications / phones | 24 |
| Retaining Client | utilidades_domesticas | Household utilities | 12 |
| Losing Client | informatica_acessorios | Computer accessories | 22 |
| Potential Client | esporte_lazer | Sports & leisure | 24 |
| New Client | beleza_saude | Beauty & health | 1,171 |
| Ordinary Client | cama_mesa_banho | Bed, table & bath (textiles) | 154 |
| Lost Client | cama_mesa_banho | Bed, table & bath (textiles) | 9,949 |

**Insights & recommendations**:

Different customer groups prefer different product types, confirming that RFM is not just an academic model but aligns with actual shopping behavior.
- **New customers overwhelmingly enter through Beauty & Health.** The largest new-client segment (1,171 customers) shops mainly in `beleza_saude` (beauty & health). This suggests beauty and health products act as the platform's primary customer-acquisition way — affordable, low-risk entry-level items that attract first-time buyers.
- **High-value Important Clients prefer telecommunications.** The 24 important clients (high recency, frequency and monetary) buy mainly `telefonia` (phones/electronics). This is a higher-price-point category, consistent with these customers being high spenders who make repeated large purchases. Offer exclusive phone/accessory bundles, extended warranties and early access to new tech products to retain their loyalty.
- **Sports & Leisure attracts frequent but low-spending Potential Clients.** `esporte_lazer` is the top category for potential clients (high frequency but low monetary value). These customers buy often but spend little per order, suggesting they are deal-sensitive browsers who could be upsold to higher-priced items. Send win-back coupons for new home-textile arrivals or related categories (furniture, decor) to trigger a second purchase.
- **Bed, Table & Bath (textiles) dominates both Ordinary and Lost clients.** `cama_mesa_banho` is the #1 category for the massive lost-client group (9,949) and the ordinary-client group (154). This mass-market home-textiles category attracts huge volume but low loyalty — most buyers purchase once and never return.
- **Losing Clients (formerly frequent, now inactive) favored Computer Accessories.** `informatica_acessorios` is the top category for clients who used to buy frequently but have gone quiet. This suggests the electronics/accessories segment may have had better repeat-purchase potential in the past, but those relationships have now cooled.
- **Cross-sell across segments.** For example, New Clients entering through Beauty & Health could be recommended Household Utilities (the top category for Retaining Clients), which may increase their order frequency and move them up the RFM ladder.


## Overall Key Business Insights
1. Most customers are one-time purchasers; platform repurchase rate is low with high customer churn risk.
2. Southeast Brazil (São Paulo, Rio de Janeiro) contributes most of platform orders and revenue.
3. Home, beauty and health-related categories generate the highest revenue.
4. Delivery delay has strong negative correlation with review scores; logistics timeliness is the core factor of customer satisfaction.

