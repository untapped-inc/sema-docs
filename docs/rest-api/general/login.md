disqus: sema-docs

Log into service. Login will return a Json Web Token. This token is required to authorize all other web services except for `sema/health-check`.

For use in subsequent web services, clients must add the Authorization header as:

`Authorization: Bearer <token>` where `<token>` is as described below in the body of a successful authorization

The token returned will expire after 24 hours. (Clients should keep track of the token expiration time and acquire a new token before the token expiration time)

## Endpoints

<span class="status-macro aui-lozenge conf-macro output-inline post-method">POST</span> sema/login

## Headers
None

## Path Parameters
None

## Query Parameters
None

## POST Body (JSON formatted)
| Field Name | Required | Type | Description
| ---------- | -------- | ---- | -----------
| usernameOrEmail | YES	| string | User name or email address. (Email address should be used to enable password recovery)
|password | YES	| string

## Sample request
```
curl --header "Content-Type: application/json" --request POST --data '{"usernameOrEmail":"<username>","password":"<password>"}' http://localhost:3001/sema/login
```

## Sample Response
```json
{
    "version": "0.0.1.0",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwidXNlcm5hbWUiOiJhZG1pbmlzdHJhdG9yIiwiZW1haWwiOiJhZG1pbkB1bnRhcHBlZC1pbmMuY29tIiwiY3JlYXRlZF9hdCI6IjIwMTgtMDUtMzBUMDE6MTQ6NDcuMDAwWiIsInVwZGF0ZWRfYXQiOiIyMDE4LTA2LTE0VDE0OjU4OjUyLjAwMFoiLCJmaXJzdF9uYW1lIjoiVGVzdCIsImxhc3RfbmFtZSI6IlVzZXIiLCJhY3RpdmUiOnRydWUsInJvbGVzIjpbeyJjb2RlIjoiYWRtaW4iLCJ1c2VyX3JvbGUiOnsicm9sZV9pZCI6MywidXNlcl9pZCI6MSwiaWQiOjV9fSx7ImNvZGUiOiJocSIsInVzZXJfcm9sZSI6eyJyb2xlX2lkIjo0LCJ1c2VyX2lkIjoxLCJpZCI6OH19XSwiaWF0IjoxNTMzNzU0MDc0LCJleHAiOjE1MzM4NDA0NzR9.9fIqWdBUeBh73RpIbIg_UHW9BLqSWfgkR9BzPfzJLEY"
}
```