disqus: sema-docs

Returns an array of kiosks. Note that many of the subsequent SEMA web services will require a kiosk identifier.

## Endpoints
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/kiosks

## Headers

| Header | Required | Example | Description
| ------ | -------- | ------- | -----------
| Authorization	| YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

## Path Parameters
None

## Query Parameters
None

## Sample request

!!! note
    The token length is reduced in size

```
curl --header "Authorization: Bearer <token>" http://localhost:3001/sema/kiosks
```

## Sample Response
```json
{
    "kiosks": [
        {
            "id": 2,
            "name": "Kiswa",
            "region_id": 2
        }
    ]
}
```


