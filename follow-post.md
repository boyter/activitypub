# Follow -> Post


Published time should be in [RFC3339](https://www.rfc-editor.org/rfc/rfc3339) and look like the following `2006-01-02T15:04:05Z07:00`


```json
{
   "@context": "https://www.w3.org/ns/activitystreams",
   "actor": "https://some.instance/u/%s",
   "id": "https://some.instance/u/%s/sub/%s",
   "object": "%s",
   "published": "%s",
   "to": "https://some.instance/u/%s/inbox",
   "type": "Follow"
}
```

