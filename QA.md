What are your risk areas? Identify and describe them.
1. DATA INTEGRITY: Inaccurate or incomplete data can lead to data integrity issues.
 The integrity of key identifiers used for relationships (e.g., fullVisitorId or productSKU)
had several inconsistencies which could lead to incorrect associations between datasets. 



QA Process:
Describe your QA process and include the SQL queries used to execute it.

Referential Integrity Check Between all_sessions table and products table using sku.

SELECT 'products' AS table_name, 
       COUNT(*) AS count_rows, 
       'sku' AS key_name,
       COUNT(DISTINCT(sku)) AS count_distinct_key
FROM products

UNION ALL

SELECT 'all_sessions' AS table_name, 
       COUNT(*) AS count_rows,    
       'productsku' AS key_name,
       COUNT(DISTINCT(productsku)) AS count_distinct_key  
FROM all_sessions;
