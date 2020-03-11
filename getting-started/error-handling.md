# Errors

Whether an API request to Uiza is successful or not is indicated by conventional _HTTP_ codes. In general, Uiza returns responses with equivalent _status codes_ which are listed below.

> **200 - OK**
>
> The request is successful.

> **400 - Bad request**
>
> The request is inadequate. This is usually caused by missing required parameters or malformed syntax.

> **401 - Unauthorized**
>
> No valid API key is provided.

> **403 - Forbidden**
>
> The API key doesn't have permissions to perform the request.

> **404 - Not found**
>
> The requested resource doesn’t exist.

> **409 - Conflict**
>
> The request conflicts with another request.

> **500, 502, 503, 504 - Server Errors**
>
> Something went wrong from Uiza’s end.

Errors are returned in the format which contains a `message` and an `error_type` to help you pinpoint what went wrong. While you can find all the possible error messages in our API Reference, these errors are categorized by the following `error_types`:

| Error Types | Definitions |
| :---: | :---: |
| `api_connection_error` | Errors that occurred during the HTTP communication. |
| `api_error` | Errors occurred internally with Uiza API. |
| `authentication_error` | The keys supplied to Uiza were either missing or invalid. |
| `invalid_request_error` | The parameters supplied to Uiza were either missing or invalid. |
| `rate_limit_error` | Too many requests were sent to Uiza too quickly. |
| `video_error` | There is something wrong with your video or live stream. |

