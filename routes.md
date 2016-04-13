# Routes
## GET or PUT /routes/{context}
/routes/public
```javascript
[
  {"regex" : "+16471234567", "callflow" : "answer_queue"},
  {"regex" : ".*", "callflow" : "answer_menu"}
]
```
/routes/default
```javascript
[
  {"regex" : "^2\\d{2}$", "callflow" : "int"},
  {"regex" : "^\\*97$", "caller_regex":"^206$", "callflow" : "check_voicemail"},
  {"regex": "^1999$", "callflow": "queue"},
  {"regex" : "^1\\d{3}$", "callflow" : "int"},
  {"regex" : "^\\*98$", "callflow" : "check_voicemail"},
  {"regex" : ".*" , "callflow" : "ext"}
]
```
{context} is the dialplan context in FreeSWITCH. "default" is for calls that originate from internal extensions; "public" is for inbound calls that from external.