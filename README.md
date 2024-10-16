# LITA.SALES.PROJECT

### Project Overview: Sales Data Analysis

### Objective:
The goal of this project is to analyze sales performance using advanced data analysis techniques to uncover trends, optimize sales strategies, and improve decision-making. The analysis will focus on understanding product and regional sales performance, customer behavior, and monthly trends, leading to actionable insights.

### Data Source:
The dataset consists of transactional sales data with the following key columns:
- Order ID: Unique identifier for each sale.
- Customer ID: Identifier for the customer.
- Product: The item sold.
- Region: The geographic area where the sale occurred.
- Order Date: Date of the transaction.
- Quantity: The number of units sold.
- Unit Price: Price per unit of the product.

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

### Key Metrics:
- Total sales value (Quantity × Unit Price).
- Orders per region and product.
- Sales growth trends over time.
- Top customers by sales volume.
- Average order value and profit margin.

### Analysis Methodology:
- SQL : will be used to extract and preprocess data from the database, filtering specific columns and applying necessary calculations.
- Excel : will be used for intermediate-level analysis and data manipulation, including summary reports and quick visualizations.
- Power BI : will be used for advanced, interactive dashboards, allowing stakeholders to explore insights visually and interactively, with the ability to filter, slice, and drill into the data.

### Expected Outcomes:
- Comprehensive Reports: Sales performance insights, including regional, product, and customer-based summaries.
- Interactive Dashboards: Dynamic Power BI dashboards enabling real-time filtering of sales metrics, trends, and performance KPIs.
- Actionable Insights: Recommendations for improving sales strategies, focusing on high-growth products and regions, and identifying key customer segments.

### Pivot Tables


![Sales by product](https://github.com/user-attachments/assets/6a71ece3-1683-48bf-bcc4-28af3e13ced0)

![Sales by Region](https://github.com/user-attachments/assets/bf435201-c4f1-439a-a8bc-335fa6bb9a81)

![Monthly trend](https://github.com/user-attachments/assets/0ae18ad7-4e6f-4257-995a-453d3a645908)

![Top 10 Customers](https://github.com/user-attachments/assets/292c96ea-e8e6-4a99-96e3-c10d712843f5)

### Code Used
 ```SQL
CREATE DATABASE Sales_DB;

SELECT * FROM Sales_DB.salesdata;

SELECT SUM(UnitPrice), Product 
FROM salesdata
GROUP BY Product;
```
