# Delete -> Post

https://www.w3.org/TR/activitypub/#delete-activity-outbox

Note that deletes should only apply to [create](create-post.md) where-as undo should be used on like/follow/block and remove on add.

For delete, when sent the instance should find the appropiate posts via the supplied id and either delete it or tombstone it. The activitypub spec does not define what it means by tombstone, but in the context of active directory it means to mark it for deletion, not display it anymore and remove it at a later date.

In the case of mastodon the object contains a dictionary where id `object.id` is the id that should be used to delete the object created. Other instances have set the `id` in the supplied JSON.

Examples below of deletes with the id `ShouldMatchTheIdOfObjectInCreate` being the one to delete in the system.

Mastodon delete example

```json
{
   "@context": "https://www.w3.org/ns/activitystreams",
   "actor": "https://some.instance/u/testinbox",
   "cc":
   [
       "https://some.instance/u/Etiolate"
   ],
   "id": "https://some.instance/u/testinbox/217h4NBLrMJzT3qz7B#delete",
   "object":
   {
       "atomUri": "https://some.instance/u/testinbox/217h4NBLrMJzT3qz7B",
       "id": "ShouldMatchTheIdOfObjectInCreate",
       "type": "Tombstone"
   },
   "published": "2023-01-05T09:26:18Z",
   "to": "https://www.w3.org/ns/activitystreams#Public",
   "type": "Delete"
}
```

Other instance delete example

```json
{
       "@context": "https://www.w3.org/ns/activitystreams",
       "actor": "https://some.instance/u/testinbox",
       "cc":
       [
           "https://some.instance/u/testinbox"
       ],
       "id": "ShouldMatchTheIdOfObjectInCreate",
       "object": "https://some.instance/u/testinbox/217h4NBLrMJzT3qz7B",
       "published": "2023-01-05T09:26:18Z",
       "to": "https://www.w3.org/ns/activitystreams#Public",
       "type": "Delete"
}
```