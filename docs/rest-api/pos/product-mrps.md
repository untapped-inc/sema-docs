disqus: sema-docs

Product - sales-channel mappings. This service returns information on how products are priced for each kiosk/site and sales channel combination. Pricing information includes both sales price plus the cost of goods sold.

## Endpoints
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/site/product-mrps

| Header | Required | Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

## Path Parameters
None

## Query Parameters
| Parameter | Required | Format	| Description
| --------- | -------- | ------ | -----------
| site-id | YES | String | The site(kiosk) for which the customers are being queried
| updated-date	| NO | string ISO 8601 format | Returns all product mrps whose updated date is LATER than updated-date.

## Sample request
```
curl --header "Authorization: Bearer <token>" http://localhost:3001/sema/site/product-mrps?site-id=2
```

## Sample Response
```json
{
    "productMRPs": [
        {
            "id": 1,
            "siteId": 2,
            "productId": 17,
            "salesChannelId": 2,
            "priceAmount": 2600.01,
            "currencyCode": "UGX",
            "cogsAmount": 1300
        },
        {
            "id": 2,
            "siteId": 2,
            "productId": 17,
            "salesChannelId": 3,
            "priceAmount": 2340,
            "currencyCode": "UGX",
            "cogsAmount": 1300
        },
        {
            "id": 3,
            "siteId": 2,
            "productId": 18,
            "salesChannelId": 2,
            "priceAmount": 4000,
            "currencyCode": "UGX",
            "cogsAmount": 2000
        },
        {
            "id": 4,
            "siteId": 2,
            "productId": 18,
            "salesChannelId": 3,
            "priceAmount": 3600,
            "currencyCode": "UGX",
            "cogsAmount": 2000
        },
        {
            "id": 5,
            "siteId": 2,
            "productId": 19,
            "salesChannelId": 2,
            "priceAmount": 20000,
            "currencyCode": "UGX",
            "cogsAmount": 10000
        },
        {
            "id": 6,
            "siteId": 2,
            "productId": 19,
            "salesChannelId": 3,
            "priceAmount": 18000,
            "currencyCode": "UGX",
            "cogsAmount": 10000
        },
        {
            "id": 7,
            "siteId": 2,
            "productId": 20,
            "salesChannelId": 2,
            "priceAmount": 25000,
            "currencyCode": "UGX",
            "cogsAmount": 13000
        },
        {
            "id": 8,
            "siteId": 2,
            "productId": 20,
            "salesChannelId": 3,
            "priceAmount": 22500,
            "currencyCode": "UGX",
            "cogsAmount": 13000
        },
        {
            "id": 9,
            "siteId": 2,
            "productId": 21,
            "salesChannelId": 2,
            "priceAmount": 25000,
            "currencyCode": "UGX",
            "cogsAmount": 13000
        },
        {
            "id": 10,
            "siteId": 2,
            "productId": 21,
            "salesChannelId": 3,
            "priceAmount": 22500,
            "currencyCode": "UGX",
            "cogsAmount": 13000
        }
    ]
}
```