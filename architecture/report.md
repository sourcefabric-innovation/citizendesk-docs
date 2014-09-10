
Structure of `report` entities is defined at
[holder.py](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/common/holder.py).

The main fields of a `report` are:

+ identifiers (_mandatory_)
..+ `_id` for internal report identification
..+ `report_id` for linking among (remote) reports, i.e. even when they are not stored in local database
..+ `parent_id`, it is `report_id` of a report that the (current) report is followup to, if the current report follows to another report
..+ `session` for grouping reports into sessions; it is (commonly) `report_id` of report that starts the session
..+ `uuid` for identification of reports when used in outgest processes

+ other basic info
..+ `client_ip` from where/what ip-address the report came
..+ `user_id` set when a local user is a creator of the report
..+ `pinned_id` id of endpoint for the report; though not used by now, as channels are used for taking the reports
..+ `language` language of the report

+ publishing
..+ `coverages` a dictionary with lists of `outgested`, `published`, and `targeting` coverages of report
..+ `on_behalf_id` user that is taken as the one who (reports and) publishes the report, generally not the original author of the report

+ logs (_mandatory_)
..+ `produced` when the report was originally produced (e.g. a tweet-based reported can be received recently, even though being old)
..+ `_created` when the report document is created in database
..+ `_updated` when the report document is updated in database
..+ `status_updated` when the verification status of the report document is updated (in database)
..+ `_etag` for synchronizing between Eve requests

+ flags
..+ `proto` is it a proto-report, i.e. not a really considered report (got e.g. by a random search)
..+ `local` is the report produced inside the Citizen Desk system
..+ `summary` is the report a session summary
..+ `sensitive` is this report sensitive
..+ `automatic` was this report created automatically by the core system
..+ `editable` is the report editable (e.g. tweet-based reports should not be edited)
..+ `decayed` wheter the report underwent a decay process; not used yet

+ status
..+ `assignments` list of users that are assigned to the report; by now used as a 0-1 property
..+ `steps` list of verification steps that should be done on a report
..+ `verified` (an old version of) stating whether the report is found to be true
..+ `status` (a new version of) stating whether the report is found to be true, false, irrelevant
..+ `importance` level of importance of report; not used by now
..+ `relevance` level of relevance of report; not used by now

+ producers (_mandatory_)
..+ `feed_type` specifying type of report (_sms_, _tweet_, _plain_)
..+ `publisher` where the report was published
..+ `channels` how and why the report was put or injested into the Citizen Desk system

+ citizens (_mandatory_)
..+ `authors` list of authors of the report, each citizen given as authority and citizen identifiers
..+ `recipients` list of recipients of the report, each citizen given as authority and citizen identifiers
..+ `endorsers` list of endorsers of the report, each citizen given as authority and citizen identifiers
..+ `targets` list of targets, given by internal IDs (it can be e.g. groups of users)

+ content
..+ `original_id` ID of the report source at the original report publisher (e.g. tweet ID)
..+ `original` (_mandatory_) original source of report as it was put or injested into the Citizen Desk system
..+ `geolocations` list of geographical coordinates
..+ `place_names` list of place names, or of geo-tags
..+ `timeline` list of date-times of the reported event
..+ `time_names` list of time-tags
..+ `citizens_mentioned` list of citizens mentioned in report, each given as authority and citizen identifiers
..+ `subjects` list of tags on who/what-entities
..+ `media` list of links to media
..+ `texts` (_mandatory_) list of original and translated texts
..+ `sources` list of links to the original report source itself
..+ `links` list of links from the report
..+ `notices_inner` list of editorial comments for internal use
..+ `notices_outer` list of editorial comments for external use
..+ `comments` list of comments by citizens
..+ `tags` list of general tags, hashtags, keywords



