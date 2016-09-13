# Subscription

## GET /subscription
Type "slack" can post a notification message to your slack channel.
```
{
    "Answer": [
        {
            "type": "json",
            "url": "httt://..."
        }
    ],
    "NewCall": [
        {
            "type": "slack",
            "url": "https://..."
        }
    ],
    "Ringing": [
        {
            "type": "json",
            "url": "http://..."
        }
    ]
}
```
## PUT /subscription
The same JSON format as in GET is used.

##Event Callback

* NewCall
```
{
  "caller_id_name": "Name",
  "caller_id_number": "+15141234567",
  "destination_number": "16471234567",
  "domain": "sip.abc.example.com",
  "event": "NewCall",
  "event_time": 1469122519879,
  "start_time": 1469122519879
}
```
* Ringing
```
{
  "caller_id_name": "Name",
  "caller_id_number": "+15141234567",
  "destination_number": "16471234567",
  "domain": "sip.abc.example.com",
  "event": "Ringing",
  "id": "b8b0dfb4-47c9-4bf8-a3f0-854ae3fbf4e6",
  "queue": "canada",
  "event_time": 1469122520301
  "start_time": 1469122519879
}
```
* Answer (similar to Ringing)
