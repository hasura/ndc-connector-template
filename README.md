_Hiya, Connector Author 👋_

_Use these handy markdown template pages to generate documentation for your open source Hasura Data Connector._

_It's designed to help your users get going as quickly as possible with your connector and is comprised of this 
README.md and a number of sub-documents in the `docs` directory. You should edit them as you see fit._ 

_Look out for the inline comments, which aren't rendered, to help you fill in the blanks._

_To list your connector on the Hasura Connector Hub, you should make a PR to the 
[Hasura NDC Hub](https://github.com/hasura/ndc-hub) repo._

_Happy documenting! 🚀_
`#deleteme!!!`

# [ConnectorName] Data Connector

`![Optional Logo Image](path-to-image)`

[![Docs](https://img.shields.io/badge/docs-v3.x-brightgreen.svg?style=flat)](https://hasura.io/docs/3.0/latest/connectors/postgresql/)
[![ndc-hub](https://img.shields.io/badge/ndc--hub-postgres-blue.svg?style=flat)](https://hasura.io/connectors/ndc-postgres)
[![License](https://img.shields.io/badge/license-Apache--2.0-purple.svg?style=flat)](LICENSE.txt)
[![Status](https://img.shields.io/badge/status-alpha-yellow.svg?style=flat)](./readme.md)

[Short description of the connector and its primary purpose.]
This Hasura Data Connector connects you to your SuperBlazingFastDB™ database. 

This connector is built using the [Rust Data Connector SDK](https://github.com/hasura/ndc-hub#rusk-sdk) and implements the [Data Connector Spec](https://github.com/hasura/ndc-spec).

- [See the listing in the Hasura Hub](https://hasura.io/connectors/[connector-name])
- [Hasura V3 Documentation](https://hasura.io/docs/3.0/)

Docs for the [connectorName] data connector:
<!-- TODO: Edit, change, delete as your wish. 
You must have Code of Conduct, Contributing, Support and Security though -->
- [Usage](./docs/usage/index.md)
  - [Querying (for example)](./docs/usage/querying.md)
- [Architecture](./docs/architecture.md)
- [Development](./docs/development.md)
- [Code of Conduct](./docs/code-of-conduct.md)
- [Contributing](./docs/contributing.md)
- [Authentication](./docs/authentication.md)
- [Debugging](./docs/debugging.md)
- [Limitations](./docs/limitations.md)
- [Production](./docs/production.md)
- [Support](./docs/support.md)
- [Security](./docs/security.md)
- [Edit and/or add additional relevant links]

## Features

Below, you'll find a matrix of all supported features for the [NAME] data connector:

<!-- TODO: Your README should contain only a single matrix; choose one below and remove either the ✅ or ❌ from each
row -->

<!-- OLTP matrix -->

| Feature                         | Supported | Notes |
| ------------------------------- | --------- | ----- |
| Native Queries + Logical Models | ✅ ❌     |       |
| Simple Object Query             | ✅ ❌     |       |
| Filter / Search                 | ✅ ❌     |       |
| Simple Aggregation              | ✅ ❌     |       |
| Sort                            | ✅ ❌     |       |
| Paginate                        | ✅ ❌     |       |
| Table Relationships             | ✅ ❌     |       |
| Views                           | ✅ ❌     |       |
| Remote Relationships            | ✅ ❌     |       |
| Mutations                       | ✅ ❌     |       |
| Distinct                        | ✅ ❌     |       |
| Enums                           | ✅ ❌     |       |
| Default Values                  | ✅ ❌     |       |
| User-defined Functions          | ✅ ❌     |       |

<!-- OLAP matrix -->
<!--
| Feature                         | Supported | Notes |
| ------------------------------- | --------- | ----- |
| Native Queries + Logical Models | ✅ ❌     |       |
| Simple Object Query             | ✅ ❌     |       |
| Filter / Search                 | ✅ ❌     |       |
| Simple Aggregation              | ✅ ❌     |       |
| Sort                            | ✅ ❌     |       |
| Paginate                        | ✅ ❌     |       |
| Table Relationships             | ✅ ❌     |       |
| Views                           | ✅ ❌     |       |
| Distinct                        | ✅ ❌     |       |
| Remote Relationships            | ✅ ❌     |       |
| Mutations                       | ✅ ❌     |       |
-->

<!-- DocDB matrix -->
<!--
| Feature                         | Supported | Notes |
| ------------------------------- | --------- | ----- |
| Native Queries + Logical Models | ✅ ❌     |       |
| Simple Object Query             | ✅ ❌     |       |
| Filter / Search                 | ✅ ❌     |       |
| Simple Aggregation              | ✅ ❌     |       |
| Sort                            | ✅ ❌     |       |
| Paginate                        | ✅ ❌     |       |
| Nested Objects                  | ✅ ❌     |       |
| Nested Arrays                   | ✅ ❌     |       |
| Nested Filtering                | ✅ ❌     |       |
| Nested Sorting                  | ✅ ❌     |       |
| Nested Relationships            | ✅ ❌     |       |
-->

## Before you get Started

[Prerequisites or recommended steps before using the connector.]

1. The [DDN CLI](https://hasura.io/docs/3.0/cli/installation) and [Docker](https://docs.docker.com/engine/install/) installed
2. A [supergraph](https://hasura.io/docs/3.0/getting-started/init-supergraph)
3. A [subgraph](https://hasura.io/docs/3.0/getting-started/init-subgraph)
<!-- TODO: add anything connector-specific here -->

The steps below explain how to Initialize and configure a connector for local development. You can learn how to deploy a
connector — after it's been configured — [here](https://hasura.io/docs/3.0/getting-started/deployment/deploy-a-connector).

## Using the [NAME] connector

### Step 1: Authenticate your CLI session

```bash
ddn auth login
```

### Step 2: Initialize the connector

```bash
ddn connector init <connector-name> -i
```

### Step 3: Choose the [connectorName] from the list

### Step 4 Choose a name for the connector

### Step 5: Choose a port for the connector

### Step 6: Provide the [name] env var(s) for the connector


## Documentation
<!-- TODO: Either on GitHub in this repo or on your own site -->
View the full documentation for the [connectorName] connector [here](./docs/index.md).

## Contributing

Check out our [contributing guide](./docs/contributing.md) for more details.

## License

The [connectorName] connector is available under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

## Additional Sections

[Any other relevant sections or details specific to the connector.]
