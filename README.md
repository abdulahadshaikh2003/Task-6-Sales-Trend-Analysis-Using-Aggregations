# Task 6: Sales Trend Analysis Using Aggregations

# Objective
Analyze monthly revenue and order volume from the online sales dataset using SQL aggregation functions.

# Dataset
Source: Kaggle - https://www.kaggle.com/datasets/shreyanshverma27/online-sales-dataset-popular-marketplace-data
online_sales table with columns:
- Transaction ID
- Date
- Product Category
- Product Name
- Units Sold
- Unit Price
- Total Revenue
- Region
- Payment Method

# Tools Used
- MySQL (Workbench)

# Sreenshots of output

# SQL Queries
USE onlinesalesdata;
show databases;
show tables;
SELECT * FROM `online sales data`;
show columns from `online sales data`;
#Monthly Revenue & Order Volume
SELECT
    YEAR(Date) AS order_year,
    MONTHNAME(Date) AS order_month,
    SUM(`Total Revenue`) as total_revenue,
    COUNT(*) AS total_orders
FROM `online sales data`
GROUP BY YEAR(Date), MONTHNAME(Date)
order by year(date), monthname(date);
#Filter for a Specific Year (Example: 2024)
SELECT 
    YEAR(Date) AS order_year,
    MONTH(Date) AS order_month,
    SUM(`Total Revenue`) AS total_revenue,
    COUNT(DISTINCT `Transaction ID`) AS total_orders
FROM `online sales data`
WHERE YEAR(Date) = 2024
GROUP BY order_year, order_month
ORDER BY order_month;
#Top 3 Months by Revenue
SELECT 
    YEAR(Date) AS order_year,
    MONTH(Date) AS order_month,
    SUM(`Total Revenue`) AS total_revenue
FROM `online sales data`
GROUP BY order_year, order_month
ORDER BY total_revenue DESC
LIMIT 3;

#Top 3 Months by Order Volume
SELECT 
    YEAR(Date) AS order_year,
    MONTH(Date) AS order_month,
    COUNT(DISTINCT `Transaction ID`) AS total_orders
FROM `online sales data`
GROUP BY order_year, order_month
ORDER BY total_orders DESC

# Folder Structure
Task-6-Sales-Trend/
├── task6_sales_trend.sql
├── screenshots/
│   ├── q1_monthly_revenue_orders.png
│   ├── q2_2023_monthly_revenue_orders.png
│   ├── q3_top3_months_revenue.png
│   └── q4_top3_months_orders.png
└── README.md

LIMIT 3;

