disqus: sema-docs

# The REST API Server

This section documents the REST services offered by the SEMA endpoints. In the future, we will use a software for this. i.e.: <a href="https://swagger.io/" target="_blank">Swagger</a>

!!! note
    The terms `site` and `kiosk` are interchangeable.

## Summary

### General

| Endpoint                 | Description                                            
| ------------------------ | -------
| [sema/health-check](/sema-docs/rest-api/general/health-check/)	| Service availability
| [sema/login](/sema-docs/rest-api/general/login/)	| Logs in via user name/password
| [sema/kiosks](/sema-docs/rest-api/general/kiosks/) | List all sites (a.k.a. kiosks)
| [sema/products](/sema-docs/rest-api/general/products/) | Retrieve product data, skus, etc.
| [sema/sales-channels](/sema-docs/rest-api/general/sales-channels/) | Retrieve sales channels
| [sema/customer-types](/sema-docs/rest-api/general/customer-types/) | Retrieve customer types

### Point of Sale (POS) specific

!!! note
    A POS tablet manages one site

| Endpoint            | Description                                            
| ------------------------ | -------
| [sema/site/customers](/sema-docs/rest-api/pos/customers/) | CRUD for managing customer accounts from the POS application
| [sema/site/receipts](/sema-docs/rest-api/pos/receipts/) | Send receipts from POS to the sema service
| [sema/site/product-mrps](/sema-docs/rest-api/pos/product-mrps/) | Gets pricing for products base on site and sales-channel

### Dashboard/Reports specific

| Endpoint            | Description                                            
| ------------------------ | -------
| [sema/dashboard/site/customer-summary](/sema-docs/rest-api/dashboard/customer-summary/) | Returns demographics information on customers
| [sema/dashboard/site/receipt-summary](/sema-docs/rest-api/dashboard/receipt-summary/) | Returns water volume and sales information organized by sales channel and filtered by customer information
| [sema/dashboard/site/sales-summary](/sema-docs/rest-api/dashboard/sales-summary/) | Summarizes sales data
| [sema/dashboard/site/water-summary](/sema-docs/rest-api/dashboard/water-summary/)	| Sales data by vendor
| [sema/dashboard/site/water-chart](/sema-docs/rest-api/dashboard/water-chart/) | Historical sales by sales distribution channel
| [sema/dashboard/site/sales-by-channel-history](/sema-docs/rest-api/dashboard/sales-by-channel-history/) | Historical data on sales organized by sales channel