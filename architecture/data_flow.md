
The _Citizen Desk_ core part is built over a common database structure (set over MongoDB).
Several parts access the database, they are namely:

+ _ingest_, for taking data from (remote) upstream sources
+ _streams_, for providing data to publishing services
+ _feeds_, for common methods, incl. sending data to citizens
+ _interface_, access to UI (outside the core part)

Each digest part has an outer and an inner part.
First, the outer part communicates with the very source of data, and puts the (preprocessed) data to the inner part.
Second, the inner part puts the data into database, with appropriate handling (incl. possible creation of) the sessions.

Streams (aka outgest) provide the data into downstream services, e.g. to Liveblog.

Regarding _Liveblog_, the connection between _Citizen Desk_ and _Liveblog_ has two parts:
+ having (active) coverages in _Citizen Desk_ itself that correspond to particular _Liveblog_ blogs
+ setting the _Citizen Desk_ (Liveblog-oriented) stream at _Liveblog_ as a chaining blog provider

When a coverage (from the upstream _Citizn Desk_) is selected for a _Liveblog_ blog with auto-publish setting on,
any report in _Citizen Desk_ that is published into the selected coverage is automatically received and displayed at the respective _Liveblog_ blog.
The link for the main Liveblog-oriened output from _Citizen Desk_ that shall be used in _Liveblog_ chaining configuration:
+ `http://_citizendesk_deployment_/streams/liveblog/coverage/`

Notice that there are two important distinction notions related to reports:
+ when a report is `proto`, it is meant that the report is a part of random noise, i.e. not (yet) considered to be a real report
+ when a report is `decayed`, it is meant that the content of the report is removed, wiht only keeping `metadata` of that report

