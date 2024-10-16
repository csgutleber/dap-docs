---
description: Generate a complete and comprehensive snapshot of a table in a namespace.
---

# dap snapshot

These queries generate a complete and comprehensive snapshot of the entire dataset at a given point in time. Snapshot queries are ideal for creating an initial full copy of the dataset or for occasional full updates.

It is not recommended to request snapshots regularly, as it is resource-intensive on the API side and expensive to process on the client side. This approach ensures that you have a full, standalone version of the data, which can be useful for comprehensive analyses, audits, and backups.

{% hint style="info" %}
For the `canvas_logs` dataset, particularly the `web_logs` table, there is a 30-day data retention policy, so the snapshot will not cover the entire dataset but only the last 30 days of data.
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
