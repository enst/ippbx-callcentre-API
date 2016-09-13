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
    "agent0",
    "agent1"
  ],
  "max_ring_time": "15",
  "max_waiting_time": "29",
  "moh": "ringback",
  "strategy": "ring_all"
}
```
The default strategy is "longest_idle".

## POST /queue/{queue_id}
Use the same JSON format as in GET

## DELETE /queue/{queue_id}

## PUT /queue/{queue_id}/agents
```javascript
["agent0", "agnet1", "agent2"]
```
