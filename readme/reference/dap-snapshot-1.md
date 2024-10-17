---
description: Retrieve changes or updates from a table.
---

# dap incremental

Generates and downloads only the new or modified records of a table within a specified timeframe. This efficient, resource-effective approach helps keep datasets up-to-date with minimal overhead. Incremental queries enable near-real-time updates, reducing the need for frequent full dataset downloads.

### Usage

```
dap [arguments] incremental [flags]
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

**`--since <datetime>`**\
Start timestamp for the incremental query. Examples: `2024-12-01T09:30:00Z`

**`--then <datetime>`**\
End timestamp for the incremental query. Examples: `2024-12-01T09:30:00Z`

**`--format <string> (default: JSONL)`**\
Defines the output format. Available options: {CSV, JSONL, Parquet, TSV}.

**`--output-directory <string> (default: downloads)`**\
Specifies the absolute or relative path to the output directory where the snapshot will be stored.

### Inherited Flags

**`-h, --help`**\
Displays help information for the command.

### Examples

Get new or modified records of the `courses` table from the `canvas` namespace since October 1, 2024\
`$ dap incremental --namespace canvas --table courses --since 2024-11-01T00:00:00`

Get new or modified records of the `courses` table from the `canvas` namespace between October 1, 2024, and October 31, 2024\
`$ dap incremental --namespace canvas --table courses --since 2024-11-01T00:00:00 --then 2024-11-01T00:00:00`

### Related Resources

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Key Concepts</strong></td><td>Get familiar with the concepts in DAP.</td><td></td><td><a href="../../">..</a></td></tr><tr><td><strong>Rate Limits &#x26; Policies</strong></td><td>Learn more about the limits and our policies.</td><td></td><td><a href="https://app.gitbook.com/o/bxMToeZxeTDBdDYnurjg/s/md43XhVX1tvwrv25xyTO/">p0kk Co.</a></td></tr><tr><td><strong>Datasets</strong></td><td>Discover namespaces and available tables</td><td></td><td><a href="../../">..</a></td></tr></tbody></table>



