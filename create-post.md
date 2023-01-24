# Create -> Post

Posts tend to be created with a few possible states before being distributed, in Mastodon and other systems.

 - Public. This will appear on the local timeline, and go to all followers of the user, and any @ mentions. Anyone can access this post via API.
 - Mentioned. This will only go to a direct @ mentions in the message itself, and not followers.
 - Followers. This will only go to followers, and not appear on the local timeline.
 - Unlisted this goes into everything, but should now allow boosts or other such actions.

takahe also has the following

 - Local Only. This will appear on the local timeline, and go to any local followers.

Rules tend to roll up, so an @ will work in any public, any mentioned or followers for example.

When a post is created by a user the instance performs the following actions.

 - Webfinger any remote instance to get the users address
 - Get the users details in order to know the inbox
 - Message the inbox

For local instances the decision is up to the instance.

```
┌────────────┐ ┌────────────┐ ┌───────────────┐
│    User    │ │  Instance  │ │Remote Instance│
└────────────┘ └────────────┘ └───────────────┘
      │              │               │         
      │              │               │         
      │              │               │         
      │────Create───▶│───Webfinger──▶│         
      │              │               │         
      │              │               │         
      │              │─────User─────▶│         
      │              │               │         
      │              │               │         
      │              │───Create to ─▶│         
      │              │     Inbox     │         
      │              │               │         
      │              │               │         
```

Generally the results from webfinger and the user probes are cached to avoid hitting the remote instance again. This information should be possible to cache forever.

Webfinger can be done with a simple get request

`https://some.instance/.well-known/webfinger?resource=acct:someone@some.instance`

User can be fetched by finding the `rel` identified as `self` inside the `links` array. This can then be fetched using the usual headers, `application/activity+json` or `application/ld+json; profile="https://www.w3.org/ns/activitystreams`. However note that some instance types will work with `application/json` although this is not strictly correct.

```
curl --location --request GET 'https://some.instance/users/someone' \
--header 'Accept: application/ld+json; profile="https://www.w3.org/ns/activitystreams'
```

The return from the above will contain a field inbox, which in the case of a mastodon system looks like the following `"inbox": "https://some.instance/users/someone/inbox"`. It is this URL that the create must be sent to as a POST.
