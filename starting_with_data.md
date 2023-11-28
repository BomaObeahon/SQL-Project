Question 1: Find the highest number of orders placed by each visitor:

SQL Queries: SELECT full_visitorid, COUNT(sku) AS order_count
             FROM products p
             JOIN all_sessions als ON p.sku = als.productsku
             GROUP by full_visitorid
             ORDER BY order_count DESC
             LIMIT 1

Answer: 9



Question 2: 

SQL Queries:

Answer:



Question 3: 

SQL Queries:

Answer:



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
