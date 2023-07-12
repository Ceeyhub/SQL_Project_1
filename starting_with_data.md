Question 1: find all duplicate records 

SQL Queries: SELECT
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

Answer: None



Question 2: find the total number of unique visitors (fullVisitorID) 

SQL Queries: SELECT
  COUNT(DISTINCT "fullVisitorId") AS unique_visitors
FROM all_sessions

Answer: 14147



Question 3: find the total number of unique visitors by referring sites

SQL Queries: SELECT
  COUNT(DISTINCT "fullVisitorId") AS unique_visitors,
  "channelGrouping"
FROM all_sessions
GROUP BY "channelGrouping"
ORDER BY "channelGrouping" DESC

Answer: Organic Search by 8181



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
