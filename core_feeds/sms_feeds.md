
**Communicating over SMS channels**

Blueprints for SMS-based communication are set at the `src/citizendesk/feeds/sms/dispatch.py` file.
Then each used `connect.py` file provide actual setup for particular methods.
The `storage.py` files usually contain schema of expected data structures in the requests.

The requests have a common structure, for the curl comman-line util, it is like:
```
curl -X __method__ http://localhost/feeds/__connector__ -H "Content-Type: application/json" -d '__json-formatted data__'
```
where the _connector_ (in the action URL), _method_, and data (for _POST_,_PUT_ methods) can be the next ones:

**for sending an SMS to a phone number of a citizen alias, using _POST_ method**
+ `sms/send` connector for sending SMS in a new session, with data:
  + `{"message":"_message_to_be_sent_", "targets":[{"type":"citizen_alias","value":"_object_id_of_citizen_alias_whose_phone_number_should_be_used_"}], "user_id":"_id_of_system_user_that_asks_for_the_sms_sending_"}`
+ `sms/reply` connector for replying to a SMS-based report, continuing a session, with data:
  + `{"message":"_reply_message_to_be_sent_", "report_id":"_object_id_of_message_to_which_this_replies_", "language":"en", "sensitive":false, "user_id":"_id_of_system_user_that_asks_for_the_replying_"}`

**for getting sms-based reports from database**
+ _connectors_ for _GET_ method
  + `sms/report`, list of sms-based reports
  + `sms/report/id/<doc_id>`, sms-based report of give _id_ or _report_id_
  + `sms/report/session/<session_id>`, list of sms-based reports of provided session
  + `sms/report/sent_to/<phone_number>`, list of sms-based reports sent to the phone number
  + `sms/report/received_from/<phone_number>`, list of sms-based reports received from the phone number

**for creating a citizen alias based on a phone number**
+ `sms/citizen/alias` (using _POST_ method) connector for creating a new citizen alias,
+ `sms/citizen/alias/id/<alias_id>` (using _PUT_ method) connector for rewriting a citizen alias, both connectors with data:
  + `{"spec": {"phone_number":"_phone_number_to_be_used_as_an_identifier_", "description": "_purpose_of_this_citizen_alias_"}, "user_id":"_id_of_system_user_that_asks_for_the_action_"}`

**for getting sms-based citizen aliases from database**
+ _connectors_ for _GET_ method
  + `sms/citizen/alias/id/<alias_id>`, sms-based citizen alias of given id
  + `sms/citizen/alias/phone_number/<phone_number>`, sms-based citizen alias of given phone number
  + `sms/citizen/alias/`, list of sms-based citizen aliases

