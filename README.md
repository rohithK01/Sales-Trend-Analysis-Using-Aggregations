Sales Trend Analysis Using Aggregations
Overview
This project focuses on analyzing monthly revenue and order volume from the online_sales dataset. The goal is to extract meaningful trends regarding sales performance over time. The analysis includes calculating the total revenue per month and the number of distinct orders made within a specified period.

Objective
The main objective is to:

Analyze monthly revenue and order volume.

Group the data by year and month.

Calculate total revenue for each month using the SUM() function.

Calculate order volume (distinct order count) for each month using COUNT(DISTINCT order_id).

Tools
This project can be executed using the following databases:

PostgreSQL

MySQL

SQLite

Dataset
The dataset used in this analysis is the online_sales dataset, which contains an orders table with the following columns:

order_date (DATE): The date the order was placed.

amount (FLOAT): The total amount spent on the order.

product_id (INT): The identifier for the product ordered.

order_id (INT): The unique identifier for each order.

SQL Script
1. Set up the environment
To perform the analysis, you can use the following SQL script to get the desired results.

sql
Copy
Edit
SELECT
    EXTRACT(YEAR FROM order_date) AS year,
    EXTRACT(MONTH FROM order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM
    orders
GROUP BY
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY
    year,
    month;
2. Explanation of SQL Query:
EXTRACT(YEAR FROM order_date): Extracts the year from the order_date column.

EXTRACT(MONTH FROM order_date): Extracts the month from the order_date column.

SUM(amount): Calculates the total revenue for each month by summing the amount column.

COUNT(DISTINCT order_id): Counts the number of distinct orders for each month.

GROUP BY: Groups the results by year and month to aggregate the data.

ORDER BY: Sorts the results first by year and then by month in ascending order.

3. Limiting the Results (Optional):
If you want to limit the results to a specific time period (e.g., the year 2023), you can add a WHERE clause:

sql
Copy
Edit
WHERE EXTRACT(YEAR FROM order_date) = 2023
Expected Output
The output will be a table displaying the total revenue and order volume for each month of the specified period, sorted by year and month.

Example Output:


Year	Month	Total Revenue	Order Volume
2023	1	5000.00	100
2023	2	4500.00	95
2023	3	6000.00	120
...	...	...	...
Conclusion
This analysis provides valuable insights into the sales trends of a business over time. By understanding the monthly revenue and order volume, businesses can make more informed decisions regarding inventory, promotions, and resource allocation.

