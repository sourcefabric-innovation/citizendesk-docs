
The main citizendesc-core components are split into several processes, according to their functions. We have ingest processes (one per ingest type), a feed process, and an outgest process. Notice that each ingest type has two parts: one separate (with its own processes), and one inside the main core.

By default the citizendesc-core system expects to be installed at `/opt/citizendesk` directory. If it is put into different directory, the startup scripts (that are by default at the `/opt/citizendesk/etc/init.d` directory) have to be adjusted accordingly.

Regarding sources at GitHub, the `/opt/citizendesk` directory is the one that shall be copied into the actual deployment directory. Then content of the `/src/citizendesk` directory should be put into the `/opt/citizendesk/lib/citizendesk` directory at the deployment (the `citizendesk` parts of the directory structures should be the same ones).

The startup scripts (that are at the `/opt/citizendesk/etc/init.d` directory) are:
+ `sms_ingest` for SMS ingest part of the main core
+ `twt_ingest` for Twitter ingest part of the main core
+ `feeds_ifce` for the common interface toward users
+ `outer_ifce` for the outgest into other systems

Log-rotating is covered by config files at the `/opt/citizendesk/etc/logrotate.d` directory.

The `/opt/citizendesk/etc/utils` directory contains auxiliary scripts, e.g. the `srvcs_*.py` ones for defining remote services that help with image verification.

Indexes in database are set by the `db_indexes.js` file. It expects that the name of the used database is _citizendesk_. Notice that this file has to be executed (by mongo client) to provide reasonable database access.

The `/opt/citizendesk/etc/citizendesk` directory contains the main configuration files. They are:
+ `sms_allowed.conf` for ip addresses from which SMS (by _FrontlineSMS_) are sent to the SMS ingest part of the main core.
+ `twt_allowed.conf` for ip addresses from which tweets (by _Newstwister_) are sent to the Twitter ingest part of the main core.
+ `feed_allowed.conf` for ip addresses from which the common interface is available
+ `sms_ifce_fill.yaml` for setting parameters on both ingest-based and feeds-based SMS communication
+ `outer_ifce_fill.yaml` for setting default parameters on the outgest processes

