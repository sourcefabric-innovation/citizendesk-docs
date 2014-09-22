
**Common acctions on reports, mostly targetting the publishing process**

Blueprints for dealing with images are set at the `src/citizendesk/feeds/any/dispatch.py` file.
Then each used `connect.py` file provide actual setup for particular methods.
The `storage.py` files usually contain schema of expected data structures in the requests.

The requests have a common structure, for the curl comman-line util, it is like:
```
curl -X __method__ http://localhost/feeds/__connector__ -H "Content-Type: application/json" -d '__json-formatted data__'
```
where the _connector_ (in the action URL), _method_, and data (for _POST_ methods) can be the next ones:

**Preparing coverages, using _POST_ method**
+ `any/coverage` connector for inserting info on a coverage
+ `any/coverage/id/<coverage_id>/activate` connector for enabling a coverage for outputting
+ `any/coverage/id/<coverage_id>/deactivate` connector for disabling a coverage for outputting

**Unpublish all reports from given coverage, using _POST_ method**
+ `any/coverage/id/<coverage_id>/unpublish` connector for bulk unpublishing from the given coverage

**Getting info on current coverages, using _GET_ method**
+ `any/coverage` connector for getting list of coverages
+ `any/coverage/id/<coverage_id>` connector for getting info on a single coverage

**Publishing a report into a coverage, using _POST_ method**
+ `any/report/id/<doc_id>/publish` connector for publishing specified report into all its targetted coverages
+ `any/report/id/<doc_id>/publish/<coverage_id>` connector for publishing specified report into specified coverage
+ `any/report/id/<doc_id>/unpublish` connector for unpublishing specified report from all coverages
+ `any/report/id/<doc_id>/unpublish/<coverage_id>` connector for unpublishing specified report from specified coverage

**Setting a Citizen Desk user that is outputted as the report dealer, using _POST_ method**
+ `any/report/id/<doc_id>/on_behalf_of/<user_id>` connector for setting the `on_behalf_of` user
+ `any/report/id/<doc_id>/on_behalf_of` connector for removing the `on_behalf_of` user

