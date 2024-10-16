---
description: Retrieve the names of all tables available in a specified namespace.
---

# dap list

The `dap list` command allows you to view the available tables within a selected namespace. This can help you identify which tables are available for further operations, such as snapshots or incremental updates.

### Usage

```
dap [arguments] list [flags]
```

### Arguments

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

Get a list of tables from the Canvas namespace:\
`$ dap list --n canvas`

### Related

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Key Concepts</td><td></td><td></td></tr><tr><td>Rate Limits &#x26; Policies</td><td></td><td></td></tr></tbody></table>



