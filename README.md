# Blinkit-Sales-Performance-Analysis-Dashboard
![image alt](https://github.com/Y7976/Blinkit-Sales-Performance-Analysis-Dashboard/blob/2adcecdb12495f160f493fe6dbfc1a335fec2fce/Blinkit%20image.png)

[Download data set](https://github.com/Y7976/Blinkit-Sales-Performance-Analysis-Dashboard/blob/56029c97d21954b4f527ccde4db8900d47427b77/BlinkIT%20Grocery%20Data%20(1).csv)
##  Project Overview

This project is based on Blinkit grocery sales data analysis using **SQL** and **Power BI**.  
The main objective of this project was to analyze sales performance, customer behavior, outlet efficiency, and product trends to generate business insights that can help improve business decision-making.

In this project, I solved multiple business-related SQL problems using the dataset and then created an interactive Power BI dashboard to visualize important KPIs and sales insights.

This project helped me improve my practical skills in:
- SQL Query Writing
- Data Analysis
- Power BI Dashboard Development
- KPI Reporting
- Business Intelligence
- Data Visualization

---

#  Business Objective

The goal of this project is to perform a comprehensive analysis of Blinkit’s grocery sales data to understand:

- Overall sales performance
- Customer purchasing behavior
- Product category performance
- Outlet efficiency
- Sales distribution across locations
- Inventory and item trends

The insights generated from this project can help businesses:
- Improve sales performance
- Enhance customer satisfaction
- Optimize inventory management
- Identify high-performing products and outlets

---

#  Tools & Technologies Used

| Tool | Purpose |
|---|---|
| SQL | Data querying and business analysis |
| Power BI | Dashboard creation and visualization |
| Excel | Dataset handling |
| DAX | KPI calculations in Power BI |
| Data Cleaning | Data preprocessing and transformation |

---

#  Dataset Information    
[Download DataSet](https://github.com/Y7976/Blinkit-Sales-Performance-Analysis-Dashboard/blob/56029c97d21954b4f527ccde4db8900d47427b77/BlinkIT%20Grocery%20Data%20(1).csv)

The dataset used in this project contains Blinkit grocery sales data collected from different outlets.  
It includes detailed information about products, sales performance, outlet characteristics, customer ratings, and inventory distribution.

The dataset was used to perform SQL-based business analysis and build an interactive Power BI dashboard for KPI tracking and visualization.

---

#  Dataset Features

The dataset contains multiple columns related to:

- Product details
- Outlet information
- Sales data
- Customer ratings
- Product categories
- Outlet performance

---

#  Important Columns Description

| Column Name | Description |
|---|---|
| Item Identifier | Unique ID assigned to each product |
| Item Weight | Weight of the product |
| Item Fat Content | Indicates whether the product is Low Fat or Regular |
| Item Visibility | Visibility percentage of the product in stores |
| Item Type | Category/type of grocery item |
| Item MRP | Maximum Retail Price of the product |
| Outlet Identifier | Unique ID assigned to each outlet |
| Outlet Establishment Year | Year when the outlet was established |
| Outlet Size | Size category of outlet (Small, Medium, High) |
| Outlet Location Type | Tier classification of outlet location |
| Outlet Type | Type of outlet or supermarket |
| Total Sales | Revenue generated from item sales |
| Rating | Customer rating for products sold |

---

#  Outlet Information

The dataset includes sales data from different outlet types such as:

- Grocery Stores
- Supermarket Type 1
- Supermarket Type 2
- Supermarket Type 3

It also includes outlet size classifications:
- Small
- Medium
- High

And outlet location tiers:
- Tier 1
- Tier 2
- Tier 3

This information helps analyze sales distribution across different business locations.

---

#  Product Categories Included

The dataset contains multiple grocery item categories such as:

- Fruits and Vegetables
- Dairy Products
- Snack Foods
- Frozen Foods
- Household Items
- Beverages
- Breakfast Items
- Health and Hygiene Products
- Meat Products
- Soft Drinks

These categories help identify top-performing products and customer preferences.

---

#  Dataset Usage in This Project

The dataset was used for:

- Sales analysis
- KPI calculations
- Outlet performance analysis
- Customer rating analysis
- Product category analysis
- SQL business problem solving
- Power BI dashboard creation

---

#  KPI Requirements

The dashboard focuses on the following KPIs:

## 1. Total Sales
Overall revenue generated from all items sold.
```sql

SELECT 
    ROUND(SUM(Total_Sales),2) AS Total_Sales
FROM blinkit_data;
```

## 2. Average Sales
Average revenue generated per sale.
```sql

SELECT 
    ROUND(AVG(Total_Sales),2) AS Average_Sales
FROM blinkit_data;
```
## 3. Number of Items
Total count of items sold.
```sql

SELECT 
    COUNT(Item_Identifier) AS Number_of_Items
FROM blinkit_data;
```
## 4. Average Rating
Average customer rating for products sold.
```sql
SELECT 
    ROUND(AVG(Rating),2) AS Average_Rating
FROM blinkit_data;
```
---

# Detailed Analysis Performed

---

## 1️ Total Sales by Fat Content

### Objective
Analyze the impact of fat content on total sales.

### Analysis
Products were categorized into:
- Low Fat
- Regular
```sql
SELECT 
    Item_Fat_Content,
    ROUND(SUM(Total_Sales),2) AS Total_Sales,
    ROUND(AVG(Total_Sales),2) AS Avg_Sales,
    COUNT(Item_Identifier) AS Number_of_Items,
    ROUND(AVG(Rating),2) AS Avg_Rating
FROM blinkit_data
GROUP BY Item_Fat_Content;
```
The analysis compared:
- Total Sales
- Average Sales
- Number of Items
- Average Ratings

### Business Insight
This helps identify customer preferences between healthy and regular products.

---

## 2️ Total Sales by Item Type

### Objective
Identify high-performing product categories.

### Analysis
Different grocery item categories were analyzed based on total revenue contribution.
```sql
SELECT 
    Item_Type,
    ROUND(SUM(Total_Sales),2) AS Total_Sales,
    ROUND(AVG(Total_Sales),2) AS Avg_Sales,
    COUNT(Item_Identifier) AS Number_of_Items,
    ROUND(AVG(Rating),2) AS Avg_Rating
FROM blinkit_data
GROUP BY Item_Type
ORDER BY Total_Sales DESC;
```
### Business Insight
This analysis helps improve:
- Inventory planning
- Product placement
- Marketing strategy

---

## 3️ Fat Content by Outlet for Total Sales

### Objective
Compare outlet sales performance based on product fat content.

### Analysis
Sales were analyzed outlet-wise for:
- Low Fat products
- Regular products
```sql
SELECT 
    Outlet_Identifier,
    Item_Fat_Content,
    ROUND(SUM(Total_Sales),2) AS Total_Sales
FROM blinkit_data
GROUP BY Outlet_Identifier, Item_Fat_Content
ORDER BY Outlet_Identifier;
```
### Business Insight
Helps understand which outlets perform better for specific product categories.

---

## 4️ Total Sales by Outlet Establishment

### Objective
Analyze how outlet age impacts sales performance.

### Analysis
Sales were compared based on outlet establishment years.
```sql
SELECT 
    Outlet_Establishment_Year,
    ROUND(SUM(Total_Sales),2) AS Total_Sales
FROM blinkit_data
GROUP BY Outlet_Establishment_Year
ORDER BY Outlet_Establishment_Year;
```
### Business Insight
Helps determine whether older or newer outlets perform better.

---

## 5️ Percentage of Sales by Outlet Size

### Objective
Understand the relationship between outlet size and total sales.

### Analysis
Outlets were categorized into:
- Small
- Medium
- High

Sales percentages were calculated for each outlet size.

### Business Insight
Helps identify which outlet size contributes the most revenue.

---

## 6️ Sales by Outlet Location

### Objective
Analyze sales distribution across outlet locations.

### Analysis
Sales were compared across:
- Tier 1
- Tier 2
- Tier 3 locations

### Business Insight
Helps understand customer purchasing behavior across different regions.

---

## 7️ All KPIs by Outlet Type

### Objective
Compare all KPIs across different outlet types.

### Analysis
Metrics analyzed:
- Total Sales
- Average Sales
- Number of Items
- Average Rating

across:
- Grocery Stores
- Supermarket Type 1
- Supermarket Type 2
- Supermarket Type 3

### Business Insight
Helps identify the best-performing outlet types.

---

#  SQL Work Performed

In this project, SQL was used for:
- Data extraction
- Aggregation
- KPI calculation
- Grouping and filtering
- Sales analysis
- Business problem solving

### SQL Concepts Used
- SELECT Statements
- GROUP BY
- ORDER BY
- Aggregate Functions
- CASE Statements
- JOINS
- Subqueries

The SQL analysis helped generate insights that were later visualized in Power BI.

---

#  Power BI Dashboard Features

The dashboard includes:

- KPI Cards
- Bar Charts
- Donut Charts
- Pie Charts
- Line Charts
- Filters & Slicers
- Outlet Comparison Visuals
- Sales Trend Analysis

### Interactive Features
Users can filter data based on:
- Outlet Type
- Outlet Size
- Item Type
- Fat Content
- Outlet Location

---



---

# Skills Gained from This Project

Through this project, I improved my skills in:

- SQL Query Writing
- Data Cleaning
- Data Visualization
- KPI Reporting
- Power BI Dashboard Design
- Business Data Analysis
- Retail Sales Analysis
- Data Storytelling

---

#  Business Questions Solved Using Dataset

Using this dataset, multiple business problems were solved such as:

- Which product category generates the highest sales?
- Which outlet type performs best?
- How does outlet size impact sales?
- Which location tier contributes maximum revenue?
- How does fat content affect product sales?
- Which outlets have better customer ratings?

---

#  Conclusion

This project demonstrates how SQL and Power BI can be combined to analyze retail business data and generate meaningful business insights.

By solving business problems using SQL and building interactive dashboards in Power BI, I gained practical experience in:
- Business Intelligence
- KPI Analysis
- Dashboard Development
- Data Analytics

This project also strengthened my understanding of real-world business analytics and reporting techniques.

---



