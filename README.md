# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals

My goal was to build a framework for managing data quality and improve the data to guarantee its accuracy and reliability while drawing meaningful insights on the provided datasets.



## Process

 Step 1 was to create a database called 'ecommerce'
 Step 2 was to create various tables on the csv files that was made available.
 Step 3 was to import the files into the created tables.
 Step 4 was to study each table.
 Step 5 was to link tables using the primary key and foreign key.
 Step 6 was data cleaning and normalization.
 Step 7 was to create queries to create insights.

## Results
(fill in what you discovered this data could tell you and how you used the data to answer those questions)
I was able to derive meaningful insights from the data like;
1. The busiest month in terms of ordered quantity by the visitors. This was done by first merging 2 tables(all_sessions and products), grouping by months,extracting the month from the date column and ordering by the month.
2. Identify products that are out of stock. This was done by joining all_sessions table and products table,grouped by the product name and stock level,then selecting the product name and stock level where the stock level was zero.

## Challenges 

1. Initially i found it difficulty in loading the various datasets(csv files) into the database.
2. Figuring out what column to set as primary key and foreign key in the database was a huge challenge.
3. The datasets was filled with a whole lot of null values, duplicated colmuns, etc. The overall accuracy of the datasets was really poor.
4. Knowing what columns from the various table to creating a query was very tasking as there were a lot on irrelevant data.

## Future Goals
(what would you do if you had more time?)
If given more time i'll do further analysis of the data.
