
**Ingest based on URL links**

Making the reports based on URL links is accessed directly at the ingest interface, i.e. not via feeds.
Blueprint for making reports based on URL links is set at the `src/citizendesk/ingest/url/connect.py` file.

The request for making the URL-based reports from UI uses _POST_ method, and it is like:
`curl -X POST -d '{"feed_name": "frontend", "url_link": <requested_link>, "request_id": <request_id>}' -H "Content-Type: application/json" "http://localhost/ingest/url/feed/"`

