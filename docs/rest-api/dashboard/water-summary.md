disqus: sema-docs

Returns information on water operations such as production, wastage, pressure and flow rate values.

## Endpoints
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/dashboard/site/water-summary

## Headers
| Header | Required | Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

## Path Parameters
None

## Query Parameters
| Parameter | Required | Format	| Description
| --------- | -------- | ------ | -----------
| site-id | YES | Number
| begin-date | NO | String ISO 8601 format | Beginning date
| end-date | NO | String ISO 8601 format | Ending date 

## Sample request
```
curl  --header "Authorization: Bearer <token>" "http://localhost:3001/sema/dashboard/site/water-summary?site-id=1&begin-date=2017-01-01&end-date=2018-09-01"
```

## Sample Response
```json
{
    "beginDate": "2017-01-01T08:00:00.000Z",
    "endDate": "2018-09-01T07:00:00.000Z",
    "totalProduction": 7602154.24,
    "fillStation": 7316744.58,
    "pressurePreMembrane": 86.098039,
    "pressurePostMembrane": 92.492308,
    "distributionFlowRate": null,
    "productFlowRate": 10.002892,
    "sourceFlowRate": 17.993228
}
```