### Core write only properties

Some status of the system is maintained by the [core][cor], so the [interface][int] and [front end][fro] should not modify such status.

The core may change the properties of several documents in several collections, so there is no way to limit the writing rights of the [interface][int] component.

Here we collect a list of the properties which should be modified just by the core:

#### `reports` collection

- `coverages.published`
- `coverages.outgested`

[cor]: https://github.com/sourcefabric-innovation/citizendesk-core
[int]: https://github.com/sourcefabric-innovation/citizendesk-interface
[fro]: https://github.com/sourcefabric-innovation/citizendesk-frontend
