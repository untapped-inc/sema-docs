disqus: sema-docs

The Volumes page shows information on water sales filtered by date. 
When the date filter chosen is "Total", the  total volume of water sold 
that meet the various criteria is shown. When a date range is specified,
 the water sales and volumes for the date filter period is shown.

## Total Volume

Example: A Site contains 181 receipts, with a water volume of 1603.4 liters.

For the month June, 2018, 199.6 liters were sold

The database requirements for water volume data are that, **receipt_line_item.quantity** and **product.unit_per_product **are populated.

The service endpoint used is **/sema/dashboard/site/receipt-summary**

## Volume/Consumer

Shows the volume sold per consumer. Note that this per consumer refers potential consumers that the kiosk services.

The database requirements for water volume data are that, **receipt_line_item.quantity** and **product.unit_per_product **are and **kiosk.consumer_base** populated.

The service endpoint used is **/sema/dashboard/site/receipt-summary**

## Average Purchase Frequency

Shows the number of times over the period that customers purchase water.

This is calculated as SUM(**receipt.id**)/SUM(Distinct r**eceipt.customer_id**)

The service endpoint used is **/sema/dashboard/site/receipt-summary**

## Volume/Purchase 

Shows the volume per purchase over the period

This is calculated as SUM(**receipt_line_item.quantity** * **product.unit_per_product**)/SUM(Distinct r**eceipt.id**)

The service endpoint used is **/sema/dashboard/site/receipt-summary**

## Volume By Sales Channel

Volume by channel shows a pie chart of volume sold via the different sales channels.

The service endpoint used is **/sema/dashboard/site/receipt-summary**

## Volume By Sales Channel and Income level

Volume
 by sales channel and income levels show horizontal bar charts for 
different income ranges where each bar displays the volumes sold via the
 various sales channels . The additional requirement is that **customer_account.income_level **be populated.

The service endpoint used is **/sema/dashboard/site/receipt-summary**

## Volume By Sales Channel and Payment Type

Volume
 by sales channel and payment types show horizontal bar charts for 
different payment types where each bar displays the volumes sold via the
 various sales channels . The additional requirements are that **receipt.amount_cash,** **receipt.amount_loan**, **receipt.amount_mobile**, **receipt.amount_card **be populated.

The service endpoint used is **/sema/dashboard/site/receipt-summary**