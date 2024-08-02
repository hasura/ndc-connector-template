<!-- TODO: Hiya, Connector Author! Throughout this template, you'll find TODO comments to help guide you and ensure
you've updated this README to be ready for users. If you have questions, shout at the docs team on #team-docs in Slack -->

# [ConnectorName] Data Connector

`![Optional Logo Image](path-to-image)`

[![Docs](https://img.shields.io/badge/docs-v3.x-brightgreen.svg?style=flat)](https://hasura.io/docs/3.0/latest/connectors/postgresql/)
[![ndc-hub](https://img.shields.io/badge/ndc--hub-postgres-blue.svg?style=flat)](https://hasura.io/connectors/ndc-postgres)
[![License](https://img.shields.io/badge/license-Apache--2.0-purple.svg?style=flat)](LICENSE.txt)
[![Status](https://img.shields.io/badge/status-alpha-yellow.svg?style=flat)](./readme.md)

[Short description of the connector and its primary purpose.]

This connector is built using the [Rust Data Connector SDK](https://github.com/hasura/ndc-hub#rusk-sdk) and implements the [Data Connector Spec](https://github.com/hasura/ndc-spec).

- [Connector information in the Hasura Hub](https://hasura.io/connectors/[connector-name])
- [Hasura V3 Documentation](https://hasura.io/docs/3.0)

Docs for the [connectorName] data connector:

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
ddn connector init <connector-name>  --subgraph my_subgraph/subgraph.yaml  --hub-connector hasura/<connector>
```

  <!-- TODO: In the snippet above, replace `connector-name` with a connector-specific recommendation, such as
  `pg-connector` and `connector` with the name of the connector as found on the connector hub -->

In the snippet above, we've used the subgraph `my_subgraph` as an example; however, you should change this
value to match any subgraph which you've created in your project.

### Step 3: Modify the connector's port

When you initialized your connector, the CLI generated a set of configuration files, including a Docker Compose file for
the connector. Typically, connectors default to port `8080`. Each time you add a connector, we recommend incrementing the published port by one to avoid port collisions.

As an example, if your connector's configuration is in `my_subgraph/connector/<connector-name>/compose.yaml`, you can modify the published port to
reflect a value that isn't currently being used by any other connectors:

```yaml
ports:
  - mode: ingress
    target: 8080
    published: "8082"
    protocol: tcp
```

  <!-- TODO: As before, update <CONNECTOR_NAME> to match step 2 -->

### Step 4: Add environment variables

Now that our connector has been scaffolded out for us, we need to provide a connection string so that the data source can be introspected and the
boilerplate configuration can be taken care of by the CLI.

The CLI has provided an `.env.local` file for our connector in the `my_subgraph/connector/<connector-name>` directory. We can add a key-value pair
of `CONNECTION_URI` along with the connection string itself to this file, and our connector will use this to connect to our database.

**Note that `CONNECTION_URI` may not always be a required key. You should consult the `supportedEnvironmentVariables` array in your
`.hasura-connector/connect-metadata.yaml` file to determine what's required.**

The file, after adding the `CONNECTION_URI`, should look like this example:

```env
OTEL_EXPORTER_OTLP_TRACES_ENDPOINT=http://local.hasura.dev:4317
OTEL_SERVICE_NAME=my_subgraph_<connector-name>
CONNECTION_URI=<connection-uri>
```

  <!-- TODO: As before, update <CONNECTOR_NAME> to match step 2 — additionally, feel free to call out the specific
  variables which are required above -->

### Step 5: Introspect your data source

With the connector configured, we can now use the CLI to introspect our database and create a source-specific configuration file for our connector.

```bash
ddn connector introspect --connector my_subgraph/connector/<connector-name>/connector.local.yaml
```

  <!-- TODO: As before, update <CONNECTOR_NAME> to match step 2 -->

### Step 6. Create the Hasura metadata

Hasura DDN uses a concept called "connector linking" to take [NDC-compliant](https://github.com/hasura/ndc-spec)
configuration JSON files for a data connector and transform them into an `hml` (Hasura Metadata Language) file as a
[`DataConnectorLink` metadata object](https://hasura.io/docs/3.0/supergraph-modeling/data-connectors#dataconnectorlink-dataconnectorlink).

Basically, metadata objects in `hml` files define our API.

First we need to create this `hml` file with the `connector-link add` command and then convert our configuration files
into `hml` syntax and add it to this file with the `connector-link update` command.

Let's name the `hml` file the same as our connector, `<connector-name>`:

```bash
ddn connector-link add <connector-name> --subgraph my_subgraph/subgraph.yaml
```

The new file is scaffolded out at `my_subgraph/metadata/<connector-name>/<connector-name>.hml`.

### Step 7. Update the environment variables

The generated file has two environment variables — one for reads and one for writes — that you'll need to add to your subgraph's `.env.my_subgraph.local` file.
Each key is prefixed by the subgraph name, an underscore, and the name of the connector. Ensure the port value matches what is published in your connector's docker compose file.

As an example:

```env
MY_SUBGRAPH_<CONNECTOR-NAME>_READ_URL=http://local.hasura.dev:<port>
MY_SUBGRAPH_<CONNECTOR-NAME>_WRITE_URL=http://local.hasura.dev:<port>
```

These values are for the connector itself and utilize `local.hasura.dev` to ensure proper resolution within the docker container.

  <!-- TODO: As before, update <CONNECTOR_NAME> to match step 2 -->

### Step 8. Start the connector's Docker Compose

Let's start our connector's Docker Compose file by running the following from inside the connector's subgraph:

```bash
docker compose -f compose.yaml up
```

  <!-- TODO: As before, update <CONNECTOR_NAME> to match step 2 -->

### Step 9. Update the new `DataConnectorLink` object

Finally, now that our `DataConnectorLink` has the correct environment variables configured for the connector,
we can run the update command to have the CLI look at the configuration JSON and transform it to reflect our database's
schema in `hml` format. In a new terminal tab, run:

```bash
ddn connector-link update <connector-name> --subgraph my_subgraph/subgraph.yaml --env-file my_subgraph/.env.my_subgraph.local
```

After this command runs, you can open your `my_subgraph/metadata/<connector-name>.hml` file and see your metadata completely
scaffolded out for you 🎉

### Step 10. [Connector-specific steps]

<!-- TODO: If there are connector-specific configuration steps, such as adding env vars or anything of the like, add
these steps here. -->

### Step 11. Deploy your connector

Connectors can be deployed to Hasura DDN or, if you choose, your own infrastructure.

#### Deploy [ConnectorName] to Hasura DDN

Prepare a `env.cloud` file for the connector. This should utilize whichever environment variables, such as a connection
string, you intend to use with your deployed supergraph. As an example:

```env
CONNECTION_URI=<database-connection-uri>
```

Then, run the following command taking care to update the referenced paths to match your project structure:

```sh
ddn connector build create \
  --connector my_subgraph/connector/my_connector/connector.cloud.yaml \
  --target-env-file my_subgraph/.env.my_subgraph.cloud \
  --target-subgraph my_subgraph/subgraph.yaml \
  --target-connector-link my_connector
```

This will deploy your connector and update your project's metadata.

#### Deploy [ConnectorName] to your own infrastructure

As a connector is an HTTP service built using Docker, you can host your connectors anywhere Docker containers can be
hosted.

On your own self- or cloud-hosted infrastructure, create a new build from within the connector's directory:

```sh
docker compose build
```

Then, bring the connector up:

```sh
docker compose up -d
```

And verify the connector is running:

```sh
docker ps
```

You'll need to follow whatever steps are necessary to expose your connector's port so that Hasura DDN can connect to it.
Additionally, you'll need to update any cloud environment variables that your deployed supergraph needs from this
connector (e.g., `MY_SUBGRAPH_MY_CONNECTOR_READ_URL`) to match your deployed connector's endpoint.

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
