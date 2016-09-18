# Callback
## POST /callback
```
{
  "type": "external",
  "from": "+16471234567",
  "to": "600"
}
```
This example will call the "from" number first. Once it answered, it'll be transfered to the "to" number 600.
The "to" number can be an internal extension, queue or conference room, etc,.
