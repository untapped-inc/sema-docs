disqus: sema-docs

The Water Operations page shows information on water production, 
quality etc,  filtered by date. When the date filter chosen is "Total", 
the  total metrics of water operations is shown. When a date range is 
specified, the water operations  for the date filter period is shown.

## Total Production

Shows water production as "**501759 liters, Wed Jan 31, 2018**".
 If there is no Date filter, total water production up to the current 
date is displayed. Otherwise production for the period selected by the 
date filter is displayed. Water production is calculated from the "Volume" parameter at the sampling site "B:Product:"

The service endpoint is **/sema/dashboard/site/water-summary**

## Total Wastage

Shows the difference in water production at the source, ("B:Product) and production at the "Fill" (D:Fill). 

The service endpoint is **/sema/dashboard/site/water-summary**

## Pressure

Shows the average water pressure in different parts of the water production system for the selected period. Details TBD

The service endpoint is **/sema/dashboard/site/water-summary**

## Flow Rate

Shows average Product/Source and Distribution flow rates for the selected period.

The service endpoint is **/sema/dashboard/site/water-summary**

## Production Chart

Shows
 a bar chart of daily water production over the period. Note that daily 
production is calculated as the (maximum volume reading -  minimum 
volume reading) per day

The service endpoint is** /sema/dashboard/site/water-chart**

## Total Chlorine

Shows a line chart of Total Chlorine levels over the period.

The service endpoint is** /sema/dashboard/site/water-chart**

## Total Dissolved Solids

Shows a line chart of Total Dissolved solids over the period

The service endpoint is** /sema/dashboard/site/water-chart**
