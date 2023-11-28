Question 1: Find the highest number of orders placed by each visitor.

SQL Queries: SELECT full_visitorid, COUNT(sku) AS order_count
             FROM products p
             JOIN all_sessions als ON p.sku = als.productsku
             GROUP by full_visitorid
             ORDER BY order_count DESC
             LIMIT 1

Answer: 9



Question 2: Identify products that are out of stock.


SQL Queries: SELECT DISTINCT v2product_name,stock_level 
             FROM products p
             JOIN all_sessions als ON p.sku = als.productsku
             GROUP BY v2product_name, stock_level
             HAVING stock_level = 0

Answer: 96 products are out of stock



Question 3: Find the number of orders placed by each visitor in 2017.

SQL Queries: SELECT full_visitorid, COUNT(sku) AS order_count
             FROM products p
             JOIN all_sessions als ON p.sku = als.productsku
             WHERE EXTRACT(YEAR FROM date) = 2017 
             GROUP by full_visitorid
             ORDER BY order_count DESC

Answer: 7140 orders were placed in 2017.



Question 4: Identify the busiest month in terms of ordered quantity.

SQL Queries: SELECT EXTRACT(MONTH FROM date) AS month, COUNT(ordered_quantity) AS order_count
             FROM products p
             JOIN all_sessions als ON p.sku = als.productsku
             GROUP BY month
             ORDER BY order_count DESC
             LIMIT 1

Answer: The busiest month is August with 1602 orders



Question 5: Categorize visitors based on total spending.

SQL Queries: SELECT DISTINCT als.full_visitorid,
             CASE 
	              WHEN SUM((unit_price/1000000) * units_sold) > 4500 THEN 'Big Buyer'
	              WHEN SUM((unit_price/1000000) * units_sold) > 1500 THEN 'Mid Buyer'
	              ELSE 'Low Buyer'
             END AS spending_class
             FROM all_sessions als
             LEFT JOIN analytics a ON als.full_visitorid = a.full_visitorid
             GROUP BY als.full_visitorid

Answer:
"0000639845445148063" ,	"Low Buyer"
"0000702913088027926" ,	"Low Buyer"
"0001436786657417059" ,	"Low Buyer"
"0001527863526384268" , "Low Buyer"
"0001611849527956932" ,	"Low Buyer"
"0002313459690268715" ,	"Low Buyer"
"0003494484836572385" ,	"Low Buyer"
"0003520120824829275" ,	"Low Buyer"
etc...
