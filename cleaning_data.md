What issues will you address by cleaning the data?
--Data Inconsistencies
--Missing Data
--Duplicate Records
--Inconsistent Data Formats

Queries:
Below, provide the SQL queries you used to clean your data.
--reviewing the data set
SELECT * FROM public.all_sessions
LIMIT 100

SELECT * FROM public.products
ORDER BY "SKU" ASC LIMIT 100

--making changes to the data set, some data entry errors were observed ...mix up with county and city, (London - United states) Product variant (not Set) instead of null, 
SELECT * FROM public.analytics
LIMIT 100

SELECT unit_price/1000000 AS Unit_Price
FROM analytics
----update unit_price on the table
UPDATE analytics
SET unit_price = unit_price/1000000

SELECT "productPrice"
FROM all_sessions
---update productPrice on the table
UPDATE all_sessions
SET "productPrice" = "productPrice"/1000000

