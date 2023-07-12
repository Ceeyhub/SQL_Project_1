Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries: SELECT city, country, MAX("totalTransactionRevenue")/1000000 AS highestTransactionRevenue
FROM all_sessions a
GROUP BY city, country
HAVING MAX("totalTransactionRevenue")/1000000 >= 1
ORDER BY highestTransactionRevenue DESC

Answer: 21 rows 




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries: SELECT a.city, a.country, AVG("OrderedQuantity") AS Average_Visitors_Orders
FROM all_sessions a
INNER JOIN products p ON a."SKU" = p."SKU"
WHERE a.city <> 'not available in demo dataset' AND a.city <> '(not set)'
GROUP BY a.city, a.country
ORDER BY Average_Visitors_Orders DESC



Answer: 268 rows with Council bluffs, United States, AVG Visitors order of 7589





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







