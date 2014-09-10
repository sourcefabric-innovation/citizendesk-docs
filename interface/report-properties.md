A report can have several orthogonal properties, one of them is the
status. The status determines the current position of the report in
the verification workflow, and it is encoded as an integer with the
following meaning:

 1. New
 2. Assigned
 3. Dismissed
 4. Falsified
 5. Verified

*Note*: avoid using `0` as a status code, it would make harder to spot
errors in languages like Javascript.

[This is a schema of the verification workflow](https://docs.google.com/drawings/d/1iNlUw-WH6aWL53blvbcVFBv2Ob-nO0GalqoYXFurK5I/edit?usp=sharing)
