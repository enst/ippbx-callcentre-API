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