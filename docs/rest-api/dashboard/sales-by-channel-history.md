disqus: sema-docs

Gets historical data on sales organized by sales channel.

## Endpoints

<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/dashboard/site/sales-by-channel-history

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
| begin-date | NO | String ISO 8601 format | Beginning date
| end-date | NO	| String ISO 8601 format | End date
| group-by | NO | String ISO 8601 format | Aggregrates sales data by "month" or "day". Default is "day"

!!! note
    If neither ending date nor beginning date are specified, data for the current year is returned.

## Sample request
```
curl --header "Authorization: Bearer <token>" "http://localhost:3001/sema/dashboard/site/sales-by-channel-history?site-id=1&begin-date=2018-01-01&end-date=2018-09-01"
```

## Sample Response
```json
{
    "salesByChannel": {
        "beginDate": "2018-01-01T08:00:00.000Z",
        "endDate": "2018-09-01T07:00:00.000Z",
        "groupBy": "day",
        "datasets": [
            {
                "salesChannel": "revendeur",
                "type": "total",
                "data": []
            },
            {
                "salesChannel": "revendeur",
                "type": "cogs",
                "data": []
            },
            {
                "salesChannel": "distributeur",
                "type": "total",
                "data": []
            },
            {
                "salesChannel": "distributeur",
                "type": "cogs",
                "data": []
            }
        ]
    }
}
```