---
description: Import a full snapshot of a table into a database.
---

# dap initdb

The `dap initdb` command automatically fetches the schema and data from DAP, connects to your specified database, creates the necessary table based on the schema, and inserts the data into the table. This process simplifies the initialization of a database with DAP data.

{% hint style="warning" %}
**Type juggling is not supported.** The data types specified in the schema from the DAP API must be strictly followed during table creation and data insertion.
{% endhint %}

### Usage

```
dap [arguments] initdb [flags]
```

### Arguments

**`--base-url <string>`**\
URL to the DAP API endpoint. Use `https://api-gateway.instructure.com`.

**`--client-id <string>`**\
Client ID obtained from the Identity Service. Skip, if `DAP_CLIENT_ID` environment variable is set.

**`--client-secret <string>`**\
Client Secret obtained from the Identity Service. Skip, if `DAP_CLIENT_SECRET` environment variable is set.

### Flags

**`--namespace <string>`**\
Specifies the data source (namespace). Available options: {canvas, canvas\_log, catalog}.

**`--table <string>`**\
Specifies the table fetch data from.

**`--connection-string <string>`**\
The connection string used to connect to the target database. It must follow RFC 3986 format:\
`dialect://username:password@host:port/database`. Skip, if `DAP_CONNECTION_STRING` environment variable is set.

### Inherited Flags

**`-h, --help`**\
Displays help information for the command.

### Examples

Get a snapshot of the `courses` table from the `canvas` namespace and insert into your database\
`$ dap initdb --namespace canvas --table courses`

Same example with the connection string defined in the command\
`$dap initdb --namespace canvas --table courses --connection-string postgresql://scott:password@server.example.com/testdb`

### Related Resources

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Key Concepts</strong></td><td>Get familiar with the concepts in DAP.</td><td></td><td><a href="../../">..</a></td></tr><tr><td><strong>Rate Limits &#x26; Policies</strong></td><td>Learn more about the limits and our policies.</td><td></td><td><a href="https://app.gitbook.com/o/bxMToeZxeTDBdDYnurjg/s/md43XhVX1tvwrv25xyTO/">p0kk Co.</a></td></tr><tr><td><strong>Datasets</strong></td><td>Discover namespaces and available tables</td><td></td><td><a href="../../">..</a></td></tr></tbody></table>



