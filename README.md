# Customer-Segmentation-using-RFM-Analysis

#1. Data Preprocessing:

1.1 Importing the Dataset:

The initial phase involved importing the eCommerce dataset, which was retrieved from
the provided Kaggle link. The dataset was loaded into a panda DataFrame, allowing for
efficient explora'on and manipula'on of the data.

1.2 Handling Missing Values:

1.2.1 Description Column (1454 missing values):

The 'Description' column had 1454 missing values. AIer careful considera'on, it was
decided to retain these missing values in the dataset. Since our focus is on RFM analysis
for customer segmenta'on, the absence of a product descrip'on for certain entries is not
deemed critical.

1.2.2 CustomerID Column (135,080 missing values):

The 'CustomerID' column, crucial for customer identification in RFM analysis, had 135,080
missing values. To ensure the integrity of customer-centric analysis, rows with missing
'CustomerID' entries were removed from the dataset. This approach allows us to
concentrate on customers with identifiable information.

1.3 Converting Data Types:

1.3.1 InvoiceDate Column:

The 'InvoiceDate' column, originally in object format, was converted to the
datetime64 data type. This conversion facilitates seamless handling of date-related
calcula'ons, ensuring accurate recency calculations for RFM analysis.

1.3.2 CustomerID Column:

The 'CustomerID' column, initially represented as floa'ng-point numbers, was converted
to the int64 data type. This conversion aligns with standard prac'ces for customer
iden'fica'on and supports compa'bility with subsequent calcula'ons.

#3. RFM Calculation:
   
In this sec'on, we further refined the RFM metrics by incorpora'ng the most recent
purchase date and addi'onal transac'on-related metrics.

2.1 Recent Purchase Date (Recency - R):

To calculate the recency (R) of each customer, we first converted the 'InvoiceDate' to the
'InvoiceDay' column, represen'ng the date of each transac'on. The maximum
'InvoiceDay' was then iden'fied as the most recent purchase date across all customers.
The 'Days_Since_Last_Purchase' metric was computed by subtrac'ng the most recent
date from each customer's last purchase date.

2.2 Total Transac)ons (Frequency - F):

To gauge the frequency (F) of customer transac'ons, we determined the total number of
unique invoices ('Total_Transac'ons') for each customer. This metric quan'fies how oIen
a customer engages in transac'ons with the business.

2.3 Total Products Purchased:

To enrich our understanding of customer behavior, we introduced the
'Total_Products_Purchased' metric, represen'ng the total quan'ty of unique products
purchased by each customer. This provides insights into the diversity and breadth of a
customer's product preferences.

2.4 Resul)ng RFM Metrics:

The resul'ng dataset now includes the following RFM metrics:
• CustomerID: Unique iden'fier for each customer.
• Days_Since_Last_Purchase: The recency of each customer's last purchase in terms of
days.
• Total_Transac'ons: The total number of unique transac'ons made by each customer.
• Total_Products_Purchased: The total quan'ty of unique products purchased by each
customer.

These metrics form a more comprehensive view of customer behavior, capturing recency,
frequency, and product diversity. The subsequent sec'ons will leverage these refined
RFM metrics for customer segmenta'on, providing valuable insights for targeted
marke'ng and engagement strategies.

3. RFM Segmentation:
   
In this sec'on, we assigned RFM scores to each customer based on quar'les, enabling the
crea'on of a single RFM score for comprehensive customer segmenta'on.

3.1 Recency Score (R):

Methodology:
The most recent purchase date for each customer was determined, and the
'Days_Since_Last_Purchase' metric was calculated.
Quar'les were applied to 'Days_Since_Last_Purchase' to create Recency Scores, with
lower scores indica'ng more recent purchases.

3.2 Frequency Score (F):

Methodology:

Total transac'ons ('Total_Transac'ons') for each customer were calculated, and
frequency ranks were assigned based on transac'on counts.
Quar'les were applied to the frequency ranks to create Frequency Scores, with higher
scores indica'ng more frequent transac'ons.

3.3 Monetary Score (M):

Methodology:

Totals spend ('Total_Spend') for each customer was calculated, and quar'les were
applied to create Monetary Scores, with higher scores indica'ng higher monetary
contribu'ons.

3.4 Crea)ng RFM Score:

Methodology:

The Recency, Frequency, and Monetary Scores were combined to create a single RFM
score for each customer, providing a holis'c view of their engagement and contribu'on
to the business.

3.5 Resul)ng RFM Segmenta)on:

The resul'ng dataset now includes the following RFM metrics and segmenta'on:
• CustomerID: Unique iden'fier for each customer.
• Recency_Score: Recency score based on quar'les.
• Frequency_Score: Frequency score based on quar'les.
• Monetary_Score: Monetary score based on quar'les.
• RFM_Score: Combined RFM score, indica'ng the overall engagement and value
contribu'on of each customer.

#4. Customer Segmenta9on:
   
In this sec'on, we u'lized clustering techniques, specifically K-Means clustering, to
segment customers based on their RFM scores. The objec've was to uncover meaningful
groups that share similar characteris'cs, aiding in targeted marke'ng and engagement
strategies.

4.1 Data Scaling:

Prior to clustering, the RFM scores (Recency, Frequency, and Monetary) were
standardized using the StandardScaler. Standardiza'on ensures that all features
contribute equally to the clustering process, preven'ng any metric from domina'ng the
results due to differences in scale.

4.2 Identifying Op)mal Number of Clusters:

To determine the op'mal number of clusters, the Elbow Method was employed. The
Elbow Method involves fidng the K-Means algorithm with a range of cluster numbers and
plodng the Within-Cluster Sum of Squares (WCSS) against the number of clusters. The
"elbow" in the plot signifies the op'mal number of clusters, where further par''oning
offers diminishing returns.

4.3 K-Means Clustering:

Based on the Elbow Method, a specific number of clusters (k) was selected. In this case, k
= 4 was deemed appropriate for segmen'ng the customers.
The K-Means algorithm was then applied to the standardized RFM scores, resul'ng in the
assignment of each customer to a specific cluster. The 'Cluster' column in the dataset
indicates the segment to which each customer belongs.

4.4 Resul)ng Customer Segmentation:

The resul'ng dataset now includes the 'Cluster' column, providing informa'on about the
segment to which each customer belongs. These segments represent groups of customers
with similar RFM characteris'cs.
CustomerID ... Cluster
0 12346 ... 2
1 12347 ... 3
2 12348 ... 0
3 12349 ... 1
4 12350 ... 2
... ... ... ...
4367 18280 ... 2
4368 18281 ... 2
4369 18282 ... 3
4370 18283 ... 3
4371 18287 ... 1

4.5 Visualizing the Clusters:

The Elbow Method plot was instrumental in determining the op'mal number of clusters.
By selec'ng an appropriate number of clusters, we ensure that each segment is dis'nct
and meaningful, providing valuable insights for targeted marke'ng strategies.

#5. Segment Profiling:
    
In this sec'on, we analyze and profile each customer segment based on the K-Means
clustering results. We describe the characteris'cs of customers in each segment,
including their RFM scores and any other relevant ajributes.

5.1 Segment 0:

Characteris'cs:

• Recency (R): High recency scores, indica'ng recent purchases.
• Frequency (F): Moderate frequency scores.
• Monetary (M): Moderate monetary scores.

Recommenda'ons:

• Offer exclusive loyalty programs to encourage purchases and increase frequency.
• Send personalized product recommenda'ons based on searching pajerns and
previous purchases with special offers to tempt them back.
• Run email or SMS campaigns to keep them connected with the brand.

5.2 Segment 1:

Characteris'cs:

• Recency (R): Moderate recency scores.
• Frequency (F): High frequency scores, indica'ng loyal customers.
• Monetary (M): High monetary scores.

Recommenda'ons:

• Recognize and reward their loyalty with member points or exclusive access to new
products and events.
• Suggest complementary products to increase their order value.
• Ask for their feedback on products purchased and services to further tailor your
offerings.

5.3 Segment 2:

Characteris'cs:

• Recency (R): Low recency scores.
• Frequency (F): Low to moderate frequency scores.
• Monetary (M): Low to moderate monetary scores.

Recommenda'ons:

• Recommend higher-value products or bundles to increase their spend.
• Create promo'ons for limited 'me offers to encourage more frequent purchases.
• Share content that highlights the benefits of your products to boost their perceived
value.

5.4 Segment 3:

Characteris'cs:

• Recency (R): Moderate to high recency scores.
• Frequency (F): Moderate frequency scores.
• Monetary (M): Moderate to high monetary scores.

Recommenda'ons:

• Send targeted campaigns with ajrac've offers to re-engage them.
• Iden'fy the reasons for their non-purchase and develop strategies to win them back.
• Ask for feedback and work on improving aspects that pushed them away from
purchasing.
These segment profiles and recommenda'ons provide ac'onable insights for tailoring
marke'ng strategies to each group's unique characteris'cs and behaviors.

#6. Marke9ng Recommenda9ons:

In this sec'on, we provide ac'onable marke'ng recommenda'ons for each customer
segment. These recommenda'ons are tailored to improve customer reten'on and
maximize revenue by addressing the unique characteris'cs and behaviors of each group.

6.1 High-Value Customers:

Recommenda'ons:

• Reten'on: Focus on retaining these customers through loyalty programs and exclusive
offers.
• Upsell: Iden'fy complementary products and offer bundle deals to increase sales.

6.2 Poten)al High-Value Customers:

Recommenda'ons:

• Promo'ons: Offer incen'ves to encourage addi'onal purchases and discounts on
related products.
• Personaliza'on: Use purchase history for personalized product recommenda'ons.

6.3 Low-Frequency, High-Value Customers:

Recommenda'ons:

• Win-Back Campaigns: Target inac've customers with special promo'ons to reac'vate
them.
• Subscrip'on Models: Introduce subscrip'on services to ensure steady revenue.

6.4 Low-Value Customers:

Recommenda'ons:

• Customer Educa'on: Provide informa've content to help customers understand
product value.
• Reac'va'on Campaigns: Create reac'va'on campaigns with exclusive offers.

6.5 General Recommenda)ons:

For clusters not explicitly men'oned, general recommenda'ons include:
• Collect customer feedback: Understand customer preferences and pain points.
• Conduct A/B tes'ng: Con'nuously op'mize marke'ng strategies based on customer
responses.

These targeted recommenda'ons align with the specific needs and behaviors of each
customer segment, offering a strategic approach for maximizing customer engagement,
reten'on, and revenue.

#7. Visualization:

7.1 RFM Distribution:

Recency Distribution:

The Recency Distribu'on chart depicts the distribu'on of days since the last purchase
across customers. The peak around 0 indicates a group of customers who made recent
purchases, while the tail shows customers with less recent transac'ons. Understanding
recency is crucial for iden'fying ac've and poten'ally lapsed customers.

Frequency Distribu'on:

The Frequency Distribu'on chart illustrates the distribu'on of the total number of
transac'ons for each customer. Peaks at higher frequencies indicate loyal and engaged
customers, while the tail represents customers with fewer transac'ons. This insight helps
in iden'fying the core customer base and tailoring strategies for different engagement
levels.

Monetary Distribu'on:

The Monetary Distribu'on chart showcases the distribu'on of total spend by customers.
Peaks at higher spend levels indicate high-value customers, while the tail represents
customers with lower monetary contribu'ons. Analyzing monetary distribu'on aids in
iden'fying customers with significant value and tailoring strategies to maximize revenue.

Find The Solu@ons:

1. Data Overview:
Size of the Dataset:
The dataset contains 401,604 rows and 9 columns.
Column Descrip)ons:
• InvoiceNo: Unique iden'fier for each transac'on.
• StockCode: Product code for items sold.
• Descrip'on: Descrip'on of the product.
• Quan'ty: Quan'ty of items purchased (nega've values indicate returns).
• InvoiceDate: Date and 'me of the transac'on.
• UnitPrice: Price per unit of the product.
• CustomerID: Unique iden'fier for each customer.
• Country: Country where the customer is located.
• Total_Spend: Total amount spent in a transac'on (calculated as Quan'ty * UnitPrice).
Time Period Covered:
The dataset covers transac'ons from December 1, 2010, at 08:26:00 to December 9,
2011, at 12:50:00.
2. Customer Analysis:
Number of Unique Customers:
The dataset encompasses transac'ons from a diverse set of 4,372 unique customers, each
iden'fied by a dis'nct CustomerID. This metric serves as a cri'cal indicator of the
dataset's coverage and represents the founda'on for subsequent customer-centric
analyses.
Distribu)on of Orders per Customer:
The distribu'on of orders per customer serves as a pivotal insight into the purchasing
behavior of the customer base. This metric elucidates the spectrum of customer
engagement, ranging from those with frequent and consistent orders to those with
sporadic and infrequent transac'ons.
Top 5 Customers with the Most Purchases by Order Count:
• Customer 17841: This customer has exhibited remarkable engagement, contribu'ng
a substan'al 7,812 orders. This signifies consistent patronage and frequent
interac'ons with the business.
• Customer 14911: Ranking second with 5,898 orders, this customer is another
significant contributor to the order count, indica'ng sustained engagement.
• Customer 14096: With 5,128 orders, this customer secures the third posi'on,
demonstra'ng a substan'al and consistent history of transac'ons.
• Customer 12748: Placing fourth with 4,459 orders, this customer has made a
considerable number of purchases, showcasing notable engagement.
• Customer 14606: Comple'ng the top five with 2,759 orders, this customer represents
a segment of the customer base with consistent but compara'vely fewer transac'ons.
3. Product Analysis:
Top 10 Most Frequently Purchased Products:
The list below represents the top 10 most frequently purchased products, along with the
respec've counts of purchases:
• WHITE HANGING HEART T-LIGHT HOLDER: 2058 purchases
• REGENCY CAKESTAND 3 TIER: 1894 purchases
• JUMBO BAG RED RETROSPOT: 1659 purchases
• PARTY BUNTING: 1409 purchases
• ASSORTED COLOUR BIRD ORNAMENT: 1405 purchases
• LUNCH BAG RED RETROSPOT: 1345 purchases
• SET OF 3 CAKE TINS PANTRY DESIGN: 1224 purchases
• POSTAGE: 1196 purchases
• LUNCH BAG BLACK SKULL: 1099 purchases
• PACK OF 72 RETROSPOT CAKE CASES: 1062 purchases
A pie chart visually represents the distribu'on of purchases among the top 10 products
by descrip'on. This graphic provides a clear illustra'on of the rela've popularity of each
product in the dataset.
Average Price of Products:
The average price of products in the dataset is approximately $3.47. This metric provides
an overview of the typical unit price across all products, aiding in understanding the
general pricing structure.
Product Category Genera)ng the Highest Revenue:
The product category with the highest revenue is iden'fied by examining the StockCode
associated with the maximum total revenue. In this dataset, the product category
genera'ng the highest revenue is REGENCY CAKESTAND 3 TIER. The total revenue
ajributed to this product category is approximately $132,567.70.
4. Time Analysis:
Orders by Day of the Week:
The bar chart illustrates the distribu'on of orders across different days of the week. The
analysis revealed that:
Busiest Day: The dataset indicates that most orders are placed on Thursday. This insight
can influence marke'ng and promo'onal strategies, ensuring op'mal resource alloca'on
on peak ordering days.
Orders by Hour of the Day:
The line chart visualizes the number of orders at different hours of the day. Key
observa'ons include:
Peak Hours: The graph indicates that the highest number of orders occurs during the
morning and early a^ernoon, with a slight decrease towards the evening. Understanding
peak ordering 'mes is crucial for staffing and resource management.
Monthly Order Trends:
The line chart displays the monthly trends in the number of orders. Key findings include:
Seasonal Pa_erns: The dataset exhibits some seasonal trends, with varia'ons in order
volumes across different months. There is a significant increase in the month of
November. And a significant drop in the month of December. Iden'fying seasonal
pajerns is essen'al for an'cipa'ng demand fluctua'ons and adjus'ng inventory levels.
Average Order Processing Time:
The average order processing 'me is calculated by measuring the 'me elapsed between
consecu've orders for each customer. The calculated average order processing 'me is
approximately 35.32 hours. This metric provides insights into the efficiency of the order
fulfillment process.
5. Geographical Analysis:
Top 5 Countries by Orders:
The bar chart on the leI side displays the top 5 countries with the highest number of
orders. Key observa'ons include:
United Kingdom Dominance: The United Kingdom (UK) stands out as the country with
the highest number of orders. This insight highlights the significance of the UK market in
terms of order volume.
Average Order Value by Country:
The bar chart on the right side illustrates the average order value for each country.
Notable findings include:
Varied Average Order Values: The average order values are distributed across countries,
with some exhibi'ng higher average values and others lower. This varia'on may be
influenced by factors such as consumer purchasing power, product pricing, and cultural
preferences.
Correla)on Analysis:
The correla'on analysis aims to determine the rela'onship between the country of the
customer and the average order value. The calculated correla'on value is nan.
This geographical analysis aids in recognizing key markets, understanding spending
pajerns across countries, and iden'fying opportuni'es for targeted marke'ng and
pricing adjustments.
6. Payment Analysis:
Most Common Payment Methods:
The analysis reveals the most common payment methods used by customers:
• Debit Card: Number of Transac'ons: 101,658
• Credit Card: Number of Transac'ons: 101,415
• Apple Pay: Number of Transac'ons: 101,236
• Cash: Number of Transac'ons: 101,131
This informa'on provides insights into the preferred payment methods among
customers, aiding the company in op'mizing payment processing and offering targeted
payment op'ons.
Rela)onship Between Payment Method and Order Amount:
A box plot is u'lized to visualize the rela'onship between payment methods and the total
spend (order amount). Box plots provide a clear representa'on of the distribu'on, central
tendency, and poten'al outliers for different payment methods.
Box Plot Insights:
The box plot visually represents the spread and distribu'on of total spend for each
payment method. It provides a quick overview of the central tendency, variability, and
poten'al outliers in the data. The analysis of the box plot can uncover pajerns, trends,
and poten'al areas for further inves'ga'on. This payment analysis contributes valuable
insights to the company's understanding of customer payment preferences and
behaviors, suppor'ng strategic decisions to improve overall customer sa'sfac'on and
opera'onal efficiency.
7. Customer Behavior:
Average Dura)on of Customer Ac)vity:
The average dura'on of customer ac'vity is calculated by determining the 'me span
between a customer's first and last purchase. The calculated average dura'on is
approximately 133.39 days. This metric provides insights into how long, on average,
customers remain ac've in terms of making purchases.
Customer Segmenta)on Based on Purchase Behavior:
Customer segmenta'on is performed based on two key metrics: recency and frequency.
• Recency: The "Recency" column represents the number of days since the customer's
last purchase. The values range from 1 day to 325 days, indica'ng varying recency
levels among customers.
• Frequency: The "Frequency" column denotes the total number of transac'ons or
purchases made by each customer. Frequencies range from 2 to 721, reflec'ng diverse
purchasing behaviors.
Segment Thresholds and Assignment:
Segmenta'on involves defining thresholds for recency and frequency, and customers are
then categorized into segments based on these thresholds.
• Recency Threshold: The median value of recency is used as the threshold.
• Frequency Threshold: The median value of frequency is u'lized as the threshold.
Customer Segments:
Customers are assigned to two segments based on the defined thresholds:
• High Ac'vity Segment: Customers with recency values below or equal to the recency
threshold and frequency values above the frequency threshold are classified as having
high ac'vity.
• Low Ac'vity Segment: Customers not mee'ng the criteria for the high ac'vity
segment are categorized as having low ac'vity.
This analysis provides a comprehensive understanding of customer behavior, allowing
businesses to adapt their strategies to different customer segments and maximize overall
customer engagement and sa'sfac'on.
8. Returns and Refunds:
Percentage of Orders with Returns or Refunds:
The percentage of orders that have experienced returns or refunds is calculated to be
2.21%. This metric provides an overview of the overall rate of returns or refunds within
the dataset.
Correla)on Between Product Category and Likelihood of Returns:
The likelihood of returns is explored by examining the percentage of returns for each
product category. Here are a few key points:
• Product Categories: The product categories are represented by their descrip'ons.
• Percentage of Returns: For each product category, the percentage of returns is
calculated. This indicates the propor'on of orders within a specific category that
resulted in returns.
Percentage of Returns by Product Category:
Descrip'on
4 PURPLE FLOCK DINNER CANDLES NaN
50'S CHRISTMAS GIFT BAG LARGE 0.909091
DOLLY GIRL BEAKER 1.459854
I LOVE LONDON MINI BACKPACK NaN
I LOVE LONDON MINI RUCKSACK NaN
……..
ZINC T-LIGHT HOLDER STARS SMALL 1.244813
ZINC TOP 2 DOOR WOODEN SHELF 18.181818
ZINC WILLIE WINKIE CANDLE STICK 0.520833
ZINC WIRE KITCHEN ORGANISER NaN
ZINC WIRE SWEETHEART LETTER TRAY NaN
9. Profitability Analysis:
Total Profit Generated:
The total profit generated by the company during the dataset's period is calculated to be
$8,278,519.42. This metric provides a comprehensive measure of the overall financial
success of the company based on the total revenue and associated costs.
Top 5 Products with the Highest Profit Margins:
The profit margin for each product is calculated by subtrac'ng the cost from the
revenue and then dividing by the revenue. Here are the top 5 products with the highest
profit margins:
• PAPER CRAFT, LITTLE BIRDIE (StockCode: 23843):
Descrip'on: Paper craI item named "Lijle Birdie."
Revenue: $168,469.60
• MEDIUM CERAMIC TOP STORAGE JAR (StockCode: 23166):
Descrip'on: Medium-sized ceramic top storage jar.
Revenue: $77,183.60
• PICNIC BASKET WICKER 60 PIECES (StockCode: 22502):
Descrip'on: Wicker picnic basket with 60 pieces.
Revenue: $38,970.00
• POST (StockCode: POST):
Descrip'on: Postage service.
Revenue: $8,142.75
• SET OF TEA COFFEE SUGAR TINS PANTRY (StockCode: 23243):
Descrip'on: Set of tea, coffee, and sugar 'ns for the pantry.
Revenue: $7,144.72
10. Customer Sa9sfac9on:
RFM-based Customer Sa)sfac)on:
• High-Value Customers:
Characteris'cs: Low recency, high frequency, and high monetary scores.
Count: 333 customers
• Poten'al Loyal Customers:
Characteris'cs: Recent purchases, high frequency, moderate monetary scores.
Count: 333 customers
• New Customers:
Characteris'cs: Very recent purchases, low frequency, and low monetary score.
Count: 110 customers
• Churned Customers:
Characteris'cs: High recency, low frequency, and low monetary scores.
Count: 44 customers
Pie Chart Analysis:
The pie chart provides a visual representa'on of the distribu'on of customers across
sa'sfac'on segments.
Key Observa)ons:
High-Value Customers: Cons'tute a significant por'on of the customer base,
emphasizing their importance.
Poten)al Loyal Customers: A considerable share, indica'ng a promising group for
future loyalty ini'a'ves.
New Customers: Represen'ng a smaller segment, poten'al for growth through targeted
engagement.
Churned Customers: A smaller but notable segment, requiring ajen'on for poten'al reengagement.
Sen)ment Analysis in Customer Feedback:
For sen'ment analysis, synthe'c data was generated, and sen'ment labels were
assigned to simulate customer feedback.
Sen'ment Labels:
• Posi've
• Nega've
The bar chart illustrates the sen'ment distribu'on in customer feedback, highligh'ng
the propor'on of posi've, nega've sen'ments., providing insights into the overall
sen'ment trends.
Strategic Implica)ons:
• Segment-Specific Strategies: Tailor marke'ng and engagement strategies based on
customer segments iden'fied through RFM analysis.
• Feedback-driven Improvements: Leverage sen'ment analysis to iden'fy areas for
improvement in products or services based on customer feedback.
• Customer Reten'on: Implement strategies to retain high-value and poten'al loyal
customers, addressing their specific needs and preferences.
Overall Impact:
The combined analysis provides a comprehensive view of customer sa'sfac'on, enabling
the company to tailor its strategies to enhance overall customer experience and loyalty.
The insights gained from these analyses will empower the company to make data-driven
decisions, improve customer sa'sfac'on, and foster long-term rela'onships with its
customer base.
