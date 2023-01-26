# ActivityPub Explained

```
     /\       | | (_)     (_) |        
    /  \   ___| |_ ___   ___| |_ _   _ 
   / /\ \ / __| __| \ \ / / | __| | | |
  / ____ \ (__| |_| |\ V /| | |_| |_| |
 /_/    \_\___|\__|_| \_/ |_|\__|\__, |
           |  __ \     | |        __/ |
           | |__) |   _| |__     |___/ 
           |  ___/ | | | '_ \          
           | |   | |_| | |_) |         
           |_|    \__,_|_.__/          
```

Sequence diagrams of how ActivityPub/Webfinger works and how to implement against it will be stored here. This is needed because the spec is vague and different instances implement things in different ways.

The goal is to create a collction that can be used by someone in a clean room environment to implement an instance that could work against the fediverse.

 - [Announce Post](announce-post.md) - Boost/Retweet/Share
 - [Create Post](create-post.md) - Toot/Tweet/Post
 - [Move Post](move-post.md) - User Migration
 - [Delete Post](delete-post.md) - Toot/Tweet/Post Deletion


Webfinger is described quite well at the following https://webfinger.net/ and should be considered essential reading as it is used across the fediverse.


PR's are encouraged!


The following are good to look through,

 - https://www.w3.org/TR/activitypub/
 - https://docs.joinmastodon.org/spec/activitypub/
 - https://activitypub.rocks/

The following are implementations in a few different languages,

 - https://github.com/jointakahe/takahe Python
 - https://humungus.tedunangst.com/r/honk Go
 - https://blog.joinmastodon.org/2018/06/how-to-implement-a-basic-activitypub-server/ JavaScript
 - https://github.com/benbrown/shuttlecraft JavaScript

Some specific behaviors are covered well here.

 - https://docs.gotosocial.org/en/latest/federation/behaviors/outbox/
