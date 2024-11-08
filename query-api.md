---
description: Access your organization’s Instructure data using a robust REST API.
---

# Query API

The DAP Query API is a robust RESTful API that enables seamless, programmatic access to data within the Data Access Platform (DAP). Designed to handle large-scale data retrieval, it supports secure, flexible interactions with Instructure datasets.

{% hint style="info" %}
Before using they Query API, it is recommended to familiarize yourself with the [key concepts of DAP](key-concepts.md).
{% endhint %}

### API Endpoint <a href="#api-endpoint" id="api-endpoint"></a>

The Query API can be accessed via the following endpoint:

```bash
https://api-gateway.instructure.com/dap/
```

### Conventions

The HTTP method used in an endpoint determines the type of action performed on a resource. Common methods include `GET`, `POST`, `DELETE`, and `PATCH`. Refer to the REST API reference documentation for details on the HTTP methods for each endpoint.

### Rate Limiting <a href="#api-reference" id="api-reference"></a>

DAP CLI follows the [rate limiting policies](./) of DAP. Be mindful of these limits when making requests.

### Status Codes

The Query API uses standard HTTP response codes to indicate the success or failure of requests:

* Codes in the **`2xx`** range indicate success.
* Codes in the **`4xx`** range indicate incorrect or incomplete parameters (e.g. invalid authentication credentials, non-exist namespace etc.).
* Codes in the **`5xx`** range indicate a server-side issue  (e.g. gateway timeout error, restricted client access etc.).

### Where To Get Help

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>DAP Community</td><td>Visit our forums to connect with the community and learn more about DAP.</td><td><a href="https://community.canvaslms.com/t5/Data-and-Analytics-Group/gh-p/data">https://community.canvaslms.com/t5/Data-and-Analytics-Group/gh-p/data</a></td></tr><tr><td>Support</td><td>To report bugs or request new features, open a ticket for our Support Team.</td><td><a href="mailto:canvasdatahelp@instructure.com">mailto:canvasdatahelp@instructure.com</a></td></tr></tbody></table>
