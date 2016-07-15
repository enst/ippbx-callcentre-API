# HTTP API: SIP User # 
RESTful url:  api/sipuser/{UserID}      {UserID} like "sipuser:*"

## GET /SIPUsers ##
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
## GET api/sipuser/{UserID} ##
Get single SIP user.

```
{
 the same as above
}
```

## PUT api/sipuser/{UserID} ##
Can change one or multiple fields. 
! Can't change UserID. !

```
{"password":"123123"}
```

## DELETE api/sipuser/{UserID} ##


