
**Parts to adjust for having multiple SMS feeds**

+ `ingest`: with feed names; auto-reply with the same feed name
+ `feeds`: requests to send/reply-to SMS with feed name
+ `session`: detecting whether SMS is in a session should probably be *feed_name*-specific
+ `configs`: the URLs and keys should be provided as a struct, item per feed;

What about citizen aliases, should they be somehow set for particular feeds?
May be it is enough to have groups of citizens according to the feeds.

