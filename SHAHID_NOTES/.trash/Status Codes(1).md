
|Class|Range|Meaning|
|---|---|---|
|1xx|100–199|Informational – Request received, continuing process|
|2xx|200–299|Success – The action was successfully received and processed|
|3xx|300–399|Redirection – Further action must be taken to complete the request|
|4xx|400–499|Client Error – The request contains bad syntax or cannot be fulfilled|
|5xx|500–599|Server Error – Server failed to fulfill an apparently valid request|

## 1xx

| Code                        | Meaning                 | Explanation                                                       |
| --------------------------- | ----------------------- | ----------------------------------------------------------------- |
| **100 Continue**            | Server received headers | Client can proceed to send the body.                              |
| **101 Switching Protocols** | Protocol upgrade        | Client requested a change in protocol (e.g., HTTP to WebSocket).  |
| **102 Processing (WebDAV)** | Server is processing    | The request is still being processed but no response yet.         |
| **103 Early Hints**         | Preload resources       | Suggests client preload resources while server prepares response. |

## 2xx


| Code               | Meaning                            | Explanation                               |
| ------------------ | ---------------------------------- | ----------------------------------------- |
| **200 OK**         | Success                            | Standard success for GET, POST, PUT, etc. |
| **201 Created**    | Resource created                   | Typically returned after POST requests.   |
| **202 Accepted**   | Request accepted but not completed | Useful for async operations.              |
| **204 No Content** | Success, no body                   | Common for DELETE requests.               |


## 4xx

| Code                                  | Meaning                              | Explanation                                |
| ------------------------------------- | ------------------------------------ | ------------------------------------------ |
| **400 Bad Request**                   | Invalid syntax                       | Could be malformed JSON, bad query params. |
| **401 Unauthorized**                  | Auth required                        | Client must authenticate itself.           |
| **403 Forbidden**                     | No permission                        | Valid credentials but access is denied.    |
| **404 Not Found**                     | Resource not found                   | URL doesn't exist on server.               |
| **405 Method Not Allowed**            | HTTP method not supported            | E.g., PUT on a read-only endpoint.         |
| **408 Request Timeout**               | Client took too long to send request |                                            |

## 5xx

| Code                          | Meaning                               | Explanation                            |
| ----------------------------- | ------------------------------------- | -------------------------------------- |
| **500 Internal Server Error** | Generic server error                  | Usually a bug in server code.          |
| **501 Not Implemented**       | Feature not supported                 | E.g., HTTP method not supported.       |
| **502 Bad Gateway**           | Invalid response from upstream server | Server is a gateway and got bad reply. |
