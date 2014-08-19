Citizen lists are implemented in a way that takes into considerations
the following:

 - while listing reports, we want to show the list that their author belongs to
 - citizen aliases are not identified by an id, but by the pair authority/id
 - the citizen aliases belonging to lists will probably be not too
   many, it will thus be possible to download the JSON containing all
   of them on the client sidewith a single request

Given this, Eve embed functionality cannot be used to associate lists
to reports when they are queried. The only way to get a set of reports
with associated lists, would be to add the logic in the server side
code, querying and joining directly with the database.

I (Francesco) find that a simpler solution is to have all the aliases
belonging to lists cached in a service on the client side, and join
them on the fly with the reports. In order to do this, i created two
collections in Citizendesk interface: `citizen_lists` and
`aliases_in_lists`.

`citizen_lists` is intended just to provide unique identifiers for the
lists, while `aliases_in_lists` should contain mappings from the pair
(authority, id) to a list. Having the latter in a dedicate collection
makes it easier to avoid duplicates.
