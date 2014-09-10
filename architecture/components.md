
The server-bound core part of **Citizen Desk** has next components:

+ _citizendesk-core_ system with ingests, feeds, and outgests processing
+ _Newstwister_ that makes communication with Twitter
+ _smsd-relay_ can be used for SMS communication if _FrontlineSMS_ is not applicable

The server part of the whole system is based on Python scripts, uses MongoDB as database storage, and is commonly deployed with Nginx as a reverse proxy.

Notice that the ingest parts can be used for two-way communication, i.e. for both receiving information from citizens, and for asking the citzens.

To simplify dealing with ingest sources, scripts for each ingest type are split into two parts: one part is bound to the ingest source, and it talks the ingest-source language. Its coupled part is inside the core system, it takes json-structured data from the source-bound part, and it saves the data into database accordingly.
