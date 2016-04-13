### * Every API path implicitly has the prefix "/api/".

#[Routes](routes)
#[Callflow](callflow)
#[Agent](agent)
#[Queue](queue)

# HTTP API: SIP User # 
## GET /SIPUsers ##
Get all SIP users. "UserID" is the SIP account.
```
#!json
[
{
  "UserID":"UserID:001",
  "DisplayName":"John",
  "Password":"123123",
  "SIPPassword":"123456",
  "PhoneVendor":"",
  "PhoneModel":"",
  "PhoneMAC":"",
},
...
]
```
## GET /SIPUser/{UserID} ##
Get single SIP user.

```
#!json

{
 the same as above
},
```

## PUT /SIPUser/{UserID} ##
Can change one or multiple fields. 
! Can't change UserID. !

```
#!json

{"DisplayName":"John",}
```

## DELETE /SIPUser/{UserID} ##

# HTTP API: SIP system configuration #
## GET /SIPSysCfg ##
```
#!json

{
  "UDPEnable":"",
  "UDPPort":"",
  "TCPEnable":"",
  "TCPPort":"",
  "TLSEnable":"",
  "TLSPort":"",
  "AutoProvisioning": {
    "Enabled":"1",
    "SvrIPv4Addr":"",
  },
}
```
## PUT /SIPSysCfg ##
Can change single or multiple items.
