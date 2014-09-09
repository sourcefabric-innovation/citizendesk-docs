
Structure of _reports_ is defined at
`https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/common/holder.py`.

The main fields of a _report_ are:

+ `_id` for internal report identification
+ `report_id` for linking among (remote) reports, i.e. even when they are not stored in local database
+ `parent_id`, it is `report_id` of a report that the (current) report is followup to
+ `session` for grouping reports into sessions; it is (commonly) `report_id` of report that starts the session
+ `uuid` for identification of reports when used in outgest processes
+ `...`



