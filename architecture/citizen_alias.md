
Structure of `citizen_alias` entities is defined at
[citizen_holder.py](https://github.com/sourcefabric-innovation/citizendesk-core/blob/master/src/citizendesk/common/citizen_holder.py).

The main fields of a `citizen_alias` are:

+ identifiers (_mandatory_)
..+ `_id` for internal citizen alias identification
..+ `uuid` for identification of citizen aliases when used in outgest processes

+ other basic info
..+ `active` whether the citizen alias is (currently) used

+ provider-based identification (_mandatory_)
..+ `authority` name of the authority that provides citizen identifiers
..+ `identifiers` dictionary of `user_id`, `user_id_search`, `user_name`, `user_name_search` citizen identifiers at the authority

+ provider-based names
..+ `name_first` citizen first name
..+ `name_last` citizen last name
..+ `name_full` citizen full name

+ provider-based other properties
..+ `avatars` list of links to avatar images
..+ `locations` list of geographical locations
..+ `time_zone` time zone where the citizens is located
..+ `languages` list of languages used by the citizen
..+ `description` textual info on citizen
..+ `sources` list of links to the original citizen info
..+ `home_pages` list of links to homepages of the citizen

+ local-edited
..+ `notable` flag
..+ `reliable` flag
..+ `verified` flag
..+ `places` list of geo-tags
..+ `comments` list of internal comments
..+ `links` list of links related to the citizen
..+ `tags` general tags related to the citizen

+ auto-generated on reports
..+ `tags_auto` tags automatically created from reports of the citizen; not used yet

+ logs (_mandatory_)
..+ `produced` when the report was originally produced (e.g. a tweet-based reported can be received recently, even though being old)
..+ `_created` when the report document is created in database
..+ `_updated` when the report document is updated in database
..+ `created_by` used when creation of the citizen alias requested by a user
..+ `updated_by` used when update of the citizen alias requested by a user

+ flags
..+ `local` is the citizen alias has been created by a local user
..+ `sensitive` is this citizen alias sensitive

+ configuration
..+ `config` dictionary of _type_:_value_ configuration properties



