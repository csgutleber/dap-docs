---
description: Generate a complete snapshot of a table within a specific namespace.
---

# dap snapshot

The `dap snapshot` command generates a full snapshot of a dataset at a specific point in time. This is ideal for creating an initial full copy of the dataset or performing occasional full updates. Snapshots are useful for comprehensive analyses, audits, and backups.

{% hint style="warning" %}
Regular use of snapshots is not recommended, as they are resource-intensive for the API and costly to process on the client side.
{% endhint %}

### Usage

```
dap [arguments] snapshot [flags]
```

### Arguments

**`--client-id <string>`**\
Client ID obtained from the Identity Service. Skip, if `DAP_CLIENT_ID` environment variable is set.

**`--client-secret <string>`**\
Client Secret obtained from the Identity Service. Skip, if `DAP_CLIENT_SECRET` environment variable is set.

### Flags

**`--namespace <string>`**\
Specifies the data source (namespace).

**`--table <string>`**\
Specifies the table fetch data from.

**`--format <string> (default: JSONL)`**\
Defines the output format. Available options: {CSV, JSONL, Parquet, TSV}.

**`--output-directory <string>`**\
Specifies the absolute or relative path to the output directory where the snapshot will be stored.

### Inherited Flags

**`-h, --help`**\
Displays help information for the command.

### Examples

Get a snapshot of the `courses` table from the Canvas namespace:\
`$ dap snapshot --n canvas --t courses`

Get a snapshot of the `web_logs` table in CSV format\
`$ dap snapshot --n canvas_logs --t web_logs --f csv`

### Related

<table data-view="cards"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>Key Concepts</td><td></td><td></td></tr><tr><td>Rate Limits &#x26; Policies</td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>



