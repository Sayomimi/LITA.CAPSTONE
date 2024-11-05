# CAPSTONE PROJECT
This repository contains the two datasets.

[Sales Performance Analysis for a Retail Store](sales-performance-analysis-for-a-retail-store)

[Customer Segmentation for a Subscription Service](customer-segmentation-for-a-subscription-service)


## Sales Performance Analysis for a Retail Store
---
[Objective](#objective)

[Data Source](#data-source)

[Tools and Techniques](#tools-and-techniques)

[Key Metrics](#key-metrics)

[Expected Outcomes](#expected-outcomes)

[Pivot Tables](#pivot-tables)

[Code Used](#code-used)

[Data Visualization](#data-visualization)

---

### Project Overview: Sales Data Analysis

### Objective:
The goal of this project is to analyze sales performance using advanced data analysis techniques to uncover trends, optimize sales strategies, and improve decision-making. The analysis will focus on understanding product and regional sales performance, customer behavior, and monthly trends, leading to actionable insights.
---
### Data Source:
The dataset consists of transactional sales data with the following key columns:
- Order ID: Unique identifier for each sale.
- Customer ID: Identifier for the customer.
- Product: The item sold.
- Region: The geographic area where the sale occurred.
- Order Date: Date of the transaction.
- Quantity: The number of units sold.
- Unit Price: Price per unit of the product.
---
### Tools and Techniques:

1. Microsoft Excel:
   - Data cleaning, transformation, and preliminary analysis.
   - Use of PivotTables and formulas to create quick summaries.
  
     
2. SQL:
   - Used for querying and aggregating data from the sales database.
   - Filtering data based on region, product, customer, and time periods.
   - Generating insights on total sales, customer segmentation, and product performance.


3. Power BI:
   - Building interactive dashboards for dynamic visualizations.
   - Visual analysis of key performance indicators (KPIs) such as total sales, regional performance, product profitability, and customer segmentation.
   - Drill-down capabilities for exploring data in detail, filtering by time periods, and comparing different products/regions.
---
### Key Metrics:
- Total sales value (Quantity × Unit Price).
- Orders per region and product.
- Sales growth trends over time.
- Top customers by sales volume.
---
### Expected Outcomes:
- Comprehensive Reports: Sales performance insights, including regional, product, and customer-based summaries.
- Interactive Dashboards: Dynamic Power BI dashboards enabling real-time filtering of sales metrics, trends, and performance KPIs.
- Actionable Insights: Recommendations for improving sales strategies, focusing on high-growth products and regions, and identifying key customer segments.
---
### Pivot Tables
![Sales_by_product](https://github.com/user-attachments/assets/51ab1674-da8f-4f17-82d3-48990c4dbb0e)

![Sales by region](https://github.com/user-attachments/assets/9efb5be8-ef99-4e3c-807f-24cc0e36424b)

![Top 10 Customers](https://github.com/user-attachments/assets/beaac4e3-6d2f-49b6-bf87-69607439efaf)

![Monthly trends](https://github.com/user-attachments/assets/bd779fe4-895e-4b9c-ab9f-8d23621d3f7c)

![Average Sale](https://github.com/user-attachments/assets/162284cb-281d-4237-89d2-7fee5a089637)

---
### Code Used
 ```SQL
CREATE DATABASE Sales_DB;

SELECT * FROM Sales_DB.salesdata;

--Retrieve the total sales for each product category--
SELECT SUM(Quantity), Product 
FROM salesdata
GROUP BY Product;

--Find the number of sales transactions in each region--
SELECT COUNT(OrderID) AS SalesTransaction, Region
FROM salesdata
GROUP BY Region;

--Calculate the total revenue per product--
SELECT Product, SUM(Quantity * UnitPrice) AS Total_sales_value
FROM salesdata
GROUP BY Product
ORDER BY Total_sales_value DESC
;

--Calculate the highest-selling product by total sales value--
SELECT Product, SUM(Quantity * UnitPrice) AS Total_sales_value
FROM salesdata
GROUP BY Product
ORDER BY Total_sales_value DESC
LIMIT 1
;

--Calculate monthly sales total for the current year--
 ALTER TABLE salesdata
ADD Year INT;

ALTER TABLE salesdata
ADD Month INT;

UPDATE salesdata
SET Year = YEAR(STR_TO_DATE(Orderdate, '%c/%e/%Y')),
Month = MONTH(STR_TO_DATE(Orderdate, '%c/%e/%Y'));

SELECT Month, SUM(Quantity * UnitPrice) AS Monthly_sales
FROM salesdata 
WHERE Year LIKE 2024
GROUP BY 
Month
ORDER BY Month 
;

--Find the top 5 customers by total purchase amount--
SELECT  Customer_id, SUM(Quantity * UnitPrice) AS Total_purchase_amount
FROM salesdata
GROUP BY Customer_id
ORDER BY Total_purchase_amount DESC
LIMIT 5;

--Calculate the percentage of total sales contributed by each region
SELECT Region,
SUM(Quantity * UnitPrice) AS Region_Sales,
(SUM(Quantity * UnitPrice)/(SELECT SUM(Quantity * UnitPrice) FROM salesdata )* 100) AS Percentage_of_totalsales
FROM salesdata
GROUP BY Region
ORDER BY Percentage_of_totalsales DESC;

--Identify products with no sales in the last quarter--
SELECT Product
FROM salesdata
GROUP BY Product
HAVING MAX(STR_TO_DATE(OrderDate, '%c/%e/%Y')) <DATE_SUB(CURDATE(), INTERVAL 1 QUARTER);
```
---
### Data Visualization

Sales Overview Dashboard Description

  - Total Sales (Revenue): $10,587,500
  - Average Revenue: $21.18K
  - Total Orders: 50K
  - Total Units Sold: 345K

- Total Sales (Revenue) by Month: A line chart displays monthly revenue trends, with the highest point reaching $2,750,000, reflecting peaks and troughs in monthly sales.

- Top Performing Products: A bar chart reveals revenue by product, with **Shoes** generating $3,087,500, followed by **Shirt** and **Hat**.

- Sum of Quantity by Product: A donut chart shows the distribution of quantities sold across products, with **Jacket** accounting for 63K units (18.12%) and **Socks** at 73K units (21.19%).

- Top Customers: A table lists the top 10 customers by total revenue, with **Cus1488** contributing the highest sales at $29,340.

- Products Purchased by Top 5 Customers: A clustered column chart displays the purchasing patterns of the top 5 customers across products, showing **Cus1375** and **Cus1049** as high-diversity product purchasers.

The dashboard includes slicers for year, product, and region, allowing users to filter and analyze data across different segments interactively.


<img width="482" alt="Capstone_Sales LITA" src="https://github.com/user-attachments/assets/80b72154-94e7-4568-9233-e88670857a39">




## Customer Segmentation for a Subscription Service

### Project Overview: Customer Segmentation for a Subscription Service
### Objective:
The primary goal of this project is to analyze customer data for a subscription service to identify segments, subscription patterns, and key trends related to cancellations and renewals. This analysis will provide insights into customer behavior, subscription preferences, and factors driving churn. The final deliverable will be a Power BI dashboard that visualizes these insights, allowing stakeholders to explore the data interactively.

### Summary:
This project involves:
- Analyzing customer data to uncover patterns in subscription plans, duration, and customer retention.
- Tracking key trends such as cancellations within the first six months, popular subscription types, and overall customer activity.
- Delivering actionable insights through an interactive Power BI dashboard.

### Tools and Techniques:
- Excel: Initial data analysis and summary reporting through PivotTables.
- SQL: Querying the dataset to extract insights from the subscription database
- Power BI: Visualizing the data and creating an interactive dashboard.

### Pivot Table
![Active customers](https://github.com/user-attachments/assets/13d83a43-14f3-475d-9275-02479308f925)

![Rev_sub_reg](https://github.com/user-attachments/assets/4df5c629-30da-41a2-b521-7dcf82bde8f5)

![Canceled sub](https://github.com/user-attachments/assets/2908732a-0d33-4ecd-93e4-3262723a1b7a)

![Avg_sub](https://github.com/user-attachments/assets/bae20d23-d4fd-4685-b586-662ac2cb6e19)

![Popular sub](https://github.com/user-attachments/assets/3ce1e230-f4a9-4f60-83ac-26e27cbfc4ef)

![Monthly revenue](https://github.com/user-attachments/assets/f633fe5e-1cba-4b7f-a390-cd79c49b563c)

### Codes Used

``` SQL
--retrieve the total number of customers from each region--

SELECT
      COUNT(CustomerID),
      Region
FROM
      customerdata
GROUP BY
      Region;

--find the most popular subscription type by the number of customers--
SELECT
     COUNT(CustomerID) AS Customer_count,
     SubscriptionType
FROM
     customerdata
GROUP BY
      SubscriptionType
ORDER BY
     Customer_count DESC
LIMIT 1;


--find customers who canceled their subscription within 6 months.--

SELECT 
    CustomerID, 
    CustomerName, 
    SubscriptionStart, 
    SubscriptionEnd,
    DATEDIFF(STR_TO_DATE(SubscriptionEnd, '%c/%e/%Y'), 
             STR_TO_DATE(SubscriptionStart, '%c/%e/%Y')) AS Subscription_duration_days
FROM 
    customerdata
WHERE  Canceled = 'TRUE'  -- Only include customers who canceled--
    AND DATEDIFF(STR_TO_DATE(SubscriptionEnd, '%c/%e/%Y'), 
                 STR_TO_DATE(SubscriptionStart, '%c/%e/%Y')) <= 180  -- Within 6 months--
    AND SubscriptionStart IS NOT NULL
    AND SubscriptionEnd IS NOT NULL;



--calculate the average subscription duration for all customers.--

SELECT 
	CustomerID,
    AVG(DATEDIFF(
        STR_TO_DATE(SubscriptionEnd, '%c/%e/%Y'), 
        STR_TO_DATE(SubscriptionStart, '%c/%e/%Y')
    )) AS average_subscription_duration
FROM  customerdata
WHERE
    SubscriptionStart IS NOT NULL
    AND SubscriptionEnd IS NOT NULL
    GROUP BY CustomerID;


--find customers with subscriptions longer than 12 months.--
SELECT 
    DISTINCT CustomerID, 
    CustomerName, 
    DATEDIFF(STR_TO_DATE(SubscriptionEnd, '%c/%e/%Y'), 
            STR_TO_DATE(SubscriptionStart, '%c/%e/%Y')) AS subscription_duration_days
FROM 
    customerdata
WHERE 
    DATEDIFF(STR_TO_DATE(SubscriptionEnd, '%c/%e/%Y'), 
            STR_TO_DATE(SubscriptionStart, '%c/%e/%Y')) > 365
    AND SubscriptionStart IS NOT NULL
    AND SubscriptionEnd IS NOT NULL;


--calculate total revenue by subscription type.--

SELECT 
    SubscriptionType, 
    SUM(Revenue) AS Total_revenue
FROM 
    customerdata
GROUP BY 
    SubscriptionType;
--find the top 3 regions by subscription cancellations.--

SELECT
    Region,
    COUNT(Canceled) AS Canceled_Subscription
FROM
    customerdata
WHERE
    Canceled LIKE '%TRUE%'
GROUP BY
    Region
ORDER BY
    Canceled_Subscription  DESC
    LIMIT 3;
--find the total number of active and canceled subscriptions.--

SELECT 
    COUNT(CASE WHEN Canceled = 'TRUE' THEN 1 END) AS Active_subscriptions,
    COUNT(CASE WHEN Canceled = 'FALSE' THEN 1 END) AS Canceled_subscriptions
FROM customerdata;
```

### Data Visualization

1. Total Revenue, Customer Count, and Subscription Duration: Displayed using card visuals, showcasing high-level metrics like the total sum of revenue (150M), customer count (75K), and overall subscription duration (27M).

2. Key Customer Segments: A bar chart that segments customers by subscription type (Basic, Premium, Standard) and region (East, North, South, West), highlighting how customer distribution varies across regions.

3. Subscription Trends: Visualized by a clustered column chart, showing revenue generated by each subscription type across regions.

4. Top 10 Customers by Revenue: A table listing the top customers based on their revenue contribution, providing insight into the highest-value customers.

5. Cancellations Analysis: A donut chart that visualizes the proportion of active versus canceled subscriptions, indicating customer retention.

6. Monthly Trends: A line chart that tracks subscription activity trends on a monthly basis, helping to identify seasonal or monthly fluctuations.

7. Subscription Duration Analysis: A bar chart that visualizes the number of customers based on their subscription duration, categorizing them by different lengths of time.

8. Year Slicer: Interactive slicer allowing users to filter the dashboard by year (2022 and 2023) for more focused analysis.
<img width="577" alt="Capstone_Customers" src="https://github.com/user-attachments/assets/62bab31f-3641-42da-a72e-c5399c51e367">



