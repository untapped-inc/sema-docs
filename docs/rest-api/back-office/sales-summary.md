disqus: sema-docs

Gets sales summary information for a site. 

* Total customers
* Total Revenue
* Cost of goods sold
* Information on sales to each customer

## Endpoints
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/dashboard/sales/trends

## Headers
| Header | Required | Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

## Path Parameters
None

## Query Parameters
| Parameter | Required | Format	| Description
| --------- | -------- | ------ | -----------
| site-id | YES | String | The site for which information is being returned
| group-by | YES | String | Used to categorize how historical sales data is organized, i.e. by month, by year etc. (Currently the supported options are "month", "year", and "none"
| begin-date | NO | String ISO 8601 format | Beginning date for the sales info. If not specified the most recent sales data is returned
| enddate | NO | String ISO 8601 format | Ending date for the sales info. If not specified the current date is used

## Sample request
```
curl --header "Authorization: Bearer <token>" http://localhost:3001/sema/dashboard/site/sales-summary?site-id=1&begin-date=2018-04-01&end-date=2018-04-30&group-by=year
```

## Sample Response

!!! note "Notes"
    Each metric return includes a total for the date range specified plus the three most current "group-by" values. These values are used to display metric trends.
    
    Also the array of customer sales data is sorted by current sales period value (descending)
```json
{
    "beginDate": "2018-04-01T07:00:00.000Z",
    "endDate": "2018-04-30T07:00:00.000Z",
    "totalRevenue": {
        "total": 2379310,
        "period": "year",
        "periods": [
            {
                "beginDate": "2018-01-01T08:00:00.000Z",
                "endDate": "2018-04-30T07:00:00.000Z",
                "value": 774665
            },
            {
                "beginDate": "2017-01-01T08:00:00.000Z",
                "endDate": "2017-12-30T08:00:00.000Z",
                "value": 1544530
            },
            {
                "beginDate": "2016-01-01T08:00:00.000Z",
                "endDate": "2016-12-30T08:00:00.000Z",
                "value": null
            }
        ]
    },
    "totalCogs": {
        "total": 1189655,
        "period": "year",
        "periods": [
            {
                "beginDate": "2018-01-01T08:00:00.000Z",
                "endDate": "2018-04-30T07:00:00.000Z",
                "value": 387332.5
            },
            {
                "beginDate": "2017-01-01T08:00:00.000Z",
                "endDate": "2017-12-30T08:00:00.000Z",
                "value": 772265
            },
            {
                "beginDate": "2016-01-01T08:00:00.000Z",
                "endDate": "2016-12-30T08:00:00.000Z",
                "value": null
            }
        ]
    },
    "totalCustomers": {
        "total": 189,
        "period": "year",
        "periods": [
            {
                "beginDate": "2018-01-01T08:00:00.000Z",
                "endDate": "2018-04-30T07:00:00.000Z",
                "value": 28
            },
            {
                "beginDate": "2017-01-01T08:00:00.000Z",
                "endDate": "2017-12-30T08:00:00.000Z",
                "value": 96
            },
            {
                "beginDate": "2016-01-01T08:00:00.000Z",
                "endDate": "2016-12-30T08:00:00.000Z",
                "value": null
            }
        ]
    },
    "customerCount": 1133,
    "customerSales": [
        {
            "name": "Felix Dalmas",
            "id": "03d280ba-c59c-11e8-8488-ac87a31a5361",
            "period": "year",
            "gps": "",
            "total": null,
            "periods": [
                {
                    "beginDate": "2018-01-01T08:00:00.000Z",
                    "endDate": "2018-04-30T07:00:00.000Z",
                    "value": 35640
                },
                {
                    "beginDate": "2017-01-01T08:00:00.000Z",
                    "endDate": "2017-12-30T08:00:00.000Z",
                    "value": 62760
                },
                {
                    "beginDate": "2016-01-01T08:00:00.000Z",
                    "endDate": "2016-12-30T08:00:00.000Z",
                    "value": null
                }
            ]
        },
        {
            "name": "Kaliko Beach",
            "id": "c0d3c202-c59c-11e8-aff1-ac87a31a5361",
            "period": "year",
            "gps": "18.86886 -72.61301",
            "total": null,
            "periods": [
                {
                    "beginDate": "2018-01-01T08:00:00.000Z",
                    "endDate": "2018-04-30T07:00:00.000Z",
                    "value": 34195
                },
                {
                    "beginDate": "2017-01-01T08:00:00.000Z",
                    "endDate": "2017-12-30T08:00:00.000Z",
                    "value": 87930
                },
                {
                    "beginDate": "2016-01-01T08:00:00.000Z",
                    "endDate": "2016-12-30T08:00:00.000Z",
                    "value": null
                }
            ]
        },
        {
            "name": "Unregistered",
            "id": "ad2c18c2-c59b-11e8-8328-ac87a31a5361",
            "period": "year",
            "gps": "",
            "total": null,
            "periods": [
                {
                    "beginDate": "2018-01-01T08:00:00.000Z",
                    "endDate": "2018-04-30T07:00:00.000Z",
                    "value": 33285
                },
                {
                    "beginDate": "2017-01-01T08:00:00.000Z",
                    "endDate": "2017-12-30T08:00:00.000Z",
                    "value": 49405
                },
                {
                    "beginDate": "2016-01-01T08:00:00.000Z",
                    "endDate": "2016-12-30T08:00:00.000Z",
                    "value": null
                }
            ]
        },
        {
            "name": "ludieu Laguerre",
            "id": "8a9d8aec-c59c-11e8-918c-ac87a31a5361",
            "period": "year",
            "gps": "18.83785, -72.57531",
            "total": null,
            "periods": [
                {
                    "beginDate": "2018-01-01T08:00:00.000Z",
                    "endDate": "2018-04-30T07:00:00.000Z",
                    "value": 30600
                },
                {
                    "beginDate": "2017-01-01T08:00:00.000Z",
                    "endDate": "2017-12-30T08:00:00.000Z",
                    "value": 72260
                },
                {
                    "beginDate": "2016-01-01T08:00:00.000Z",
                    "endDate": "2016-12-30T08:00:00.000Z",
                    "value": null
                }
            ]
        }
    ]
}
```