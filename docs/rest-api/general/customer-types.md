disqus: sema-docs

The Sema service supports different types of customers. Examples of customer types are school, church, walk-up etc...

## Endpoints
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/customer-types

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
curl --header "Authorization: Bearer <token>" http://localhost:3001/sema/customer-types
```

## Sample Response
```json
{
    "customerTypes": [
        {
            "id": 2,
            "name": "generic",
            "description": null
        },
        {
            "id": 3,
            "name": "anonymous",
            "description": null
        }
    ]
}
```