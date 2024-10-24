# Getting Started

## Overview

This guide will walk you through setting up and using the Data Access Platform (DAP) command-line interface (CLI) to access Canvas Data 2. The steps are suitable for IT admins, analysts, and non-technical users. By the end of this guide, you will be able to install the DAP CLI, configure environment variables, and interact with datasets through the DAP API.

***

## 1. Get API Client ID and Secret

To access the DAP API, you will need a Client ID and Secret. These are generated via the Instructure Identity Services.

### Steps:

1. Log into [Instructure Identity Services](https://identity.instructure.com).
2. Select your institution from the drop-down menu and log in.
3. Once authorized, navigate to the dashboard and click **Add New Key**.
4. Enter a name for the key and set the expiration time.
5. Copy the **Client ID** and **Secret** when they appear. **Note:** These are displayed only once. If you lose them, you will need to generate new ones.

***

## 2. Install DAP CLI on Your Computer

The DAP CLI tool allows you to interact with the Canvas Data 2 API. Installation steps differ slightly depending on your operating system.

### For Mac:

1.  Install Xcode Developer Tools:

    ```sh
    xcode-select --install
    ```
2.  Install Python 3.10+:

    ```sh
    python3 --version
    ```

    If needed, download and install Python from [here](https://www.python.org/downloads/).
3.  Install PIP (if not installed by default):

    ```sh
    pip3 --version
    ```
4.  Install the DAP CLI tool with PostgreSQL support:

    ```sh
    pip3 install "instructure-dap-client[postgresql]"
    ```

### For Windows:

1. Install Python 3.10+ from [here](https://www.python.org/downloads/windows/).
2.  Install the DAP CLI tool using the Windows command prompt:

    ```sh
    pip3 install "instructure-dap-client[postgresql]"
    ```

***

## 3. Store Client Credentials in Environment Variables

For secure access to the API, it's recommended to store your credentials as environment variables. This prevents sensitive information from being exposed in command-line arguments.

### MacOS/Linux:

1.  Open Terminal and run the following commands, replacing placeholders with your actual Client ID and Secret:

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

***

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

***

### 4.1 Obtain a Full Snapshot of a Table

Use the `initdb` command to download a full snapshot of a table and store it in your database.

#### Command:

```sh
dap initdb --connection-string postgresql://user:password@localhost/mydb --namespace canvas --table accounts
```

***

### 4.2 Synchronize Data with a Table

After obtaining a snapshot, keep your database updated with the `syncdb` command. This ensures incremental changes are applied to your table.

#### Command:

```sh
dap syncdb --connection-string postgresql://user:password@localhost/mydb --namespace canvas --table accounts
```

***

### 4.3 Changing the Temporary Storage Location

If you need to change the temporary storage directory for data processing, you can configure the location using the following command-line option:

```sh
dap syncdb --temp-dir /new/temp/location --connection-string postgresql://user:password@localhost/mydb --namespace canvas --table accounts
```

***

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

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Key Concepts</strong></td><td>Get familiar with the concepts in DAP.</td><td></td><td><a href="../">..</a></td></tr><tr><td><strong>Rate Limits &#x26; Policies</strong></td><td>Learn more about the limits and our policies.</td><td></td><td><a href="https://app.gitbook.com/o/bxMToeZxeTDBdDYnurjg/s/md43XhVX1tvwrv25xyTO/">p0kk Co.</a></td></tr><tr><td><strong>Datasets</strong></td><td>Discover namespaces and available tables</td><td></td><td><a href="../">..</a></td></tr></tbody></table>

### Overview <a href="#overview" id="overview"></a>

This guide will walk you through setting up and using the Data Access Platform (DAP) command-line interface (CLI) to access Canvas Data 2. The steps are suitable for IT admins, analysts, and non-technical users. By the end of this guide, you will be able to install the DAP CLI, configure environment variables, and interact with datasets through the DAP API. t

***

### 1. Get API Client ID and Secret <a href="#id-1.-get-api-client-id-and-secret" id="id-1.-get-api-client-id-and-secret"></a>

To access the DAP API, you will need a Client ID and Secret. These are generated via the Instructure Identity Services.

#### Steps: <a href="#steps" id="steps"></a>

1. Log into [Instructure Identity Services](https://identity.instructure.com/).
2. Select your institution from the drop-down menu and log in.
3. Once authorized, navigate to the dashboard and click **Add New Key**.
4. Enter a name for the key and set the expiration time.
5. Copy the **Client ID** and **Secret** when they appear. **Note:** These are displayed only once. If you lose them, you will need to generate new ones.

***

### 2. Install DAP CLI on Your Computer <a href="#id-2.-install-dap-cli-on-your-computer" id="id-2.-install-dap-cli-on-your-computer"></a>

The DAP CLI tool allows you to interact with the Canvas Data 2 API. Installation steps differ slightly depending on your operating system.

#### For Mac: <a href="#for-mac" id="for-mac"></a>

1.  Install Xcode Developer Tools:

    Copy

    ```
    xcode-select --install
    ```
2.  Install Python 3.10+:

    Copy

    ```
    python3 --version
    ```

    If needed, download and install Python from [here](https://www.python.org/downloads/).
3.  Install PIP (if not installed by default):

    Copy

    ```
    pip3 --version
    ```
4.  Install the DAP CLI tool with PostgreSQL support:

    Copy

    ```
    pip3 install "instructure-dap-client[postgresql]"
    ```

#### For Windows: <a href="#for-windows" id="for-windows"></a>

1. Install Python 3.10+ from [here](https://www.python.org/downloads/windows/).
2.  Install the DAP CLI tool using the Windows command prompt:

    Copy

    ```
    pip3 install "instructure-dap-client[postgresql]"
    ```

***

### 3. Store Client Credentials in Environment Variables <a href="#id-3.-store-client-credentials-in-environment-variables" id="id-3.-store-client-credentials-in-environment-variables"></a>

For secure access to the API, it's recommended to store your credentials as environment variables. This prevents sensitive information from being exposed in command-line arguments.

#### MacOS/Linux: <a href="#macos-linux" id="macos-linux"></a>

1.  Open Terminal and run the following commands, replacing placeholders with your actual Client ID and Secret:

    Copy

    ```
    export DAP_API_URL='https://api-gateway.instructure.com'
    export DAP_CLIENT_ID='your_canvas_data_client_id'
    export DAP_CLIENT_SECRET='your_canvas_data_secret'
    ```
2. Restart Terminal for changes to take effect.

#### Windows: <a href="#windows" id="windows"></a>

Follow this [guide to setting environment variables](https://www.computerhope.com/issues/ch000549.htm) or use the `set` command in the Windows command line:

Copy

```
set DAP_API_URL=https://api-gateway.instructure.com
set DAP_CLIENT_ID=your_canvas_data_client_id
set DAP_CLIENT_SECRET=your_canvas_data_secret
```

***

### 4. Work with Databases <a href="#id-4.-work-with-databases" id="id-4.-work-with-databases"></a>

DAP CLI allows you to interact with PostgreSQL or MySQL databases. You will need the connection string of your database for DAP to function correctly.

#### Connection String Format: <a href="#connection-string-format" id="connection-string-format"></a>

Copy

```
protocol://username:password@host:port/database_name
```

#### Example for PostgreSQL: <a href="#example-for-postgresql" id="example-for-postgresql"></a>

Copy

```
postgresql://user:password@localhost:5432/mydatabase
```

***

#### 4.1 Obtain a Full Snapshot of a Table <a href="#id-4.1-obtain-a-full-snapshot-of-a-table" id="id-4.1-obtain-a-full-snapshot-of-a-table"></a>

Use the `initdb` command to download a full snapshot of a table and store it in your database.

**Command:**

Copy

```
dap initdb --connection-string postgresql://user:password@localhost/mydb --namespace canvas --table accounts
```

***

#### 4.2 Synchronize Data with a Table <a href="#id-4.2-synchronize-data-with-a-table" id="id-4.2-synchronize-data-with-a-table"></a>

After obtaining a snapshot, keep your database updated with the `syncdb` command. This ensures incremental changes are applied to your table.

**Command:**

Copy

```
dap syncdb --connection-string postgresql://user:password@localhost/mydb --namespace canvas --table accounts
```

***

#### 4.3 Changing the Temporary Storage Location <a href="#id-4.3-changing-the-temporary-storage-location" id="id-4.3-changing-the-temporary-storage-location"></a>

If you need to change the temporary storage directory for data processing, you can configure the location using the following command-line option:

Copy

```
dap syncdb --temp-dir /new/temp/location --connection-string postgresql://user:password@localhost/mydb --namespace canvas --table accounts
```

***

### 5. Export Data <a href="#id-5.-export-data" id="id-5.-export-data"></a>

You can export data using either the snapshot or incremental methods, depending on your use case.

#### 5.1 Snapshot Export <a href="#id-5.1-snapshot-export" id="id-5.1-snapshot-export"></a>

A snapshot export captures a full copy of the dataset at a point in time.

Regular use of snapshots is not recommended, as they are resource-intensive for the API and costly to process on the client side.

**Command:**

Copy

```
dap snapshot --namespace canvas --table accounts
```

#### 5.2 Incremental Export <a href="#id-5.2-incremental-export" id="id-5.2-incremental-export"></a>

An incremental export captures only the data that has changed since your last export.

**Command:**

Copy

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>asdfdsafad</td><td>sdsafdsafdsaf</td><td></td><td><a href="../command-line/reference/">reference</a></td></tr><tr><td></td><td></td><td></td><td></td></tr></tbody></table>



```
dap incremental --namespace canvas --table accounts --since YYYY-MM-DDTHH:MM:SSZ

```
