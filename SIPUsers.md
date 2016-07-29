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
Get single SIP user.

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
Can change one or multiple fields. 
! Can't change UserID. !

```
{"password":"123123"}
```

## DELETE api/sipuser/{UserID}


