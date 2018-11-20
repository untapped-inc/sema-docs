# The REST API Server

This section documents the REST services offered by the SEMA endpoints.

!!! note
    The terms `site` and `kiosk` are interchangeable.

## Summary

### General

| Endpoint                 | Description                                            
| ------------------------ | -------
| sema/health-check	| Service availability
| sema/login	| Logs in via user name/password
| sema/kiosks | List all sites (a.k.a. kiosks)
| sema/products | Retrieve product data, skus, etc.
| sema/sales-channels | Retrieve sales channels
| sema/customer-types | Retrieve customer types

### Point of Sale (POS) specific

!!! note
    A POS tablet manages one site

| Endpoint            | Description                                            
| ------------------------ | -------
| sema/site/customers | CRUD for managing customer accounts from the POS application
| sema/site/receipts | Send receipts from POS to the sema service
| sema/site/product-mrps | Gets pricing for products base on site and sales-channel

### Dashboard/Reports specific

| Endpoint            | Description                                            
| ------------------------ | -------
| sema/dashboard/site/customer-summary | Returns demographics information on customers
| sema/dashboard/site/receipt-summary | Returns water volume and sales information organized by sales channel and filtered by customer information
| sema/dashboard/site/sales-summary | Summarizes sales data
| sema/dashboard/site/water-summary	| Sales data by vendor
| sema/dashboard/site/water-chart | Historical sales by sales distribution channel