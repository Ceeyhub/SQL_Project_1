Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SELECT city, country, MAX("totalTransactionRevenue")/1000000 AS highestTransactionRevenue
FROM all_sessions a
WHERE a.city <> 'not available in demo dataset' AND a.city <> '(not set)'
GROUP BY city, country
HAVING MAX("totalTransactionRevenue")/1000000 >= 1
ORDER BY highestTransactionRevenue DESC

Answer: 20 rows, Atlanta, US - city/country with the highest Transaction revenue




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries: SELECT a.city, a.country, AVG("OrderedQuantity") AS Average_Visitors_Orders
FROM all_sessions a
INNER JOIN products p ON a."SKU" = p."SKU"
WHERE a.city <> 'not available in demo dataset' AND a.city <> '(not set)'
GROUP BY a.city, a.country
ORDER BY Average_Visitors_Orders DESC



Answer: 268 rows with Council bluffs, United States, AVG Visitors order of 7589





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries: SELECT a."v2ProductCategory", a."city", a."country"
FROM all_sessions a
INNER JOIN sales_report sr ON a."SKU" = sr. "SKU"
WHERE a.city <> 'not available in demo dataset' AND a.city <> '(not set)' AND a."v2ProductCategory" <> '(not set)'
ORDER BY sr."TotalOrdered" DESC



Answer: 4130 rows...Yes there is a pattern to the types of product categories ordered - Home/office products





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries: SELECT a.city, a.country, MAX(sr."TotalOrdered"), sr."Name" AS top_Selling_Product
FROM all_sessions a
LEFT JOIN sales_report sr ON a."SKU" = sr."SKU"
WHERE a.city <> 'not available in demo dataset' AND a.city <> '(not set)'
GROUP BY sr."Name", a.country, a.city, sr."TotalOrdered"
HAVING MAX(sr."TotalOrdered") >= 1
ORDER BY MAX(sr."TotalOrdered") DESC



Answer: 1960 rows - Top selling products is Ballpoint LED light pen 





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:SELECT DISTINCT a."city", a."country", SUM(a."totalTransactionRevenue"/1000000) AS Revenue_Generated
FROM all_sessions a
WHERE a.city <> 'not available in demo dataset' AND a.city <> '(not set)' 
AND a."totalTransactionRevenue" >= 1
GROUP BY a."city", a."country"
ORDER BY Revenue_Generated DESC


Answer: San Francisco has the highest revenue generated from each city







