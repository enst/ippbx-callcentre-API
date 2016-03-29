# Routes
## GET or PUT /routes/{context}
/routes/public
```javascript
[
  {"regex" : "+16471234567", "dialplan" : "answer_queue"},
  {"regex" : ".*", "dialplan" : "answer_menu"}
]
```
/routes/default
```javascript
[
  {"regex" : "^2\d{2}$", "dialplan" : "internal"}, 
  {"regex" : "^\*98$", "dialplan" : "check_voicemail"},
  {"regex" : ".*" , "dialplan" : "external"}
]
```
{context} is the dialplan context in FreeSWITCH. "default" is for calls originate from internal extension; "public" is for inbound calls from external.

In Redis, they should be stored in routes:default or routes:public.


# Dialplan
## GET /dialplan/{dilaplan_id}
Get a dialplan node by dialplan (node) id. A call can be jumped in the dialplan tree.
Each dialplan has a module and may have one or more properties (key-value pairs).

### queue
```javascript
{
  "module": "queue",
  "id": "q0"
}
```

### call out
```javascript
{
  "module": "callout",
  "max_ring_time": "20"
}
```
Note: Using integer may be better for max_ring_time but it seems everything in Redis is a string. 

### group call
```javascript
{
  "module": "callout",
  "numbers": ["1000", "1003"]
}
```

### answer
```javascript
{
  "module": "answer",
  "next": "menu"
}
```
It'll jump to the "next" node after answered.

### menu
```javascript
{
  "module": "menu",
  "dtmf": {
     "0": "queue",
     "1": "group",
     "1XXX": "int"}
}
```

### voicemail
* Leave a message.
```javascript
{
  "module": "voicemail"
}
```
* Check mailbox.
```javascript
{
  "module": "voicemail",
  "type": "check"
}
```

## PUT /dialplan/{dialplan_id}
Create or update a dialplan node.
The JSON is in the same format as GET.

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
    "agent_wrapup_time": "5",
    "agents": [
      "agent0",
      "agent1"
    ],
    "id": "q0"
  },
  {
    "agent_wrapup_time": "undefined",
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
  "agent_wrapup_time": "5",
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
