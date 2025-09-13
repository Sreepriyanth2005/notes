
- Node.js is a **runtime environment** that lets you run **JavaScript code outside of a web browser**.
- It uses Google Chrome’s V8 JavaScript engine to run JavaScript fast.
- Node.js uses an **event-driven, non-blocking I/O model**.
- That means it can handle many requests at the same time without waiting for one to finish before starting another
- Comes with **npm (Node Package Manager)**, the world’s largest ecosystem of open-source libraries.

### HTTP (Port 80)

- **HTTP** stands for **HyperText Transfer Protocol**.  
- It’s a **communication protocol** that defines **how data is exchanged between a client (like a web browser or mobile app) and a server** over the internet.

**Characteristics**

- **Stateless** → Each request is independent; server doesn’t “remember” previous requests (cookies/sessions are added later to handle state).
- **Flexible** → Can carry text, images, JSON, video, etc.
- **Simple** → Easy to understand and implement.
- **Extensible** → Supports headers, authentication, caching, compression, etc.

### HTTPS (Port 443)

- HTTPS = **HTTP + SSL/TLS encryption**.
- It’s just the secure version of HTTP.
- It ensures safe communication between **client (browser/app)** and **server** by encrypting the data.

**Characteristics**

- **Encryption** → All data is encrypted using **SSL/TLS**.
- **Authentication** → HTTPS uses **digital certificates (SSL Certificates)** issued by trusted Certificate Authorities (CA).This proves that the server is genuine (not an attacker’s fake site).
- **Performance** → **HTTP/2 and TLS 1.3**, it’s **faster and more efficient**.

### JSON

**JSON (JavaScript Object Notation)** is a lightweight data-interchange format.  
It is mainly used to transfer data between a server and a client in a readable and structured way.

- It’s **text-based** and **language-independent**, but derived from JavaScript object syntax.
- Easy for both **humans to read** and **machines to parse**.

### NPM

- **npm** = **Node Package Manager**
- It is the **default package manager** that comes bundled with Node.js installation.
- It helps developers install, share, and manage **libraries (packages/modules)** needed for a project.

**Package. json**

- The **heart of any Node.js project**.
- It is a JSON file that stores project metadata and dependencies.

```scss
npm init -y
```

**dependencies vs devDependencies**

**devDependencies**:

- Packages needed **only during development** (not required in production).
- Example: testing tools, bundlers, nodemon.

**dependencies**:

- Packages needed **for the app to run in production**.
- Example: `express`, `mongoose`.

