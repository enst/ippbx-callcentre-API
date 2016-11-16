# Callflow
## GET /callflow/{callflow_id}
Get a callflow node by callflow (node) id. A call can be jumped in the dialplan tree.
Each callflow should have a module and may have one or more properties.

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
  "max_ring_time": 20,
  "voicemail": "answer_voicemail"
}
```

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
    "audio": "ivr.wav",
    "dtmf": {
        "100": "conf",
        "2XX": "int",
        "3XX": "int"
    },
    "module": "menu"
}
```

### voicemail
* Leave a message.  (no answer extension)
```javascript
{
  "module": "voicemail"
}
```
* Leave message in a specified mailbox.
```javascript
{
  "module": "voicemail",
  "box" : "201"
}
```
* Check mailbox.
```javascript
{
  "module": "voicemail",
  "type": "check"
}
```
### schedule
```javascript
{
	"module": "schedule",
	"default": "off",
	"rules": [{
		"days_of_week": [1, 2, 3, 4, 5],
		"start": "09:00",
		"end": "17:00",
		"callflow": "on"
	}]
}
```
### app
* call freeswitch application
```javascript
{
  "module": "app",
  "command": "conference",
  "data": "conf_room_1"
}
```

## PUT /callflow/{callflow_id}
Create or update a dialplan node.
The JSON is in the same format as GET.
