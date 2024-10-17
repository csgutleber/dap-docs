---
description: Delete a synchronized table in a database
---

# dap dropdb

With the `dropdb` command, you can completely drop a table from your database that was previously created with `initdb`. An error is triggered if the given table does not exist in the target database.

{% hint style="info" %}
This command not only drops the specified table from the target database but also removes meta-information used for synchronization.
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

Drop the `courses` table from your database \
`$ dap dropdb --namespace canvas --table courses`

Same example with the connection string defined in the command\
`$dap dropdb --namespace canvas --table courses --connection-string postgresql://scott:password@server.example.com/testdb`

### Related Resources

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Key Concepts</strong></td><td>Get familiar with the concepts in DAP.</td><td></td><td><a href="../../">..</a></td></tr><tr><td><strong>Rate Limits &#x26; Policies</strong></td><td>Learn more about the limits and our policies.</td><td></td><td><a href="https://app.gitbook.com/o/bxMToeZxeTDBdDYnurjg/s/md43XhVX1tvwrv25xyTO/">p0kk Co.</a></td></tr><tr><td><strong>Datasets</strong></td><td>Discover namespaces and available tables</td><td></td><td><a href="../../">..</a></td></tr></tbody></table>



