---
description: Generate a complete and comprehensive snapshot of a table in a namespace. bla
---

# dap snapshot

These queries generate a complete and comprehensive snapshot of the entire dataset at a given point in time.  Snapshot queries are ideal for creating an initial full copy of the dataset or for occasional full updates.&#x20;

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
Client ID obtained from the Identity Service. Skip, if environment variable DAP\_CLIENT\_ID is set.

**`--client-secret <string>`**\
Client Secret obtained from the Identity Service. Skip, if environment variable DAP\_CLIENT\_ID is set.

### Flags

**`--namespace <string>`**\
Specify the data source.&#x20;

**`--table <string>`**\
Specify the table to fetch data from.&#x20;

**`--format <string> (default: JSONL)`**\
Define the output format: {CSV, JSONL, Parquet, TSV}.&#x20;

**`--output-directory <string>`**\
Provide the absolute or relative path to the directory.

### Inherited Flags

**`-h, --help`**\
Show help for command.

### Examples

Get a snapshot of the courses table from Canvas namespace\
`$ dap snapshot --n canvas --t courses`

Get a snapshot of the web\_logs table in CSV format\
`$ dap snapshot --n canvas_logs --t web_logs --f csv`



