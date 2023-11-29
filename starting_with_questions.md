Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries: SELECT country, city, ROUND((SUM(revenue)/1000000),0) AS total_revenue
             FROM analytics a
             LEFT JOIN all_sessions als ON a.full_visitorid = als.full_visitorid
             WHERE city NOT LIKE '%not%'
             GROUP BY country, city
             HAVING SUM(revenue) IS NOT NULL
             ORDER BY total_revenue DESC
             LIMIT 1




Answer: "United States",	"Mountain View"	, 10549



**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries: 
SELECT country, city, ROUND(AVG(ordered_quantity),0) AS avg_productordered
FROM products p
JOIN all_sessions als ON p.sku = als.productsku
WHERE country != '(not set)' AND city NOT LIKE '%not%'
GROUP BY country, city
ORDER BY avg_productordered DESC

Answer:
"United States"	,"Council Bluffs",	7589
"Ireland",	"Cork" ,	3786
"United States"	, "Bellflower",	3786
"Chile"	, "Santiago" ,	3607
"United States",	"Bellingham",	2836
"United States"	, "Detroit"	, 2748
"South Africa",	"Westville" ,	2299
"Argentina"	, "Santa Fe",	1933
"United States"	, "Nashville",	1886
"Czechia", 	"Brno" ,	1548
etc..





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
SELECT v2product_category AS product_category, ordered_quantity, city, country
FROM products p
JOIN all_sessions als ON p.sku = als.productsku
WHERE city NOT LIKE '%not%' AND country != '(not set)' AND v2product_category NOT LIKE '%not%'
GROUP BY v2product_category, ordered_quantity, city, country
ORDER BY ordered_quantity DESC


Answer: Yes there is pattern.





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:

SELECT name, country, SUM(ordered_quantity) AS total_order
FROM products p
JOIN all_sessions als on p.sku = als.productsku
GROUP BY name, country
ORDER BY total_order DESC



Answer: 
"United States"	, " Kick Ball"	,409590
"United States",	" Custom Decals" , 	306666
"United States",	" Twill Cap", 187298
"United States"	, " Cam Outdoor Security Camera - USA" ,	179454
"United States",	" 22 oz Water Bottle",	153147
"United States"	, "22 oz  Bottle Infuser" ,	146500
"United States"	, " Cam Indoor Security Camera - USA" ,	143313
"United States"	, " Learning Thermostat 3rd Gen-USA - Stainless Steel" ,	103730
"United States"	, " Men's 100% Cotton Short Sleeve Hero Tee White" , 	86064
"United States" ,	"SPF-15 Slim & Slender Lip Balm" ,	84686
"United States"	, " Leatherette Notebook Combo"	 , 83804
"India"	, " Custom Decals"	, 83292




**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:
SELECT country, SUM((revenue)/1000000) AS summ_revenue
FROM analytics a  
LEFT JOIN all_sessions als  ON a.full_visitorid = als.full_visitorid
WHERE country IS NOT NULL
GROUP BY country
HAVING SUM(revenue) IS NOT NULL
ORDER BY summ_revenue DESC



Answer:
"United States"	, 114833
"Canada", 	485
"Germany", 	69
"Japan", 29
"Switzerland", 16







