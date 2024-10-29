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
