
The core part of Citien Desk requires some system and python packages to be installed.
When using Ubuntu, those packages are:

+ python-bson
+ python-pymongo
+ python-flask
+ python-yaml
+ python-beautifulsoup
+ python-chardet

+ mongodb-server
+ mongodb-clients
+ nginx-full

The Newstwister ingest part additionally requires:

+ python-twisted
+ python-oauth2
+ python-setproctitle

Reverse proxy by Nginx server can be configured e.g. next way, with setting the proper port numbers there:

```
        location /feeds/ {
                proxy_pass          http://localhost:9060/feeds/;
                proxy_set_header    Host             $host;
                proxy_set_header    X-Real-IP        $remote_addr;
                proxy_set_header    X-Forwarded-For  $proxy_add_x_forwarded_for;
        }

        location /ingest/sms/ {
                proxy_pass          http://localhost:9056/ingest/sms/;
                proxy_set_header    Host             $host;
                proxy_set_header    X-Real-IP        $remote_addr;
                proxy_set_header    X-Forwarded-For  $proxy_add_x_forwarded_for;
        }
                
        location /ingest/twt/ {
                proxy_pass          http://localhost:9055/ingest/twt/;
                proxy_set_header    Host             $host;
                proxy_set_header    X-Real-IP        $remote_addr;
                proxy_set_header    X-Forwarded-For  $proxy_add_x_forwarded_for;
        }

        location /ingest/url/ {
                proxy_pass          http://localhost:9071/ingest/url/;
                proxy_set_header    Host             $host;
                proxy_set_header    X-Real-IP        $remote_addr;
                proxy_set_header    X-Forwarded-For  $proxy_add_x_forwarded_for;
        }

        location /streams/ {
                proxy_pass          http://localhost:9061/streams/;
                proxy_set_header    Host             $host;
                proxy_set_header    X-Real-IP        $remote_addr;
                proxy_set_header    X-Forwarded-For  $proxy_add_x_forwarded_for;
        }

```
