
### sending an SMS to a phone number of a citizen alias in a new session
```
curl -X POST http://localhost:9060/feeds/sms/send -H "Content-Type: application/json" -d '{"message":"_message_to_be_sent_", "targets":[{"type":"citizen_alias","value":"_object_id_of_citizen_alias_whose_phone_number_should_be_used_"}], "user_id":"_id_of_system_user_that_asks_for_the_sms_sending_"}'
```

### replying to a SMS-based report, continuing a session
```
curl -X POST http://localhost:9060/feeds/sms/reply -H "Content-Type: application/json" -d '{"message":"_reply_message_to_be_sent_", "report_id":"_object_id_of_message_to_which_this_replies_", "language":"en", "sensitive":false, "user_id":"_id_of_system_user_that_asks_for_the_replying_"}
```

### creating a citizen alias based on a phone number
```
curl -X POST http://localhost:9060/feeds/sms/citizen/alias -H "Content-Type: application/json" -d '{"spec": {"phone_number":"_phone_number_to_be_used_as_an_identifier_", "description": "_purpose_of_this_citizen_alias_"}, "user_id":"_id_of_system_user_that_asks_for_the_action_"}'
```

