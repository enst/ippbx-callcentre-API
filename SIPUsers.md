# HTTP API: SIP User
RESTful url:  /api/sipuser/{UserID}

## GET /SIPUsers
Get all SIP users. "id" is the SIP account.
```
[
{
  "id": "201",
  "password":"123123",
},
...
]
```
## GET api/sipuser/{UserID}
Get a single SIP user.

```
{
  "password": "123123",
  "vm-password": "user-choose",
  "vm-mailto": "example@gmail.com",
  "vm-mailfrom": "notification@example.com",
  "vm-email-all-messages": "true",
  "vm-attach-file": "true"
}
```

## PUT api/sipuser/{UserID}
One or more fields can be changed. UserID can't be changed!

```
{"password":"123123"}
```

## DELETE api/sipuser/{UserID}


