disqus: sema-docs

The Sales page shows sales information filtered by date. When the 
date filter chosen is "Total", the  total metrics of water sold that 
meet the various criteria is shown. When a date range is specified, the 
water sales  for the date filter period is shown.

## Total Customers

Shows
 the total customers for the site plus the change in customers since the
 previous period. For example if there are 40 total customers,  9 
created for May 2018 and 4 customers created in April 2018, this show as
 "**40 Total Customers, 125% since April, 2018**"

The service endpoint is **/sema/dashboard/site/sales-summary**

## Total Revenue

Shows total revenue plus the change in revenue for the for the current period since the last period.

The service endpoint is **/sema/dashboard/site/sales-summary**

## Gross Margin

Gross
 Margin is calculated as total revenue - cost of goods sold. Both total 
Gross Margin and change in Gross Margin since the previous period are 
shown

The requirements for Gross Margin is that, **receipt.cogs** is populated.

The service endpoint is **/sema/dashboard/site/sales-summary**

## Customer Location

The customer location map shows the geographic location of customers. The requirement for geographic locations is that **customer_account.gps_coordinates**
 be populated. Customers whose sales increased over the previous period 
are shown in green, while customers whose sales decreased over the 
previous period are shown in red. Larger circles correspond to larger 
gains/losses

The service endpoint is **/sema/dashboard/site/sales-summary**

## Customer Sales List

The
 customer sales list shows customers, by sales revenue in descending 
order. Green indicates a gain, while red indicates a loss since the 
previous period. The 'trend' column indicates if sales increased or 
decreased since the previous period.

The service endpoint is **/sema/dashboard/site/sales-summary**

## Revenue/Customer

Shows the Revenue/Customer for the current period.

## Revenue/Sales Channel

Shows a pie chart of revenue by sales channel for the period

The service endpoint is** /sema/dashboard/site/receipt-summary**