
These commands are low-level ones. More high-level interface is available through Citizen Desk core.
Notice that REST-based actions (_search_, _user_, _pick_) use Twitter app keys set in configuration file.
Stream _start_ uses keys provided in requests. And _tweet_ sending needs authorized keys (via _authini_, _authfin_) that are then provided in the sending requests.
Requests on stream _status_ and to _stop_ a stream do not need any keys (as they do not do requests on Twitter).

GET requests
------------

asking whether a stream is running
```
/_status
```


POST requests
-------------

starting a stream
```
/_start
```

stopping a stream
```
/_stop
```

making a rest-search
```
/_search
```

taking info on a user
```
/_user
```

taking tweet by id
```
/_pick
```

authorizing keys for tweet sending
```
/_authini
/_authfin
```

sending a tweet
```
/_tweet
```

