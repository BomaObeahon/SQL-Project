# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals

My goal was to build a framework for managing data quality and improve the data to guarantee its accuracy and reliability while drawing meaningful insights on the provided datasets.



## Process

 Step 1 was to create a database called 'ecommerce'
 Step 2 was to create various tables on the csv files that was made available.
 Step 3 was to import the files into the created tables.
 Step 4 was to study each table.
 Step 5 was to model the data by creating a table called the visitor table,having only the full_visitorid to establish a relationship between the analytics table and the all_sessions table.
 Step 6 was to link tables using the primary key and foreign key.
 Step 7 was to create queries to derive insights while cleaning the data to remove duplicates,nulls values etc.

## Results
(fill in what you discovered this data could tell you and how you used the data to answer those questions)
I was able to derive meaningful insights from the data like;
1. The busiest month in terms of ordered quantity by the visitors, which was the month of August with 1602. This was done by first merging 2 tables(all_sessions and products), grouping by months,extracting the month from the date column and ordering by the month.
2. Identify products that are out of stock, which had 96 products not in stock. This was done by joining all_sessions table and products table,grouped by the product name and stock level,then selecting the product name and stock level where the stock level was zero.
3. I was able to find the number of orders placed by each visitor in 2017,which was 7140 orders.
4. I was able to categorize visitors based on  their total spending, this was done by using the CASE clause.
   CASE 
	    WHEN SUM((unit_price/1000000) * units_sold) > 4500 THEN 'Big Buyer'
    	WHEN SUM((unit_price/1000000) * units_sold) > 1500 THEN 'Mid Buyer'
	    ELSE 'Low Buyer'
6. Mountain View city in the United State had the highest transaction revenue.
7. Carried out a Referential Integrity check between all_sessions table and products table using sku(productsku), which showed that was a valid relationship between both tables.


## Challenges 

1. Initially i found it difficulty in loading the various datasets(csv files) into the database.
2. Figuring out what column to set as primary key and foreign key in the database was a huge challenge.
3. The datasets was filled with a whole lot of null values, duplicated colmuns, etc. The overall accuracy of the datasets was really poor.
4. Knowing what columns from the various table to creating a query was very tasking as there were a lot on irrelevant data.

## Future Goals
(what would you do if you had more time?)
If given more time i'll do further analysis of the data.
