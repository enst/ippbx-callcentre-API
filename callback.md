# Callback
## POST /callback
### type "exterenal"
```
{
  "type": "external",
  "from": "+16471234567",
  "to": "600"
}
```
This example will call the "from" number first. Once it answered, it'll be transfered to the "to" number 600.
The "to" number can be an internal extension, queue or conference room, etc,.

### type "agent"
```
{
  "type": "agent",
  "to": "+16471234567",
  "from": "agent1" 
}
```

In this case, agent1 will ring first. Once agent1 answered, the outbound call will be made.
