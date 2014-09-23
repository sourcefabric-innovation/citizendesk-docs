
**Parts to adjust for having multiple SMS feeds**

+ `ingest`: with feed names; auto-reply with the same feed name
+ `feeds`: requests to send/reply-to SMS with feed name
+ `session`: detecting whether in a session should probably be *feed_name*-specific

What about citizen aliases, should they be somehow set for particular feeds?
May be it is enough to have groups of citizens according to the feeds.

