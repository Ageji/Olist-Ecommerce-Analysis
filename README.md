# Olist-Ecommerce-Analysis

### Project Overview
Olist is a Brazilian e-commerce marketplace that connects small businesses to customers across Brazil. This project analyzes over 100,000 orders placed between 2016 and 2018 to uncover insights about sales performance, customer behavior, delivery operations and seller performance and to answer one simple question: what does the data tell us about how this business is really doing?

The analysis was carried out across four phases. The first phase focused on cleaning and preparing the raw data. The second explored sales trends and revenue patterns. The third used RFM analysis to segment customers based on how recently they bought, how often they bought and how much they spent. The fourth looked at delivery performance and how it connects to customer satisfaction.

The goal of this project is not just to produce charts  it is to tell a story with data and translate that story into real business recommendations that Olist could act on.

### Data Source
The dataset used in this project is the Olist Brazilian E-Commerce Public Dataset, freely available on Kaggle. It contains over 100,000 orders placed on the Olist marketplace between September 2016 and August 2018, spread across 9 CSV files covering orders, customers, products, sellers, payments, reviews and geolocation data.

### Tools Used
Python was the primary tool for this project, handling everything from data cleaning and transformation to analysis and visualization. Pandas was used for data manipulation, while Matplotlib and Seaborn were used to produce all the charts. The entire analysis was built and documented inside Jupyter Notebook, making it easy to follow the thought process behind every decision. All code and outputs are published on GitHub.

### Data Cleaning & Preparation
Real world data is never clean and the Olist dataset was no exception. Before a single insight could be drawn, the raw data had to go through a thorough cleaning process. Here is exactly what was tackled:
- The dataset came as 9 separate CSV files with no obvious way to connect them. The first task was understanding how they related to each other and what each one contained before anything else could happen.
- Several columns had missing data, most noticeably the delivery date columns. But this was not a data error  cancelled orders never get delivered so those dates are naturally empty. Understanding why data is missing is just as important as finding it.
- Every date column was stored as plain text. Converting them to proper datetime format was essential  without it, calculating delivery times  would have been completely impossible.
-  All 71 product categories were written in Portuguese. A translation table was merged in to convert every category to English. Three categories had no translation available and were manually mapped to make sure nothing was lost.
- States were stored as two letter codes like SP and RJ. Meaningful on their own but confusing on a chart. All 27 state codes were mapped to their full names so every visualisation could speak for itself.
- With all tables cleaned, they were joined into one master dataframe using order_id, customer_id, product_id and seller_id as connecting keys. The result was a single dataset with 115,000+ rows and 35 columns everything needed for analysis in one place.

  ### Exploratory Data Analysis
  EDA involves exploring the Olist E-Commerce dataset to answer these questions:
  ### Phase 1  Data Overview
- How many orders, customers, products and sellers does the dataset contain, and what time period does it cover?
- What is the breakdown of order statuses and how many orders were successfully delivered?
- Which product categories appear most frequently across all orders?
- What is the distribution of payment types used by customers?

### Phase 2  Sales & Revenue
- Which month and quarter recorded the highest revenue and order volume, and how did sales grow between 2016 and 2018?
- What are the top performing product categories by revenue and by order volume, and are the same categories leading in both?
- How does payment type influence average order value, and which payment method generates the most revenue?
- How do freight costs vary across different states, and which regions are paying the most to receive their orders?

### Phase 3 Customer Segmentation
- How are customers distributed across RFM segments based on recency, frequency and monetary value?
- Which customer segments contribute the most to total revenue and what percentage of total revenue does each segment represent?
- How does average spend, purchase frequency and days since last purchase vary across different customer segments?
- Which segments are at risk of churning and which ones show the most potential for growth?

### Phase 4  Delivery & Review Performance
- How does actual delivery time compare to estimated delivery time, and what percentage of orders are delivered late?
- How do late delivery rates vary across different customer states, and which regions are most affected?
- How does delivery time influence customer review scores, and does being late directly lead to lower ratings?
- What is the overall distribution of customer review scores across all delivered orders?
- How does seller performance vary in terms of review scores, delivery speed and revenue generated, and which sellers are consistently underperforming?

### Findings
### Phase 1 Data Overview
Out of 99,441 total orders in the dataset, 96,478 were successfully delivered representing 97% of all orders. A small number were cancelled (625), shipped but not yet delivered (1,107) or unavailable (609). Order volume grew steadily from September 2016 through 2018 with November 2017 recording the highest spike likely driven by Black Friday promotions. The top 3 most ordered product categories were bed_bath_table (9,417 orders), health_beauty (8,836 orders) and sports_leisure (7,720 orders). Credit card was by far the most dominant payment method at 73.9% of all transactions, followed by boleto at 19%, voucher at 5.6% and debit card at just 1.5%.

### Phase 2 Sales & Revenue
Revenue grew consistently from R$751,539 in Q1 2017 to a peak of R$2,922,665 in Q2 2018 nearly 4x growth in just over a year. Health & Beauty was the top revenue generating category at R$1,275,776 followed by Watches & Gifts at R$1,214,620 and Bed & Bath Table at R$1,092,461. While Bed & Bath Table led in order volume with 9,272 orders, Health & Beauty led in revenue  confirming that Health & Beauty products carry a significantly higher price point at an average of R$130 per item compared to R$92 for Bed & Bath Table. Credit card customers had the highest average order value at R$179, closely followed by boleto at R$176, while voucher customers spent the least at just R$65 per order. On the freight side, Paraíba recorded the highest average freight cost at R$43.59 followed by Roraima at R$43.09 and Rondônia at R$41.22 all remote states in the North and Northeast of Brazil far from where most sellers are concentrated.

### Phase 3 Customer Segmentation
The RFM analysis segmented 93,358 unique customers into 9 groups based on how recently they bought, how often they bought and how much they spent. At Risk customers generated the highest total revenue at R$4,264,036 (21.4% of total revenue) despite not having purchased recently making them the most urgent group to re-engage. Loyal Customers followed at R$3,826,935 (19.2%) and New Customers at R$3,062,988 (15.4%). Despite being one of the smallest segments with only 6,462 customers, Champions had the highest average spend at R$444 per customer and the shortest recency at just 91 days since their last purchase. The scatter plot of recency vs monetary value confirmed a clear pattern Champions and Loyal Customers clustered in the top left with high spend and recent purchases, while Lost customers sat at the far right with no recent activity for up to 700 days. Across all segments, average purchase frequency was between 1.0 and 1.18 orders per customer revealing that the vast majority of Olist customers buy once and never return regardless of their segment.

### Phase 4 Delivery & Review Performance
Out of 115,104 delivered orders, 106,960 (92.9%) arrived on time or early while 8,144 (7.1%) were delivered late. Olist consistently delivered faster than promised actual delivery averaged 11.8 days while estimated delivery averaged 23.3 days, meaning most customers received their orders roughly 12 days earlier than expected. However late delivery rates varied significantly by state. Alagoas recorded the highest late delivery rate at 26.2% followed by Maranhão at 22.2% and Sergipe at 17.6%  all northeastern states with longer distances from seller hubs. The analysis confirmed a direct and strong relationship between delivery performance and customer satisfaction. Orders with a review score of 1 had an average delivery time of 18.22 days and a late rate of 30%, while orders rated 5 had an average delivery time of just 10.12 days and a late rate of only 2% making delivery speed the single biggest driver of customer satisfaction on the platform. Seller performance also varied widely. The top sellers maintained perfect or near perfect review scores of 5.00 with 0% late delivery rates, while the worst performing sellers had review scores as low as 1.93 with late rates as high as 64%. The average seller review score across the platform was 4.13 out of 5.

### Recommendations

Based on the analysis, here are five recommendations Olist should act on:

- Win back At Risk customers immediately.This segment holds R$4,264,036 in pastrevenue and has not purchased recently. A targeted email campaign with a personalized discount or product recommendation could recover a significant portion of this revenue before these customers move to the Lost segment permanently.

- Build a loyalty program to fix the retention problem. With average purchase frequency sitting at just 1.0 to 1.18 orders per customer across all segments, Olist
is heavily dependent on acquiring new customers rather than retaining existing ones. A points based loyalty program or exclusive returning customer discounts would encourage repeat purchases and improve long term revenue stability.

- Improve logistics in Alagoas, Maranhão and Sergipe. These three states recorded the highest late delivery rates at 26.2%, 22.2% and 17.6% respectively. Olist should explore regional fulfilment centres or partnerships with local logistics providers in the North and Northeast to close the delivery gap between these states and the rest of Brazil.

- Flag and support underperforming sellers. The worst performing sellers had review scores as low as 1.93 and late delivery rates as high as 64%. These sellers are
directly damaging the platform's reputation and customer satisfaction. Olist should introduce minimum performance thresholds and provide training or support to struggling sellers before considering removal from the platform.

- Protect and reward Champions. With only 6,462 customers but an average spend of R$444 each, Champions are the most valuable customers on the platform. Olist should invest in keeping this group engaged through early access to new products, exclusive offers and personalised communication to prevent them from slipping into the At Risk segment.
