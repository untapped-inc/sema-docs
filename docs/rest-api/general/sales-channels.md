disqus: sema-docs

The Sema service supports different sales channels. Sales channels allow product pricing and availability to be customized. For example, a product could be priced differently through the retail and wholesaler sales channels.

## Endpoints
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/sales-channels

## Headers
| Header | Required	| Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

## Path Parameters
None

## Query Parameters
None

## Sample request
```
curl --header "Authorization: Bearer <token>" http://localhost:3001/sema/sales-channels
```

## Sample Response
```json
{
    "salesChannels": [
        {
            "id": 2,
            "name": "walkup",
            "description": null
        },
        {
            "id": 3,
            "name": "reseller",
            "description": null
        }
    ]
}
```