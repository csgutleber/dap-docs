
# Data Access Platform (DAP) Setup Guide

## Overview

This guide will walk you through setting up and using the Data Access Platform (DAP) command-line interface (CLI) to access Canvas Data 2. The steps are suitable for IT admins, analysts, and non-technical users. By the end of this guide, you will be able to install the DAP CLI, configure environment variables, and interact with datasets through the DAP API.

---

## 1. Get API Client ID and Secret

To access the DAP API, you will need a Client ID and Secret. These are generated via the Instructure Identity Services.

### Steps:

1. Log into [Instructure Identity Services](https://identity.instructure.com).
2. Select your institution from the drop-down menu and log in.
3. Once authorized, navigate to the dashboard and click **Add New Key**.
4. Enter a name for the key and set the expiration time.
5. Copy the **Client ID** and **Secret** when they appear. **Note:** These are displayed only once. If you lose them, you will need to generate new ones.

---

## 2. Install DAP CLI on Your Computer

The DAP CLI tool allows you to interact with the Canvas Data 2 API. Installation steps differ slightly depending on your operating system.

### For Mac:

1. Install Xcode Developer Tools:

   ```sh
   xcode-select --install
   ```

2. Install Python 3.10+:

   ```sh
   python3 --version
   ```

   If needed, download and install Python from [here](https://www.python.org/downloads/).

3. Install PIP (if not installed by default):

   ```sh
   pip3 --version
   ```

4. Install the DAP CLI tool with PostgreSQL support:

   ```sh
   pip3 install "instructure-dap-client[postgresql]"
   ```

### For Windows:

1. Install Python 3.10+ from [here](https://www.python.org/downloads/windows/).
2. Install the DAP CLI tool using the Windows command prompt:

   ```sh
   pip3 install "instructure-dap-client[postgresql]"
   ```

---

## 3. Store Client Credentials in Environment Variables

For secure access to the API, it's recommended to store your credentials as environment variables. This prevents sensitive information from being exposed in command-line arguments.

### MacOS/Linux:

1. Open Terminal and run the following commands, replacing placeholders with your actual Client ID and Secret:

   ```sh
   export DAP_API_URL='https://api-gateway.instructure.com'
   export DAP_CLIENT_ID='your_canvas_data_client_id'
   export DAP_CLIENT_SECRET='your_canvas_data_secret'
   ```

2. Restart Terminal for changes to take effect.

### Windows:

Follow this [guide to setting environment variables](https://www.computerhope.com/issues/ch000549.htm) or use the `set` command in the Windows command line:

```sh
set DAP_API_URL=https://api-gateway.instructure.com
set DAP_CLIENT_ID=your_canvas_data_client_id
set DAP_CLIENT_SECRET=your_canvas_data_secret
```

---

## 4. Work with Databases

DAP CLI allows you to interact with PostgreSQL or MySQL databases. You will need the connection string of your database for DAP to function correctly.

### Connection String Format:

```
protocol://username:password@host:port/database_name
```

### Example for PostgreSQL:

```
postgresql://user:password@localhost:5432/mydatabase
```

---

### 4.1 Obtain a Full Snapshot of a Table

Use the `initdb` command to download a full snapshot of a table and store it in your database.

#### Command:

```sh
dap initdb --connection-string postgresql://user:password@localhost/mydb --namespace canvas --table accounts
```

---

### 4.2 Synchronize Data with a Table

After obtaining a snapshot, keep your database updated with the `syncdb` command. This ensures incremental changes are applied to your table.

#### Command:

```sh
dap syncdb --connection-string postgresql://user:password@localhost/mydb --namespace canvas --table accounts
```

---

### 4.3 Changing the Temporary Storage Location

If you need to change the temporary storage directory for data processing, you can configure the location using the following command-line option:

```sh
dap syncdb --temp-dir /new/temp/location --connection-string postgresql://user:password@localhost/mydb --namespace canvas --table accounts
```

---

## 5. Export Data

You can export data using either the snapshot or incremental methods, depending on your use case.

### 5.1 Snapshot Export

A snapshot export captures a full copy of the dataset at a point in time.

{% hint style="warning" %}
Regular use of snapshots is not recommended, as they are resource-intensive for the API and costly to process on the client side.
{% endhint %}

#### Command:

```sh
dap snapshot --namespace canvas --table accounts
```

### 5.2 Incremental Export

An incremental export captures only the data that has changed since your last export.

#### Command:

```sh
dap incremental --namespace canvas --table accounts --since YYYY-MM-DDTHH:MM:SSZ
```

### Related Resources

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Key Concepts</strong></td><td>Get familiar with the concepts in DAP.</td><td></td><td><a href="../../">..</a></td></tr><tr><td><strong>Rate Limits &#x26; Policies</strong></td><td>Learn more about the limits and our policies.</td><td></td><td><a href="https://app.gitbook.com/o/bxMToeZxeTDBdDYnurjg/s/md43XhVX1tvwrv25xyTO/">p0kk Co.</a></td></tr><tr><td><strong>Datasets</strong></td><td>Discover namespaces and available tables</td><td></td><td><a href="../../">..</a></td></tr></tbody></table>
