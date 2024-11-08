# Rate Limits & Policies

## Rate Limits

To maintain fair usage and performance, the following rate limits have been implemented on the [DAP Query API](https://github.com/instructure/data-access-platform-documentation/blob/master/docs/query-api.md).

<table data-full-width="false"><thead><tr><th width="203">Request</th><th width="403">Endpoint</th><th>Calls per minute</th></tr></thead><tbody><tr><td>Create  job</td><td>POST <code>/query/{namespace}/table/{table}/data</code></td><td>5</td></tr><tr><td>Get job</td><td>GET <code>/job/</code></td><td>500</td></tr><tr><td>List tables</td><td>GET <code>/query/{namespace}/table</code></td><td>5</td></tr><tr><td>Get table schema</td><td>GET <code>/query/{namespace}/table/{table}/schema</code></td><td>500</td></tr><tr><td>Create pre-signed URLs</td><td>POST <code>/object/url</code></td><td>200</td></tr></tbody></table>

These limits are independent for each endpoint. Reaching the limit for one request type or endpoint does not impact the limits for other types or endpoints. For example, reaching the limit for GET requests on `/dap/query/canvas/table` will not affect your ability to make POST requests or use other GET endpoints.

{% hint style="info" %}
Since the CLI and Client Library are built on top of the Query API and use its endpoints, these rate limits apply to them as well.&#x20;
{% endhint %}

If you anticipate needing higher limits, please contact your Customer Success Manager to discuss your requirements.

## Data Refresh

Data in DAP is refreshed every 4 hours.

## Further Resources

Learn more details about [Instructure's Canvas API policies](https://www.instructure.com/policies/canvas-api-policy).
