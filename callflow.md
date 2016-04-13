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
  "max_ring_time": 20
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

## PUT /callflow/{callflow_id}
Create or update a dialplan node.
The JSON is in the same format as GET.