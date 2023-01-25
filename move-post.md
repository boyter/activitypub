# Move -> Post

Specific to Mastodon https://docs.joinmastodon.org/spec/activitypub/#supported-activities-for-profiles as it is not included in the main w3 spec https://www.w3.org/TR/activitypub/

```json
{
    "@context": "https://www.w3.org/ns/activitystreams",
    "id": "https://first.instance/users/username#moves/1",
    "type": "Move",
    "target": "https://other.instance/users/username",
    "actor": "https://first.instance/users/username",
    "object": "https://first.instance/users/username"
}
```