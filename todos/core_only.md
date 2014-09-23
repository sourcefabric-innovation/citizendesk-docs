
**Stuff only in cd-core:**

+ tweet related
  + *pick tweet* by id/url (different than general url-based *web_links*)
  + *authorize keys* for tweet sending (do not use currently used keys)
  + *tweet* sending/replying

+ media related
  + links to *image-loaded services*

Below we describe the cases in more detail.


+ **Pick tweet by id/url (different than general url-based *web_links*)**

[POST to /feeds/twt/pick/](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/twt/pick/connect.py#L9)
with [data](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/twt/pick/storage.py#L20):
`{"endpoint_id":<endpoint_id>,"tweet_spec":{"tweet_id":<tweet_id>}}`
or
`{"endpoint_id":<endpoint_id>,"tweet_spec":{"tweet_url":<tweet_url>}}`


+ **Authorize keys for tweet sending (do not use currently used keys for that)**

Done in two phases, all the data stored together at structure [described at core](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/twt/authorized/storage.py#L20).

1. sets the initial app keys (without tokens), creates temporary tokens, and asks for verification code (to be get from *verifier_url*)
[POST to /feeds/twt/authorized/](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/twt/authorized/connect.py#L15)
with data:
`{"spec":{"app_consumer_key":<app_consumer_key>,"app_consumer_secret":<app_consumer_secret>}}`
2. authorizes the keys with the help of the verifier pin (that was taken by an editor through the *verifier_url*, that was itself set at the first step)
[POST to /feeds/twt/authorized/<doc_id>/finalize/](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/twt/authorized/connect.py#L16)
with data:
`{"spec":{"verifier_pin":<verifier_pin>}}`


+ **Tweet sending/replying**

Can be done as a tweet in a new session, or a reply to a tweet (thus part of the session of that reply-to tweet).
If a reply, tweet has to start with *@user_name*.

[POST to /feeds/twt/send/](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/twt/send/connect.py#L9) for a new session
[POST to /feeds/twt/send/<report_id>/reply/](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/twt/send/connect.py#L10) for a reply
both with data:
`{"authorized_id":<authorized_id>,"user_id":<user_id>,"endpoint_id":<endpoint_id>,"tweet_spec":<tweet_spec>}`
*authorized_id* is *_id* of an authorized app key (set at the authorize-keys process),
and the rest is [according to core](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/twt/send/storage.py#L20).

Notice that *endpoint_id* is used as *channel.value* (alike in the picking case) at the stored report data.


+ **Links to image-loaded services**

When a report contains links to images (it is e.g. for some tweet-based and url-based reports),
verifiers can try to use online services for making investigations based on those linked images.

Overall setup is descibed at [image feeds docs](https://github.com/msat-cont/citizendesk-docs/blob/master/core_feeds/image_feeds.md).
with data structure of the image services stored
[at *media_services* collection](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/img/service/storage.py#L22).

The URLs of the cd-core actions are set at
[core part](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/feeds/img/service/connect.py#L6)
and since we have a basic set of remote services loaded into database
(via script at the file `/opt/citizendesk/etc/utils/srvcs_spec.py`) it can be used just with GET requests to
`/feeds/img/service/resolved/report/<report_id>/`

It returns list (according to the list of linked images) of structures (according to the set of the services).

