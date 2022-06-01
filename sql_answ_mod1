SELECT * FROM datalearn.orders
LIMIT 5

--Total Sales
SELECT ROUND(SUM(sales), 2) AS "Total Sales"
FROM datalearn.orders;

--Total Profit
SELECT ROUND(SUM(profit), 2) AS "Total Profit"
FROM datalearn.orders;

--Profit Ratio
SELECT ROUND(SUM(profit) / SUM(sales) * 100, 2) AS "Profit Ratio"
FROM datalearn.orders;

--Profit per Order
SELECT order_id, ROUND(SUM(profit), 2) AS "Profit per Order"
FROM datalearn.orders
GROUP BY order_id
ORDER BY ROUND(SUM(profit), 2) DESC;

--Sales Per Customer
SELECT ROUND(SUM(sales) / COUNT(DISTINCT order_id), 2) AS "Sales Per Customer"
FROM datalearn.orders;

--Avg. Discount
SELECT ROUND(AVG(discount), 2) AS "Average Discount"
FROM datalearn.orders;

--Monthly Sales by Segment 
SELECT segment, EXTRACT(YEAR FROM Order_date) AS "Year", EXTRACT(MONTH FROM Order_date) AS "Month", ROUND(SUM(sales), 2) AS "Sales"
FROM datalearn.orders
GROUP BY segment, 2, 3
HAVING EXTRACT(YEAR FROM Order_date) = 2019
ORDER BY 2 DESC, 3 ASC, 1 ASC;

--Monthly Sales by Product Category
SELECT category, EXTRACT(YEAR FROM Order_date) AS "Year", EXTRACT(MONTH FROM Order_date) AS "Month", ROUND(SUM(sales), 2) AS "Sales"
FROM datalearn.orders
GROUP BY category, 2, 3
HAVING EXTRACT(YEAR FROM Order_date) = 2019
ORDER BY 2 DESC, 3 ASC, 1 ASC;

--Sales by Product Category over time
SELECT category, EXTRACT(YEAR FROM Order_date) AS "Year", ROUND(SUM(sales), 2) AS "Sales"
FROM datalearn.orders
GROUP BY category, 2
ORDER BY 1 ASC, 2 DESC;


--Sales and Profit by Customer
SELECT customer_name, ROUND(SUM(sales), 0) AS "Sales", ROUND(SUM(profit), 0) AS "Profit"
FROM datalearn.orders
GROUP BY customer_name 
ORDER BY 3 DESC;

--Sales per region
SELECT state, ROUND(SUM(sales), 0) AS "Sales"
FROM datalearn.orders
GROUP BY state 
ORDER BY 2 DESC;

--Customer Ranking
SELECT customer_name, RANK() OVER (ORDER BY SUM(sales) DESC), ROUND(SUM(sales), 0) AS "Sales"
FROM datalearn.orders
GROUP BY customer_name
LIMIT 10;
