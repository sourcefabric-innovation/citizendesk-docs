
**Communicating over Twitter channels**

Blueprints for Twitter-based communication are set at the `src/citizendesk/feeds/twt/dispatch.py` file.
Then each used `connect.py` file provide actual setup for particular methods.
The `storage.py` files usually contain schema of expected data structures in the requests.

The requests have a common structure, for the curl comman-line util, it is like:
```
curl -X __method__ http://localhost/feeds/__connector__ -H "Content-Type: application/json" -d '__json-formatted data__'
```
where the _connector_ (in the action URL), _method_, and data (for _POST_, _SEARCH_, _PUT_, _PATCH_ methods) can be the next ones:

The next parts are used:
+ `twt/filter` for setting filters of Twitter stream monitors
+ `twt/oauth` for setting Twitter keys used with monitors
+ `twt/stream` for setting Twitter streams, using data form the `filter` and `oauth` parts
+ `twt/search` for REST-base Twitter search of tweets
+ `twt/pick` for acquiring information on a single tweet
+ `twt/authorized` for setting Twitter keys for tweet sending
+ `twt/send` for tweet sending, using keys from the `authorized` part
+ `twt/citizen_alias` for acquiring info on a Twiiter user
+ `twt/report`, `twt/endpoint`, `twt/session` for database search on current data

Below we show some of the implemented methods; look please at the code of the particular feed parts (as listed above) for all the other actions.

+ `twt/filter` connector, setting a stream filter, _POST_ method, with data:
  + `{"spec": {"track":["citizen desk", "citizendesk", "superdesk", "liveblog", "airtime", "booktype"],"follow":[],"locations":[],"language":null}}`

+ `twt/stream` connector, setting a stream info (without actual starting the stream), _POST_ method, with data:
  + `{"spec": {"filter_id": <filter_id>, "oauth_id": <oauth_id>}}`

+ `twt/stream/<stream_id>` connector, updating the stream info (without actual starting the stream), _PUT_ method, with data:
  + `{"spec": {"filter_id": <filter_id>, "oauth_id": <oauth_id>}}`

+ `twt/stream/<stream_id>` connector, starting the set-up stream, _PATCH_ method, with data:
  + `{"control": {"streamer_url": "http://localhost:9054/", "switch_on": true}}`

+ `twt/stream/<stream_id>/start` connector, starting a stream in another way, _POST_ method, with no data;

+ `twt/stream/<stream_id>` connector, stopping a running stream, _PATCH_ method, with data:
  + `{"control": {"switch_on": false}}`

+ `twt/stream/<stream_id>/stop` connector, stopping a running stream in another way, _POST_ method, with no data;

+ `twt/search/<search_id>/request/<request_id>` making a REST-search, _POST_, _SEARCH_ methods, with data:
  + `{"query":{"contains":["liveblog"]}}`

+ `twt/search` connector, another form of rest-search, _POST_, _SEARCH_ methods, with data:
  + `{"user_id":<user_id>, "request_id":<request_id>, "search_spec":{"query":{"contains":["liveblog"]}}}`

+ getting citizen alias based on a Twitter user, with asking Twitter for that info if such citizen alias not stored yet, _GET_ method, connectors:
  + `twt/citizen/alias/name/_twitter_screen_name_of_a_twitter_user_?force=1`
  + `twt/citizen/alias/id/_twitter_user_id_of_a_twitter_user_?force=1`

