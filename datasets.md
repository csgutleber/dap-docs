---
description: Everything about namespaces, tables, and schemas.
---

# Datasets

Data replication in Data Access Platform (DAP) is based on **tables**. You can synchronize the state of each table individually with the data stored in DAP.

Tables are organized into **namespaces**. For example, the Canvas tables assignments, content\_tags or submissions are in the namespace canvas. The table web\_logs is in the namespace canvas\_logs. Other products have their own namespace, e.g. catalog.

{% hint style="info" %}
**Disclaimer:** The data available currently is a ‘best effort’ attempt, and is not guaranteed to be complete or wholly accurate.
{% endhint %}

### All available namespaces <a href="#all-available-namespaces" id="all-available-namespaces"></a>

| Namespace                                                                                                                          | Description                     |
| ---------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| [`canvas`](https://github.com/instructure/api-docu-portal/blob/test/gitbook/services/dap/canvas.md#tables-in-canvas)               | Tables from Canvas              |
| [`canvas_logs`](https://github.com/instructure/api-docu-portal/blob/test/gitbook/services/dap/canvaslogs.md#tables-in-canvas-logs) | Tables representing access logs |
| [`catalog`](https://github.com/instructure/api-docu-portal/blob/test/gitbook/services/dap/catalog.md#tables-in-catalog)            | Tables from Canvas Catalog      |

{% hint style="info" %}
Please note that access to the data in the `catalog` namespace requires a separate purchase of [Canvas Catalog](https://community.canvaslms.com/t5/Canvas-Catalog/What-is-Canvas-Catalog/ta-p/1764).[\
](https://inst.gitbook.io/test-instructure-api-documentation-portal/itrTPCOhkudBF8CjNrin/services/dap/limits-policies)
{% endhint %}
