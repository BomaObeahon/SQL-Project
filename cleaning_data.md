What issues will you address by cleaning the data?

Duplicated rows and columns
Inaccurate and missing values.



Queries:
Below, provide the SQL queries you used to clean your data.
SELECT country, city, ROUND((SUM(revenue)/1000000),0) AS total_revenue
FROM all_sessions als
LEFT JOIN analytics a ON als.full_visitorid = a.full_visitorid
WHERE als.time_onsite IS NOT NULL AND city NOT LIKE '%not%'
GROUP BY country, city
HAVING SUM(revenue) IS NOT NULL

This was used to address the issue of the unit price and remove missing values

SELECT country,city,ROUND(AVG(ordered_quantity),0) AS avg_productordered
FROM products p
JOIN all_sessions als ON p.sku = als.productsku
WHERE country != '(not set)' AND city NOT LIKE '%not%'
GROUP BY country,city
ORDER BY avg_productordered DESC

This was used to remove rows with input as 'not set'
