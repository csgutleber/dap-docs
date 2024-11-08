# Status Codes

Responses from the API use HTTP response codes are used to indicate general classes of success and error.

| Status code range | Description                         |   |
| ----------------- | ----------------------------------- | - |
| **`2xx`**         | Successfully processed the request. |   |
| **`4xx`**         | Incorrect or incomplete parameters  |   |
| **`5xx`**         |                                     |   |



* Codes in the **`2xx`** range indicate success.
* Codes in the **`4xx`** range indicate incorrect or incomplete parameters (e.g. a required parameter was omitted, or an operation failed with a 3rd party, etc.).
* Codes in the **`5xx`** range indicate an error with GitBook's servers.

GitBook also outputs an error message and an error code formatted in JSON:

Copy

```
{
    "error": {
        "code": 404,
        "message": "Page not found in this space"
    }
}
```

\
