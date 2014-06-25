
### setting a stream filter
```
curl -X POST -d '{"spec": {"track":["citizen desk", "citizendesk", "superdesk", "liveblog", "airtime", "booktype"],"follow":[],"locations":[],"language":null}}' -H 'Content-Type: application/json' http://localhost:9060/feeds/twt/filter/
```

### setting a stream info (without actual starting the stream)
```
curl -X POST -d '{"spec": {"filter_id": 2, "oauth_id": 1}}' -H 'Content-Type: application/json' http://localhost:9060/feeds/twt/stream/
```

### updating the stream info (without actual starting the stream)
```
curl -X PUT -d '{"spec": {"filter_id": 1, "oauth_id": 1}}' -H 'Content-Type: application/json' http://localhost:9060/feeds/twt/stream/1
```

### starting the set-up stream
```
curl -X PATCH -d '{"control": {"streamer_url": "http://localhost:9054/", "switch_on": true}}' -H 'Content-Type: application/json' http://localhost:9060/feeds/twt/stream/1
```

### starting a stream in another way
```
curl -X POST http://localhost:9060/feeds/twt/stream/1/start
```

### stopping a running stream
```
curl -X PATCH -d '{"control": {"switch_on": false}}' -H 'Content-Type: application/json' http://localhost:9060/feeds/twt/stream/1
```

### stopping a running stream in another way
```
curl -X POST http://localhost:9060/feeds/twt/stream/1/stop
```

### making a rest-search
```
curl -X SEARCH -d '{"query":{"contains":["liveblog"]}}' -H 'Content-Type: application/json' http://localhost:9060/feeds/twt/search/101/request/102/
```

### another form of rest-search
```
curl -X POST -d '{"user_id":"103", "request_id":"104", "search_spec":{"query":{"contains":["liveblog"]}}}' -H 'Content-Type: application/json' http://localhost:9060/feeds/twt/search/
```

### getting citizen alias based on a twitter user, with asking Twitter for that info if such citizen alias not stored yet
```
curl -X GET http://localhost:9060/feeds/twt/citizen/alias/name/_twitter_screen_name_of_a_twitter_user_?force=1
curl -X GET http://localhost:9060/feeds/twt/citizen/alias/id/_twitter_user_id_of_a_twitter_user_?force=1
```

