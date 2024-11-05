# Rate Limits & Policies

To maintain fair usage and performance, the following rate limits have been implemented on the [DAP Query API](https://github.com/instructure/data-access-platform-documentation/blob/master/docs/query-api.md).

### GET Requests

<table data-full-width="true"><thead><tr><th>Requesst</th><th>Endpoint</th><th>Limit</th></tr></thead><tbody><tr><td>List tables</td><td><code>/query/{namespace}/table</code></td><td>5 requests per minute</td></tr><tr><td>Get table schema</td><td><code>/query/{namespace}/table/[table_name]/schema</code></td><td>500 calls per minute</td></tr><tr><td>Get job status</td><td><code>/job/</code></td><td>500 calls per minute</td></tr></tbody></table>

### POST Requests

<table data-full-width="true"><thead><tr><th></th><th>Request</th><th>Limit</th></tr></thead><tbody><tr><td>Create query job</td><td><code>/query/canvas_logs/table/[table_name]/data</code></td><td>5 calls per minute</td></tr><tr><td>Create pre-signed URLs</td><td><code>/object/url</code></td><td>200 calls per minute</td></tr></tbody></table>

{% hint style="info" %}
These limits are not additive. Reaching a limit for one request type or endpoint does not affect the limits of other types or endpoints. For example, if you reach the limit for GET requests on `/dap/query/canvas/table`, it will not impact your ability to make **POST** requests or **GET** requests on other endpoints.
{% endhint %}

If you anticipate needing higher limits, please reach out to your Customer Success Manager to discuss your requirements.

Learn more details about [Instructure's Canvas API policies](https://www.instructure.com/policies/canvas-api-policy).
