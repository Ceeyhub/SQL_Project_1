What are your risk areas? Identify and describe them.
Data Intergrity concerns due to inconsistencies noticed in data  
Error scripting - the columns in the table required the use of "" before executing on PGAdmin

QA Process:
Describe your QA process and include the SQL queries used to execute it.
I reviewed the data to see if the data type was consistent 

SELECT * FROM public.all_sessions
LIMIT 100

SELECT * FROM public.analytics
LIMIT 100

SELECT * FROM public.products
ORDER BY "SKU" ASC LIMIT 100

I checked for duplicate rows
SELECT
  COUNT(*) AS num_duplicate_rows
FROM
  all_sessions
GROUP BY
  "fullVisitorId",
  "channelGrouping",
  "time",
  "country",
  "city",
  "totalTransactionRevenue",
  "transactions",
  "timeOnSite",
  "pageviews",
  "sessionQualityDim",
  "date",
  "visitId",
  "type",
  "productRefundAmount",
  "productQuantity",
  "productPrice",
  "productRevenue",
  "SKU",
  "v2ProductName",
  "v2ProductCategory",
  "productVariant",
  "currencyCode",
  "itemQuantity",
  "itemRevenue",
  "transactionRevenue",
  "transactionId",
  "pageTitle",
  "searchKeyword",
  "pagePathLevel1",
  "eCommerceAction_type",
  "eCommerceAction_step",
  "eCommerceAction_option"
HAVING 
 COUNT (*) > 1
