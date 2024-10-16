---
description: '-'
---

# dap incremental

\-

### Usage

```
dap [arguments] incremental [flags]
```

### Arguments

**`--client-id <string>`**\
Client ID obtained from the Identity Service. Skip, if environment variable DAP\_CLIENT\_ID is set.

**`--client-secret <string>`**\
Client Secret obtained from the Identity Service. Skip, if environment variable DAP\_CLIENT\_ID is set.

### Flags

**`--namespace <string>`**\
Specify the data source.

**`--table <string>`**\
Specify the table to fetch data from.

**`--format <string> (default: JSONL)`**\
Define the output format: {CSV, JSONL, Parquet, TSV}.

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
