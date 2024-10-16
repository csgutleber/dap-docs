---
description: Returns the JSON schema of a table
---

# dap schema

\[insert description] export to a file

### Usage

```
dap [arguments] schema [flags]
```

### Arguments

**`--client-id <string>`**\
Client ID obtained from the Identity Service. Skip, if `DAP_CLIENT_ID` environment variable is set.

**`--client-secret <string>`**\
Client Secret obtained from the Identity Service. Skip, if `DAP_CLIENT_SECRET` environment variable is set.

### Flags

**`--namespace <string>`**\
Specifies the data source (namespace). Available options: {canvas, canvas\_log, catalog}.

**`--table <string>`**\
Specifies the table fetch data from.

**`--output-directory <string>`**\
Specifies the absolute or relative path to the output directory where the snapshot will be stored.

### Inherited Flags

**`-h, --help`**\
Displays help information for the command.

### Examples

Get the schema of the `accounts` table from the Canvas namespace:\
`$ dap schema --n canvas --t accounts`

Get the schema of the `web_logs` table from the canvas\_logs namespace into schemas folder:\
`$ dap snapshot --n canvas_logs --t web_logs --out csv`

### Related

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Key Concepts</td><td></td><td></td></tr><tr><td>Rate Limits &#x26; Policies</td><td></td><td></td></tr></tbody></table>
