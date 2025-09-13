- **Express.js** is a **web framework for Node.js**.
- It sits on top of Node’s built-in `http` module and makes it **much easier** to:
    - Create servers
    - Handle routes
    - Manage requests & responses
    - Work with middleware (logging, authentication, parsing, etc.)

### Routing

| Method     | Purpose                        |
| ---------- | ------------------------------ |
| **GET**    | Retrieve data                  |
| **POST**   | Create new data                |
| **PUT**    | Update existing data (replace) |
| **DELETE** | Remove data                    |

|Method|Purpose|
|---|---|
|**PATCH**|Partial update of a resource (modify some fields only).|
|**HEAD**|Same as GET but returns headers only (no body).|
|**OPTIONS**|Shows supported HTTP methods (used in CORS & API discovery).|

### Middleware

- In Express.js, **middleware** = functions that run **between the request and response**.
    
- They can:
    1. Modify the `req` and `res` objects.
    2. Execute code.
    3. End the request-response cycle.
    4. Or pass control to the next middleware using `next()`.

**Body Parser**

- Parses the **body of incoming requests** (JSON, form data, etc.).
- Without this, `req.body` would be `undefined`.

```js
app.use(express.json()); // For JSON
app.use(express.urlencoded({ extended: true })); // For form data
```

**Cross Origin Resource Sharing**

- Controls which domains can access your API.
- By default, browsers **block cross-origin requests** for security.
- `cors` middleware lets you open or restrict access.

```js
app.use(cors()); // allow all origins
app.use(cors({origin: 'http://example.com'}));
```

**Logger(Morgan)

- Logs requests (method, URL, response time).
- Useful for debugging and monitoring.
- Morgan is a **HTTP request logger middleware** for Node.js/Express

```js
//custom Logging
app.use(morgan(':method :url :status :res[content-length] - :response-time ms'));
```

**Error Handler**

Error-handling middleware is a **special type of middleware** that catches errors occurring in your application

```js
app.use((err, req, res, next) => {
  console.error(err.stack);  // logs error
  res.status(500).json({ error: "Something went wrong!" });
});
```
### Static files serving

**Static files are assets that don’t change dynamically on the server side**

```js
app.use(express.static(path.join(__dirname, 'public')));
```

