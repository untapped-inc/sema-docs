disqus: sema-docs

Gets demographics information on customers.

## Endpoints

<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/dashboard/site/customer-summary

## Headers
| Header | Required | Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

## Path Parameters
None

## Query Parameters
| Parameter | Required | Format	| Description
| --------- | -------- | ------ | -----------
| site-id | YES | String | The site/kiosk for which sales info is being returned
| begin-date | NO | String ISO 8601 format | Beginning date  for customers included
| end-date | NO	| String ISO 8601 format | Ending date  for customers included
| income-gt<br><br>income-lt | NO | Number | Used to filter customers by income. If Both income-lt and income-gt are specified, all customers whose income is between the ranges will be returned. If income-lt is specified, customers whose income below the value will be included. If income-gt is specified, customers whose income above the value will be included
| gender | NO| String | 'M' or 'F'. Used to filter customers by gender
| distance-gt<br><br>distance-lt | NO | Number | Used to filter customers by distance. If Both distance-lt and distance-gt are specified, all customers whose distance is between the ranges will be returned. If distance-lt is specified, customers whose distance below the value will be included. If distance-gt is specified, customers whose distance above the value will be included

!!! note
    If either `begin-date` or `end-date` is specified, both dates must be included.

## Sample request
```
curl --header "Authorization: Bearer <token>" http://localhost:3001/sema/dashboard/site/customer-summary?site-id=1&begin-date=2016-02-02&end-date=2019-09-01&income-gt=2&income-lt=8
```

## Response

The response includes  the count of customers created that meet the filter criteria plus the potential consumer base for the kiosk.

## Sample Response
```json
{
    "beginDate": "2016-02-02T08:00:00.000Z",
    "endDate": "2019-09-01T07:00:00.000Z",
    "incomeGreaterThan": "2",
    "incomeLessThan": "8",
    "customerCount": 52,
    "consumerBase": 400
}
```