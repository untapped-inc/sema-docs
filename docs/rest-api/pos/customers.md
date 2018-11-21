disqus: sema-docs

Customer services for a site/kiosk.

## GET Endpoint
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/site/customers

### Headers
| Header | Required | Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

### Path Parameters
None

### Query Parameters
| Parameter | Required | Format	| Description
| --------- | -------- | ------ | -----------
| site-id | YES | String | The site/kiosk for which the customers are being queried
| begin-date | NO | String ISO 8601 format | Beginning date for the customer info. If not specified all customers up until end-date are returned.
| end-date | NO	| String ISO 8601 format | Ending date. If not specified all customers from the begin-date are returned.
| updated-date | NO	| String ISO 8601 format | Returns all customers whose updated date is LATER than updated-date.

!!! note "Notes"
    updated-date and begin-date/end-date are mutually exclusive
    
    If no dates are specified, all customers for the site are returned

### Sample Request
```
curl --header "Authorization: Bearer <token>" http://localhost:3001/sema/site/customers?site-id=2
```

### Sample Response
```json
{
  "customers": [
    {
      "customerId": "225aee42-95f0-11e8-955a-ac87a31a5361",
      "createdDate": "2018-01-01T08:00:00.000Z",
      "updatedDate": "2018-08-08T05:47:26.000Z",
      "active": true,
      "address": "241 Mistletoe Rd Ca 95032",
      "name": "Fred O'Leary",
      "customerTypeId": 2,
      "salesChannelId": 2,
      "gpsCoordinates": "gps",
      "siteId": 2,
      "phoneNumber": "408-656-2041",
      "dueAmount": 0
    },
    {
      "customerId": "22b7a18c-95f0-11e8-9a65-ac87a31a5361",
      "createdDate": "2018-02-01T08:00:00.000Z",
      "updatedDate": "2018-02-01T08:00:00.000Z",
      "active": true,
      "address": "test_address",
      "name": "TestCustomer 2",
      "customerTypeId": 2,
      "salesChannelId": 2,
      "gpsCoordinates": "gps",
      "siteId": 2,
      "phoneNumber": "555-1313",
      "dueAmount": 0
    },
    {
      "customerId": "2312dd90-95f0-11e8-9a72-ac87a31a5361",
      "createdDate": "2018-03-01T08:00:00.000Z",
      "updatedDate": "2018-03-01T08:00:00.000Z",
      "active": true,
      "address": "test_address",
      "name": "TestCustomer 3",
      "customerTypeId": 2,
      "salesChannelId": 2,
      "gpsCoordinates": "gps",
      "siteId": 2,
      "phoneNumber": "555-1414",
      "dueAmount": 0
    },
  ]
}
```

## POST Endpoint
<span class="status-macro aui-lozenge conf-macro output-inline post-method">POST</span> sema/site/customers

Used to create a customer.

### Headers
| Header | Required	| Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login
| Content-Type | YES | Content-Type: application/json

### Path Parameters
None

### Query Parameters
None

### POST Body (JSON formatted)
| Field Name | Required | Type | Description |
| ---------- | -------- | ---- | -----------
| customerId | NO | string | Unique id for the customer (uuid). If not specified, the REST service will create this field
| siteId | YES | number	| Kiosk/Site identifier
| address | YES	| string | address
| name | YES | string | User name
| customerTypeId | YES | number	| Customer type identifier (sema/customer-types)
| salesChannelId | YES | number	| Sales channel identifier
| phoneNumber | YES	| string | Phone number
| gpsCoordinates | NO | string | GPS coordinates, (',' separated)
| createdDate | NO | String	ISO 8601 format | If not specified, the REST service will create this with the current date/time
| updatedDate | NO | String	ISO 8601 format | If not specified, the REST service will set this the same as the createdDate
| gender | NO | string

### Sample request
```
curl --header "Authorization: Bearer <token>" -d '{"name":"post customer","siteId":1,"customerTypeId":1,"salesChannelId":3,"address":"1234 main st","phoneNumber":"555-1212"}' -H "Content-Type: application/json" -X POST localhost:3001/sema/site/customers/
```

### Sample Response
```json
{
    "customerId": "6794d3c0-d0cd-11e8-8c05-1174232b1a96",
    "createdDate": "2018-10-15T22:55:25.948Z",
    "updatedDate": "2018-10-15T22:55:25.948Z",
    "active": true,
    "address": "1234 main st",
    "name": "post customer",
    "customerTypeId": 1,
    "salesChannelId": 3,
    "gpsCoordinates": "",
    "siteId": 1,
    "phoneNumber": "555-1212",
    "dueAmount": 0
}
```

## PUT Endpoint
<span class="status-macro aui-lozenge conf-macro output-inline put-method">PUT</span> sema/site/customers/{customerId}

Used to update a customer. 

!!! note
    If a customer is referenced by another entity, it cannot be deleted. Instead it will be deactivated.

### Headers
| Header | Required	| Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login
| Content-Type | YES | Content-Type: application/json

### Path Parameters

CustomerId - The id of the customer being updated

### Query Parameters
None

### PUT Body (JSON formatted)
| Field Name | Required | Type | Description |
| ---------- | -------- | ---- | -----------
| active | NO | boolean	| Used to activate/deactivate a customer
| address | NO	| string | address
| name | NO | string | User name
| customerTypeId | YES | number	| Customer type identifier (sema/customer-types)
| salesChannelId | NO | number	| Sales channel identifier
| phoneNumber | NO	| string | Phone number
| gpsCoordinates | NO | string | GPS coordinates, (',' separated)
| createdDate | NO | String	ISO 8601 format | If not specified, the REST service will create this with the current date/time
| updatedDate | NO | String	ISO 8601 format | If not specified, the REST service will set this the same as the createdDate
| gender | NO | string

### Sample request
```
curl --header "Authorization: Bearer <token>" -d '{ "gpsCoordinates":"41.2865,174.7762"}' -H "Content-Type: application/json" -X PUT localhost:3001/sema/site/customers/6794d3c0-d0cd-11e8-8c05-1174232b1a96
```

### Sample Response
```json
{
    "customerId": "6794d3c0-d0cd-11e8-8c05-1174232b1a96",
    "createdDate": "2018-10-16T05:55:25.000Z",
    "updatedDate": "2018-10-15T23:12:42.418Z",
    "active": true,
    "address": "1234 main st",
    "name": "post customer",
    "customerTypeId": 1,
    "salesChannelId": 3,
    "gpsCoordinates": "41.2865,174.7762",
    "siteId": 1,
    "phoneNumber": "555-1212",
    "dueAmount": 0
}
```

## DELETE Endpoint

<span class="status-macro aui-lozenge conf-macro output-inline delete-method">DELETE</span> sema/site/customers/{customerId}

Used to delete a customer.

!!! note
    If a customer is referenced by another entity, it cannot be deleted. Instead it will be deactivated via `PUT`.

### Headers
| Header | Required	| Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login
| Content-Type | YES | Content-Type: application/json

### Path Parameters
CustomerId - The id of the customer being deleted

### Query Parameters
None

### Sample request
```
curl --header "Authorization: Bearer <token>"  -X DELETE localhost:3001/sema/site/customers/6794d3c0-d0cd-11e8-8c05-1174232b1a96
```