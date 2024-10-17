---
description: Generate a complete snapshot of a table within a specific namespace.
---

# dap snapshot

This command generates and download a full snapshot of a table table within a namespace at a specific point in time. This is ideal for creating an initial full copy of the dataset or performing occasional full updates. Snapshots are useful for comprehensive analyses, audits, and backups.

{% hint style="warning" %}
**Regular use of snapshots is not recommended**, as they are resource-intensive for the API and costly to process on the client side.
{% endhint %}

### Usage

```
dap [arguments] snapshot [flags]
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

**`--format <string> (default: JSONL)`**\
Defines the output format. Available options: {CSV, JSONL, Parquet, TSV}.

**`--output-directory <string> (default: downloads)`**\
Specifies the absolute or relative path to the output directory where the snapshot will be stored.

### Inherited Flags

**`-h, --help`**\
Displays help information for the command.

### Examples

Get a snapshot of the `courses` table from the `canvas` namespace:\
`$ dap snapshot --namespace canvas --table courses`

Get a snapshot of the `web_logs` table from `canvas_log` namespace in CSV format\
`$ dap snapshot --namespace canvas_logs --table web_logs --format csv`

### Related Resources

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Key Concepts</strong></td><td>Get familiar with the concepts in DAP.</td><td></td><td><a href="../../">..</a></td></tr><tr><td><strong>Rate Limits &#x26; Policies</strong></td><td>Learn more about the limits and our policies.</td><td></td><td><a href="https://app.gitbook.com/o/bxMToeZxeTDBdDYnurjg/s/md43XhVX1tvwrv25xyTO/">p0kk Co.</a></td></tr><tr><td><strong>Datasets</strong></td><td>Discover namespaces and available tables</td><td></td><td><a href="../../">..</a></td></tr></tbody></table>



