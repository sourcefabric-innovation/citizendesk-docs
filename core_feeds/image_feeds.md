
**Actions for dealing with images linked from reports**

Blueprints for dealing with images are set at the `src/citizendesk/feeds/img/dispatch.py` file.
Then each used `connect.py` file provide actual setup for particular methods.
The `storage.py` files usually contain schema of expected data structures in the requests.

The requests have a common structure, for the curl comman-line util, it is like:
```
curl -X __method__ http://localhost/feeds/__connector__ -H "Content-Type: application/json" -d '__json-formatted data__'
```
where the _connector_ (in the action URL), _method_, and data (for _POST_ methods) can be the next ones:

**Remote services that analyse images are set using _POST_ method**
+ `img/service` connector for inserting info on a remote image-oriented service
+ `img/service/id/<service_id>/activate` connector for enabling a remote image-oriented service
+ `img/service/id/<service_id>/deactivate` connector for disabling a remote image-oriented service

**Remote image-oriented services are listed using _GET_ method**
+ `img/service` connector for listing the services
+ `img/service/id/<service_id>` connector for getting info on the specified service

**Getting links to remote services setup to analyse images of a given report, using _GET_ method**
+ `img/service/resolved/report/<report_id>/` connector for getting links where the report images are already preset

