OVERVIEW: This project demonstrates my SQL skills and the techniques commonly used by data analysts to explore, clean, and analyse retail sales data. It involves creating and managing a retail sales database, performing data analysis, and using SQL queries to answer key business questions and generate meaningful insights.

Below, I have included the SQL questions and queries used throughout the project, demonstrating how I applied SQL to investigate the data and address specific business requirements.


# SQL--Retails-Sales-Project-1-

SELECT current_database(), current_schema();

SELECT schemaname, tablename
FROM pg_tables 
WHERE tablename = 'retail_sales';

SELECT * FROM retail_sales
WHERE 
transactions_id IS NULL
OR
sale_time IS NULL
OR
customer_id IS NULL
OR
gender IS NULL
OR 
age IS NULL
OR 
category IS NULL
OR 
quantity IS NULL 
OR 
price_per_unit IS NULL 
OR 
cogs IS NULL 
OR 
total_sale IS NULL;

DELETE FROM retail_sales 
WHERE 
transactions_id IS NULL
OR
sale_time IS NULL
OR
customer_id IS NULL
OR
gender IS NULL
OR 
age IS NULL
OR 
category IS NULL
OR 
quantity IS NULL 
OR 
price_per_unit IS NULL 
OR 
cogs IS NULL 
OR 
total_sale IS NULL;

-- Data Analysis & Bussiness problems

-- Q.1 How many sales were complete?
 SELECT COUNT(*) as total_sale FROM retail_sales

-- Q.2 How many individual customers do we have?
SELECT COUNT (DISTINCT customer_id) as total_sale FROM retail_sales

-- Q.3 Write a SQL Query to retrieve all transactions where the category is 'clothing' and the quantity sold is more than or equal to 4. 
SELECT *
FROM retail_sales 
WHERE category = 'Clothing' 
AND quantity >=4

-- Q.4 Write a SQL query to find the average age of customers who purchase from the Electronics category.
 SELECT
 ROUND (AVG(age), 2) as avg_age
 FROM retail_sales 
 WHERE category = 'Electronics'

-- Q.5 Write a SQL query to find all transactions where the total sale is great than 1000.
SELECT * FROM retail_sales 
WHERE total_sale >1000

-- Q.6 Write a SQL query to find the total number of transactions made by each gender in each category.
SELECT
  category,
  gender,
  COUNT(*) as total_transactions
FROM retail_sales
GROUP BY 
  category, gender
ORDER BY 1

-- Q.7 Write a SQL query to find the top 5 customers based on the highest total sales.
SELECT 
    customer_id,
    SUM(total_sale) as total_sales
FROM retail_sales
GROUP BY 1
ORDER BY 2 DESC
LIMIT 5

-- END of project 
