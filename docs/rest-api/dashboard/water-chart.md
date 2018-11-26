disqus: sema-docs

Gets historical data on a water reading (production, chlorine, total dissolved solids).

## Endpoints
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span>  sema/dashboard/site/water-chart

## Headers
| Header | Required | Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

## Path Parameters
None

## Query Parameters
| Parameter | Required | Format	| Description
| --------- | -------- | ------ | -----------
| site-id | YES | Number | The site for which sales info is being returned
| type | YES | String | Must be one of "totalchlorine", "production" or "tds"
| begin-date | NO | String ISO 8601 format | Beginning date
| end-date | NO | String ISO 8601 format | Ending date.
| group-by | NO | String, optional when type is "production" either month or day default is "day". Water production is aggregated daily unless "month" is specified

!!! note
    If neither ending date nor beginning date are specified, data for the current year is returned

## Sample request
```
curl --header "Authorization: Bearer <token>" "http://localhost:3001/sema/dashboard/site/water-chart?site-id=1&type=production&begin-date=2018-01-01&end-date=2018-09-01"
```

## Sample Response
```json
{
    "beginDate": "2018-01-01T08:00:00.000Z",
    "endDate": "2018-09-01T07:00:00.000Z",
    "type": "production",
    "data": {
        "time": [
            "2018-01-01T08:00:00.000Z",
            "2018-01-02T08:00:00.000Z",
            "2018-01-03T08:00:00.000Z",
			...
		],
        "values": [
            15915.200000000186,
            15979.810000000056,
            15927.85999999987,
			...
		]
	}
}
```
