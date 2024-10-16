---
description: Access your organization's Instructure data from the command line.
---

# DAP CLI

The Data Access Platform (DAP) CLI is a command-line tool that enables efficient access to large volumes of educational data with high fidelity and low latency. It adheres to a canonical data model and integrates with various educational products.

Built on top of the [Query API](https://www.notion.so/DAP-CLI-121159a404cd8009a33de73f6ae93ee7?pvs=21), DAP CLI allows you to:

* Fetch initial snapshots of data.
* Track incremental changes.
* Initialize and synchronize a supported database with [DAP data](https://data-access-platform-api.s3.amazonaws.com/tables/index.html).

Before using DAP CLI, it is recommended to familiarize yourself with the key concepts of DAP.

### Requirements

* **Supported Operating Systems:** Ubuntu 22, Windows 11, Windows Server 2022, macOS 1
* **Supported Database Integrations:** PostgreSQL 16.1+, MySQL 8.2+

### Installation

The DAP CLI is available as a Python package in the [Python Package Index (PyPI)](https://pypi.org/project/instructure-dap-client/). To install, use the following command:

```bash
pip install instructure-dap-client
```

If you are synchronizing with a database, install the package with the following features:

```bash
pip install "instructure-dap-client[postgresql,mysql]"
```

Learn more details about the installation and setup in the [Getting Started](https://app.gitbook.com/o/bxMToeZxeTDBdDYnurjg/s/md43XhVX1tvwrv25xyTO/) guide.

### Commands

The basic syntax is:

```bash
dap [arguments] [command] [flags]
```

Refer to [Reference](https://app.gitbook.com/o/bxMToeZxeTDBdDYnurjg/s/md43XhVX1tvwrv25xyTO/) section in the sidebar for a list of available commands. Or, run the `dap --help` command to get this information right in your terminal.

### Upgrading DAP CLI

To ensure optimal performance, always use the latest version of DAP CLI. Check your current version and available updates with:

```bash
dap --version
```

To upgrade to the latest version, run:

```bash
pip install --upgrade instructure-dap-client
pip install --upgrade "instructure-dap-client[postgresql,mysql]"
```

### Rate Limiting

DAP CLI follows the [rate limiting policies of DAP](https://www.notion.so/DAP-CLI-121159a404cd8009a33de73f6ae93ee7?pvs=21). Be aware of these limits when making requests.

### Logging & Debugging

The default log level is `info`, and messages are printed to the console. To change the log level or save logs to a file, use the following parameters:

```bash
dap --loglevel debug --logfile dap.log initdb --namespace canvas --table accounts
```

### Where To Get Help

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th></th><th data-type="content-ref"></th></tr></thead><tbody><tr><td>DAP Community</td><td>Visit our forums to connect with the community and learn more about DAP.</td><td></td><td></td></tr><tr><td>Support</td><td>To report bugs or request new features, open a ticket for our Support Team.</td><td></td><td></td></tr></tbody></table>

