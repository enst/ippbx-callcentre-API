# HTTP API: SIP User # 
RESTful url:  api/sipuser/{UserID}      {UserID} like "sipuser:*"

## GET /SIPUsers ##
Get all SIP users. "userid" is the SIP account.
```
[
{
  "userid":"sipuser:001",
  "display_name":"John",
  "password":"123123",
  "vm_password":"123456"
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
{"display_name":"John"}
```

## DELETE api/sipuser/{UserID} ##


