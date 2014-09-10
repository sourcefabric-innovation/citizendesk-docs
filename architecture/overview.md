

**Citizen Desk** architecture is based on dealing with connections among citizens and reports.

Citizens are identified by (remote) authorities, and identifiers held by the (remote) authorities. It is e.g. Twitter as authority and Twitter user-id as the identifer, or telco companies as the authority and phone numbers as the identifiers.

Each such identifier (on a citizen at a network) is saved as a _citizen-alias_ structure. The overall information on a _citizen_ is a list of _citizen-alias_ structures then.

The central structure of the _Citizen Desk_ system is _report_. It contains info on its authors, recipients; textual and multimedia content, and its connections to other reports.

Notice that multimedia are only linked from particular reports, as the main purpose of the _Citizen Desk_ system is to provide **connections among citizens and reports**.

An important information on reports is whether the (received) reports are true or false, thus a verification helper is part of the _Citizen Desk_ system.

Another defining feature of _Citizen Desk_ is that it enables **two-way communication with citizens**, i.e. that it allows bidirectional exchange of information, both from and toward citizens.

