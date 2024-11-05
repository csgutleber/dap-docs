# Rate Limits & Policies

To maintain fair usage and performance, the following rate limits have been implemented on the [DAP Query API](https://github.com/instructure/data-access-platform-documentation/blob/master/docs/query-api.md).

### GET Requests

| Requesst         | Endpoint                                       | Limit                 |
| ---------------- | ---------------------------------------------- | --------------------- |
| List tables      | `/query/{namespace}/table`                     | 5 requests per minute |
| Get table schema | `/query/{namespace}/table/[table_name]/schema` | 500 calls per minute  |
| Get job status   | `/job/`                                        | 500 calls per minute  |

### POST Requests

|                        | Request                                      | Limit                |
| ---------------------- | -------------------------------------------- | -------------------- |
| Create query job       | `/query/canvas_logs/table/[table_name]/data` | 5 calls per minute   |
| Create pre-signed URLs | `/object/url`                                | 200 calls per minute |

{% hint style="info" %}
These limits are not additive. Reaching a limit for one request type or endpoint does not affect the limits of other types or endpoints. For example, if you reach the limit for GET requests on `/dap/query/canvas/table`, it will not impact your ability to make **POST** requests or **GET** requests on other endpoints.
{% endhint %}

If you anticipate needing higher limits, please reach out to your Customer Success Manager to discuss your requirements.

Learn more details about [Instructure's Canvas API policies](https://www.instructure.com/policies/canvas-api-policy).
