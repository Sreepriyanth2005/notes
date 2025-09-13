
#### Request

```scss
GET /path HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: text/html,application/json
Accept-Language: en-US
Content-Type: application/json
Content-Length: 47
Authorization: Bearer <token>
```

- **Request Line** → `GET /path HTTP/1.1` (method, path, HTTP version)
- **Host** → the domain name (`example.com`)
- **User-Agent** → browser or client details
- **Accept** → what response formats the client accepts
- **Content-Type** → format of the request body (JSON, XML, form-data, etc.)
- **Content-Length** → size of request body
- **Authorization** → credentials (token, API key, etc.)

#### Response

```scss
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 138
Server: Apache/2.4.1 (Unix)
Set-Cookie: sessionId=abc123; HttpOnly
Cache-Control: no-cache
Date: Sun, 31 Aug 2025 12:30:00 GMT
```

- **Status Line** → `HTTP/1.1 200 OK` (version, status code, message)
- **Content-Type** → type of returned data
- **Content-Length** → response body size
- **Server** → server info (Apache, Nginx, Node.js, etc.)
- **Set-Cookie** → to send cookies to client
- **Cache-Control** → caching rules
- **Date** → when the response was generated
