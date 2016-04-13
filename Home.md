### * Every API path implicitly has the prefix "/api/".

#[Routes](routes)
#[Callflow](callflow)

# Agent
## GET /agents
Get all agents. "contact" is the SIP account of the VOIP client.
```javascript
[
  {
    "contact": "1000",
    "id": "agent0",
    "idle_since": "0",
    "state": "waiting",
    "status": "logged_in"
  },
  {
    "contact": "1003",
    "id": "agent1",
    "idle_since": "0",
    "state": "waiting",
    "status": "logged_in"
  }
]
```

## GET /agent/{agent_id}
```javascript
{
  "contact": "1000",
  "id": "0",
  "idle_since": "0",
  "state": "waiting",
  "status": "logged_in"
}
```

## PUT /agent/{agent_id}
One or multiple fields can be updated.
```javascript
{"status": "logged_in"}
```

## DELETE /agent/{agent_id}

# Queue

## GET /queues
Get all queues.
```javascript
[
  {
    "agent_wrapup_time": 5,
    "max_ring_time": 60, 
    "agents": [
      "agent0",
      "agent1"
    ],
    "id": "q0"
  },
  {
    "agents": [
      "agent0",
      "agent1",
      "agent3"
    ],
    "id": "q1"
  }
]
```

## GET /queue/{queue_id}
```javascript
{
  "agent_wrapup_time": 5,
  "agents": [
    "0",
    "1"
  ],
  "id": "0"
}
```

## PUT /queue/{queue_id}
```javascript
{"agents": ["0", "1", "2"]}
```

## DELETE /queue/{queue_id}

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
