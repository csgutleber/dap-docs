---
description: Retrieve the names of all tables available in a namespace.
---

# dap list

Get a list of available tables within a selected namespace. This can help you identify which tables are available for further operations, such as snapshots or incremental updates.

### Usage

```
dap [arguments] list [flags]
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

### Inherited Flags

**`-h, --help`**\
Displays help information for the command.

### Examples

List tables from the `canvas` namespace\
`$ dap list --namespace canvas`

### Related Resources

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Key Concepts</strong></td><td>Get familiar with the concepts in DAP.</td><td></td><td><a href="../../">..</a></td></tr><tr><td><strong>Rate Limits &#x26; Policies</strong></td><td>Learn more about the limits and our policies.</td><td></td><td><a href="https://app.gitbook.com/o/bxMToeZxeTDBdDYnurjg/s/md43XhVX1tvwrv25xyTO/">p0kk Co.</a></td></tr><tr><td><strong>Datasets</strong></td><td>Discover namespaces and available tables</td><td></td><td><a href="../../">..</a></td></tr></tbody></table>
