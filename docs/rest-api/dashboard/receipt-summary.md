disqus: sema-docs

Gets water volume and sales information  organized by sales channel, and filtered by customer income and/or payment type.

## Endpoints

<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/dashboard/site/receipt-summary

## Headers
| Header | Required | Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

## Path Parameters
None

## Query Parameters
| Parameter | Required | Format	| Description
| --------- | -------- | ------ | -----------
| site-id | YES | String | The site for which information is requested
| type | YES | String | Must be "sales-channel"
| begin-date | NO | String ISO 8601 format
| end-date | NO	| String ISO 8601 format
| income-gt<br><br>income-lt | NO | Number | Used to filter customers by income. If Both income-lt and income-gt are specified, all customers whose income is between the ranges will be returned. If income-lt is specified, customers whose income below the value will be included. If income-gt is specified, customers whose income above the value will be included
| payment-type | NO | String | Used to filter sales by payment type. May be one of: 'cash', 'mobile', 'loan' or 'card'.

!!! note
    If either `begin-date` or `end-date` are specified, both must be included.

## Sample request
```
curl --header "Authorization: Bearer <token>" http://localhost:3001/sema/dashboard/site/receipt-summary?site-id=1&begin-date=2017-01-01&end-date=2018-09-01&type=sales-channel&payment-type=cash
```

## Sample Response
```json
{
    "beginDate": "2017-01-01T08:00:00.000Z",
    "endDate": "2018-09-01T07:00:00.000Z",
    "type": "sales-channel",
    "volume": {
        "data": [
            {
                "salesChannel": "Household",
                "volume": 3075.8
            },
            {
                "salesChannel": "Main Station",
                "volume": 9812.9
            },
            {
                "salesChannel": "Access Points",
                "volume": 6722.5
            },
            {
                "salesChannel": "Prepaid Meter",
                "volume": 0
            }
        ]
    },
    "total": {
        "data": [
            {
                "salesChannel": "Household",
                "total": 197.2
            },
            {
                "salesChannel": "Main Station",
                "total": 795.6
            },
            {
                "salesChannel": "Access Points",
                "total": 428.4
            },
            {
                "salesChannel": "Prepaid Meter",
                "total": 0
            }
        ]
    },
    "paymentType": "cash"
}
```