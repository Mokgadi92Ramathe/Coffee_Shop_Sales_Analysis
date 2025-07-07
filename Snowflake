SELECT * FROM COFFEE.SHOP.COFFEESHOPSALES;

SELECT COUNT (transaction_id) AS number_of_sales
FROM COFFEE.SHOP.COFFEESHOPSALES;


SELECT SUM (Transaction_qty) AS number_of_unit_sold
FROM COFFEE.SHOP.COFFEESHOPSALES;

--Calculate the total revenue --
SELECT Transaction_qty*unit_price AS revenue_per_transanction 
FROM COFFEE.SHOP.COFFEESHOPSALES;

--Revenue product category---
SELECT SUM(transaction_qty*unit_price) AS total_revenue,
product_category
FROM COFFEE.SHOP.COFFEESHOPSALES
GROUP BY product_category
ORDER BY total_revenue DESC;


SELECT * FROM COFFEE.SHOP.COFFEESHOPSALES;

--Get the earliest time in which the shop opens
SELECT MIN(transaction_time)
FROM COFFEE.SHOP.COFFEESHOPSALES;


--Get the latest time in which the shop closes--
SELECT MAX(transaction_time)
FROM COFFEE.SHOP.COFFEESHOPSALES;


--Final query for analysis--
SELECT
    SUM(transaction_qty*unit_price) AS Total_revenue,
    SUM(transaction_qty) AS number_of_units_sold,
    SUM(transaction_id) AS number_of_sales,
    TO_CHAR(transaction_date, 'YYYYMM') AS month_id,
    MONTHNAME(transaction_date) AS month_name,
    DAYNAME(transaction_date) AS day_name,    
    CASE
        WHEN transaction_time BETWEEN '06:00:00' AND '11:59:59' THEN 'Morning'
        WHEN transaction_time BETWEEN '12:00:00' AND '15:59:59' THEN 'Afternoon'
        WHEN transaction_time BETWEEN '16:00:00' AND '20:00:00' THEN 'Evening'
END AS time_bucket,
    CASE
        WHEN  SUM(transaction_qty*unit_price) BETWEEN 0 AND 20 THEN 'low'
        WHEN  SUM(transaction_qty*unit_price) BETWEEN 21 AND 40 THEN 'Med'
        WHEN  SUM(transaction_qty*unit_price) BETWEEN 41 AND 60 THEN 'High'
    ELSE 'Very High'
END AS spend_bands,
       product_category,
        product_type,
        product_detail,
        store_location
FROM COFFEE.SHOP.COFFEESHOPSALES
GROUP BY time_bucket,
        product_category,
        product_type,
        product_detail,
        store_location,
        month_id,
        month_name,
        day_name;


