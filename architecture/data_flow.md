
The Citizen Desk core part is built over a common database structure (set over MongoDB).
Several parts access the database, they are namely:

+ ingest, for taking data from (remote) upstream sources
+ streams, for providing data to publishing services
+ feeds, for common methods, incl. sending data to citizens
+ interface, access to UI (outside the core part)

Each digest part has an outer and an inner part.
First, the outer part communicates with the very source of data, and puts the (preprocessed) data to the inner part.
Second, the inner part puts the data into database, with appropriate handling (incl. possible creation of) the sessions.

Streams (aka outgest) provide the data into downstream services, e.g. to Liveblog.

Regarding Liveblog, the connection between Citizen Desk and Liveblog has two parts:
+ having (active) coverages in Citizen Desk itself that correspond to particular Liveblog blogs
+ setting the Citizen Desk (Liveblog-oriented) stream at Liveblog as a chaining blog provider

When a coverage (from the upstream Citizn Desk) is selected for a Liveblog blog with auto-publish setting on,
any report in Citizen Desk that is published into the selected coverage is automatically received and displayed at the respective Liveblog blog.

