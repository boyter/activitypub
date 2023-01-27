# User

Fetching a users details usually follows a webfinger against the user to validate they exist.

Given a valid webfinger such as the following

https://mastinator.com/.well-known/webfinger?resource=acct:someaccount@mastinator.com

We can then query their self location to determine their inbox,

```json
{
    "subject": "acct:someaccount@mastinator.com",
    "links": [
        {
            "rel": "self",
            "type": "application/activity+json",
            "href": "https://mastinator.com/u/someaccount"
        }
    ]
}
```

The important part in the above is the `links.rel` where `self` indicates that the `href` for this object contains the location of this users details.

We can then issue a get request to this endpoint to get the details for the user.

```json
curl --location --request GET 'https://mastinator.com/u/someaccount' \
--header 'Accept: application/ld+json; profile="https://www.w3.org/ns/activitystreams"
```

For mastodon the accept headers of `application/activity+json`, `application/ld+json; profile="https://www.w3.org/ns/activitystreams` or `application/json` will work for the above call, but many instance types will reject the first two. It is safer to use one of the first two which are strictly speaking more correct anyway.

Note that fetching the url without this header will usually result in a redirect to the HTML version of the users inbox, or return HTML directly.