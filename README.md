# PROJECT TITLE: PROJECT SALES ANALYSIS

### PROJECT OVERVIEW
---
This project aims at analyzing the sales performance of a retail store over a certain period of time. This will be achieved by analysing the sales data to uncover key insights such as top-selling products, regional performances, and monthly sales trends. The goal is to produce an interactive Power BI dashboard that highlights these findings from the data.

### DATA SOURCES
---
The Primary source of Data used is Sales Performance Analysis for a Retail Store downloaded from the Learning Management System of the Ladies in Tech Africa.

## TOOLS USED
---
* Microsoft Excel [Download here](https://www.microsoft.com)
  
  a. cleaning duplicates
  
  b. Analysis with the Pivot tables
  
  c. Visualization
  
* SQL- Structured Query Language for Querying the Sales Data
  
* PowerBI- used for creating Visualizations
  
### DATA CLEANING AND PREPARATION
---
For Data cleaning and Preparations, I performed the following:

* Data download
  
* Checked for Duplicates
  
* Removed Duplicates
  
* Added columns to include information needed such as Total Sales and Revenue
  
### EXPLORATORY DATA ANALYSIS
---
This involved exploring the data to answer some questions such as;
 
 a. top-selling products
 
 b. regional performances
 
 c. monthly sales trends
 
### DATA ANALYSIS
---
This is where we used some lines of code or queries;

```SQL
SELECT * FROM[dbo].[SalesProjecttt]
----1----retrieve the total sales for each product category-----
SELECT product, sum(Quantity) as Total_sales
FROM[dbo].[SalesProjecttt]
GROUP BY Product;

----2--Find the number of sales transactions in each region----
SELECT region,
count(customer_id) as sales_transactions
FROM[dbo].[SalesProjecttt]
GROUP BY region
Order by sales_transactions;

------3-----find the highest-selling product by total sales value ------
SELECT Product, sum(Quantity) as highestsellingproduct
FROM [dbo].[SalesProjecttt]
GROUP BY Product
ORDER BY highestsellingproduct DESC

------4----calculate total revenue per product------
SELECT Product, sum(Quantity) as Total_revenue
FROM[dbo].[SalesProjecttt]
GROUP BY Product
ORDER BY Total_revenue;

SELECT * FROM[dbo].[SalesProjecttt]

------5----calculate monthly sales totals for the current year------
SELECT Month(orderdate) as month,
sum(quantity*unitprice) as monthly_sales
FROM[dbo].[SalesProjecttt]
WHERE YEAR(orderdate)=YEAR(GetDate())
GROUP BY Month(orderdate)
ORDER BY Month;

-----6-------find the top 5 customers by total purchase amount-----
SELECT TOP 5 Customer_Id,
SUM(Quantity) as Total_Purchase
FROM[dbo].[SalesProjecttt]
GROUP BY Customer_Id
ORDER BY Total_Purchase;

-----7------calculate the percentage of total sales contributed by each region-----
SELECT Region,
SUM(Total_sales) as Regionsales, (SUM(Total_sales)/(Select Sum(Total_sales)
FROM [dbo].[SalesProjecttt]))*100 as Percentage_of_total_sales
FROM [dbo].[SalesProjecttt]
GROUP BY region
ORDER BY Regionsales DESC;

SELECT * FROM[dbo].[SalesProjecttt]

-----8----------identify products with no sales in the last quarter.--------
SELECT product, orderId
FROM[dbo].[SalesProjecttt]
WHERE NOT EXISTS(Select 1
FROM[dbo].[SalesProjecttt]
WHERE OrderId= OrderId and Orderdate>= DateAdd(quarter,-1,GetDate()));
```

### DATA VISUALIZATION
---
![Screenshot (19)](https://github.com/user-attachments/assets/473226ea-0bdc-46da-be04-e9d23240a9dc)
