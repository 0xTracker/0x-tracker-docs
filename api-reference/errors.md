# Errors

0x Tracker uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the `2xx` range indicate success. Codes in the `4xx` range indicate an error that failed given the information provided \(e.g., a required parameter was omitted\). Codes in the `5xx` range indicate an error with 0x Tracker's servers.

| Code | Description |
| :--- | :--- |
| 200 - OK | Everything worked as expected. |
| 400 - Bad Request | The request format was invalid \(e.g. a missing parameter\). |
| 404 - Not Found | The requested endpoint or resource does not exist. |
| 429 - Too Many Requests | The rate limits for the caller's IP address have been exceeded. |
| 500 - Server Error | Something unexpected went wrong. |



