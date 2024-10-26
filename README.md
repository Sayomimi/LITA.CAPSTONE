# SALES PERFORMANCE ANALYSIS FOR A RETAIL STORE
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
SELECT COUNT(OrderID), Region
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

SELECT Month, SUM(Quantity * UnitPrice) AS Total_sale_value
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

1. Cards for Key Metrics:
   - Total Revenue
   - Average Revenue per Customer
   - Total Units Sold
   - Total Orders
     
2. Line Chart for Total Revenue by Month:
   - A line chart tracks the total revenue over time, broken down by month, providing insight into seasonal trends and revenue growth over time.

3. Bar Chart for Top Performing Products by Revenue:
   - A bar chart highlights the top-performing products based on total revenue. This helps identify which products contribute the most to the company's sales.

4. Donut Chart for Sum of Products by Quantity:
   - A donut chart visualizes the sum of products sold by quantity, giving an overview of product demand in terms of volume.

5. Top Customers:
   - A table showcases the top 10 customers by revenue, giving a detailed view of high-value customers.
   - A clustered column chart visualizes the top 5 customers by the products they purchase, helping to understand customer preferences and product choices.

6. Interactive Slicers:
   - Slicers for Region,
   -  Product,
   -  Year allow users to filter the visuals and explore the data dynamically, providing deeper insights into specific segments.



<img width="480" alt="Sales Capstone" src="https://github.com/user-attachments/assets/7064664e-2eaa-4bb0-9d5e-ce4cae98b180">


