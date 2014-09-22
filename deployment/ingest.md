
Ingest components require additional outer processes outside the main _citizendesc-core_ system.

+ Twitter ingest uses _Newstwister_ system as the outer part for direct dealing with Twitter.

+ SMS ingest require a _FrontlineSMS-like_ system to be available. It can be an instance at _FrontlineSMS_ cloud,
or e.g. the _smsd-relay_ that communicates via the _FrontlineSMS-like_ interface.
For now, regular testing has been only done with _FrontlineSMS_ cloud.

+ URL-links ingest is a special type of ingest that (by now) only have the inner part, while the outer part is played by UI.

**Newstwister**

By default, _Newstwister_ expects to be installed at `/opt/newstwister` though it can be put into any other directory (then the startup scripts have to be adjusted). If it is at this `/opt/newstwister` directory, the startup script is the `/opt/newstwister/etc/init.d/newstwister` shell file.

Regarding sources at GitHub, the `/opt/newstwister` directory is the one that shall be copied into the actual deployment directory.

For running the _Newstwister_ system, default Twitter API keys have to be prepared, so that _Newstiwister_ can execute REST-based queries to Twitter. They are expected to be at `/opt/newstwister/etc/newstwister/oauth/search_auth.py` or at any other directory set in the _Newstwister_ startup script.

Notice that the default deployment type expects that _Newstwister_ should run at the same server as the main citizendesk-core system. The `/opt/newstwister/etc/newstwister/allowed.conf` file is for setting the allowed ip-addresses of clients that make (direct) requests to _Newstwister_, i.e. here it should be the ip-address of system where the main _citizendesk-core_ system runs (if it is not at localhost).

Log-rotating is covered by config at the `/opt/newstwister/etc/logrotate.d/newstwister` file.

Communication with Twitter requires API keys. For common (read-only) REST-based actions, _Newstwister_ uses a set of the keys stored at the `/opt/newstwister/etc/newstwister/oauth/search_auth.py` file.
Monitors and tweet-sending actions (that need multiple key sets) use API keys stored in database, at `twt_oauths`, `twt_authorized` collections for monitors, tweet-sending, respectively.


**FrontlineSMS**

When using _FrontlineSMS_, it is necessary to configure `HTTP Web Connection` that uploads incoming SMS into _Citizen Desk_. The web-connection should lead to `http://citizendesk.deployment/ingest/sms/feed/` with (preferably) POST requests. It should contain `pass` field with a chosen password, `phone` message-src-number, `text` for message-body, and `time` for message-timestamp. (The field names can be different if set accordinly in the main part of citizendesk-core too.)

It should have API enabled, the API secret key should be set for SMS sending at _citizendesk-core_ too, it should be set with `do not use a keyword`, and it can get any name.

For actual sending and receiving SMS via _FrontlineSMS_, the _FrontlineSMS_ account should have set a connection to outer SMS provider.

**URL-links**

Ingest based on general URL links require to have a file with stated effective top level domains, so that the _citizendesk-core_ can find the actual specific domain.
The current set of definitions is taken from `https://publicsuffix.org/list/effective_tld_names.dat` that is stored in `opt/citizendesk/etc/citizendesk/effective_tld_names.dat` file.

