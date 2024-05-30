<!-- TODO: Hiya, Connector Author! Throughout this template, you'll find TODO comments to help guide you and ensure
you've updated this README to be ready for users. If you have questions, shout at the docs team on #team-docs in Slack -->

# [ConnectorName] Connector

`![Optional Logo Image](path-to-image)`

[![Docs](https://img.shields.io/badge/docs-v3.x-brightgreen.svg?style=flat)](https://hasura.io/docs/3.0/latest/connectors/postgresql/)
[![ndc-hub](https://img.shields.io/badge/ndc--hub-postgres-blue.svg?style=flat)](https://hasura.io/connectors/ndc-postgres)
[![License](https://img.shields.io/badge/license-Apache--2.0-purple.svg?style=flat)](LICENSE.txt)
[![Status](https://img.shields.io/badge/status-alpha-yellow.svg?style=flat)](./readme.md)

[Short description of the connector and its primary purpose.]

This connector is built using the [Rust Data Connector SDK](https://github.com/hasura/ndc-hub#rusk-sdk) and implements the [Data Connector Spec](https://github.com/hasura/ndc-spec).

- [Connector information in the Hasura Hub](https://hasura.io/connectors/[connector-name])
- [Hasura V3 Documentation](https://hasura.io/docs/3.0)
- [Additional relevant links]

## Features

Below, you'll find a matrix of all supported features for the [NAME] connector:

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

1. Create a [Hasura Cloud account](https://console.hasura.io)
2. Install the [CLI](https://hasura.io/docs/3.0/cli/installation/)
3. [Create a project](https://hasura.io/docs/3.0/getting-started/create-a-project)
<!-- TODO: add anything connector-specific here -->

## Using the connector

To use the [NAME] connector, follow these steps in a Hasura project:

1. Add the connector:

   ```bash
   ddn add connector-manifest <connector-name> --subgraph app --hub-connector <connector> --type cloud
   ```

   <!-- TODO: In the snippet above, replace `connector-name` with a connector-specific recommendation, such as
   `pg-connector` and `connector` with the name of the connector as found on the connector hub -->

   In the snippet above, we've used the subgraph `app` as it's available by default; however, you can change this
   value to match any [subgraph](https://hasura.io/docs/3.0/project-configuration/subgraphs) which you've created in your project.

2. Add your connection URI:

   Open your project in your text editor and open the `base.env.yaml` file in the root of your project. Then, add the
   `<CONNECTOR_NAME>_CONNECTION_URI` environment variable with the connection string under the `app` subgraph:

   ```yaml
   supergraph: {}
   subgraphs:
     app:
       <CONNECTOR_NAME>_CONNECTION_URI: "<YOUR_CONNECTION_URI>"
   ```

   Next, update your `/app/<CONNECTOR_NAME>/connector/<CONNECTOR_NAME>.build.hml` file to reference this new environment
   variable:

   ```yaml
   # other configuration above
   CONNECTION_URI:
     valueFromEnv: <CONNECTOR_NAME>_CONNECTION_URI
   ```

    <!-- TODO: Update all <CONNECTOR_NAME> refs in this step to the name you used in step 1's snippet -->

   Notice, when we use an environment variable, we must change the key to `valueFromEnv` instead of `value`. This tells
   Hasura DDN to look for the value in the environment variable we've defined instead of using the value directly.

3. Update the connector manifest and the connector link

   These two steps will (1) allow Hasura to introspect your data source and complete the configuration and (2) deploy the
   connector to Hasura DDN:

   ```bash
   ddn update connector-manifest <CONNECTOR_NAME>
   ```

   ```bash
   ddn update connector-link <CONNECTOR_NAME>
   ```

    <!-- TODO: As before, update <CONNECTOR_NAME> to match step 1 -->

4. [Connector-specific steps]
<!-- TODO: If there are connector-specific configuration steps, such as adding env vars or anything of the like, add
these steps here. -->

## Example

[Optional: Provide an example or use-case scenario for the connector.]

## Documentation

(If required) View the full documentation for the [connectorName] connector [here](./docs/index.md).

## Contributing

Check out our [contributing guide](./docs/contributing.md) for more details.

## License

The [connectorName] connector is available under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

## Additional Sections

[Any other relevant sections or details specific to the connector.]
