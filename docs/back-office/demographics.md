disqus: sema-docs

The Demographics page shows information on active customers filtered 
by date. When the date filter chosen is "Total" the count of all active 
customers created that meet the various criteria are shown. When a date 
range is specified, the count of all all active customers created during
 the date range are shown.

## Number of Active Customers and Consumer Penetration

Example:
 A Site contains a total of 45 customers, 40 of which are active and 
these customers have a total consumer base of 859. The Site has an 
estimated potential consumer base of 2000 consumers

Demographics will show a total of 40 customers for 'total' date range with a Consumer Penetration rate of 43% (859/2000 *100)

For
 the month June, 2018, 9 customers with a potential consumer base of 263
 consumers  were created.  This results in a Consumer Penetration rate 
for that month of  13%  (263/2000 *100)

The requirements for accurate "Consumer Penetration" are that database** kiosk.consumer_base** and **customer_account.consumer_base** be populated.

The service endpoint for **Number of Active Customers** and **Consumer Penetration** is **/sema/dashboard/site/customer-summary**

## Customers by By Distance

Customers
 by distance shows a pie chart of customers as a function of distance 
from the kiosk. The requirements for accurate "Customers by distance" is
 that **customer_account.distance **be populated.

The service endpoint is **/sema/dashboard/site/customer-summary**

## Customers by By Income level

Customers
 by income level shows a pie chart of customers as a function of income 
level. The requirements for accurate "Customers by income level " is 
that **customer_account.income_level **be populated.

The service endpoint is **/sema/dashboard/site/customer-summary**

## Customers by By Gender

Customers
 by gender shows a pie chart of customers as a function of gender. The 
requirements for accurate "Customers by income level " is that **customer_account.gender **be populated, ('M' or 'F')

The service endpoint is **/sema/dashboard/site/customer-summary**