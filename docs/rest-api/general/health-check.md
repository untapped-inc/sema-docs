disqus: sema-docs

Determines the status of the SEMA service.

## Endpoints
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/health-check/

## Headers
None

## Path Parameters
None

## Query Parameters
None

## Sample request
```
curl "http://localhost:3001/sema/health-check"
```

## Sample Response
```json
{"server":"Ok","database":"Ok","version":"0.0.1.4","schema":"sema_sample_core"}
```


