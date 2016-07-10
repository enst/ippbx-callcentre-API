# Agent
## GET /agents
Get all agents. "contact" is the SIP account of the VOIP client.
```javascript
[
  {
    "contact": "1000"
  },
  {
    "contact": "1003"
  }
]
```

## GET /agent/{agent_id}
```javascript
{
  "contact": "1000"
}
```

## PUT /agent/{agent_id}
One or multiple fields can be updated.
```javascript
{"contact": "1001"}
```

## DELETE /agent/{agent_id}

## GET /status/agent/{agent_id}
```javascript
{
    "state": "waiting",
    "status": "logged_in"
}
```

## PUT /status/agent/{agent_id}
```javascript
{
    "status": "logged_in"
}
```
