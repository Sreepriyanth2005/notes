

## JWT

- **JWT** = JSON Web Token
- It is a **compact, URL-safe token** used to **transfer claims** between a client and a server.
- Commonly used for **authentication and authorization** in web apps, APIs, and mobile apps.
- Stateless → the server does not need to store session info.

#### Structure of JWT

```scss
<Header>.<Payload>.<Signature>
```

```scss
//Example

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
.
eyJ1c2VySWQiOjEyMywiZW1haWwiOiJleGFtcGxlQG1haWwuY29tIiwiaWF0IjoxNjg1MjYwMDAwfQ
.
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c

```

**1. Header**

- Metadata about the token: **type** and **algorithm**.
- Usually JSON, then Base64URL encoded.

```json
{
  "alg": "HS256",   // HMAC SHA-256
  "typ": "JWT"      // Type: JWT
}
```

**2 . Payload**

Contains the **claims** → statements about the user or token.

- **Registered claims** (standard, optional):
    - `iss` → issuer
    - `sub` → subject
    - `aud` → audience
    - `exp` → expiration time
    - `iat` → issued at
    
- **Public claims** → defined by you (e.g., `userId`, `role`)
- **Private claims** → custom application-specific info

```json
{
  "userId": 123,
  "email": "example@mail.com",
  "role": "admin",
  "iat": 1685260000,
  "exp": 1685263600
}
```

**3. Signature**

- Ensures the token was **not tampered**.
- Server verifies the signature when receiving the token.

```json
HMACSHA256(
  base64UrlEncode(header) + "." + base64UrlEncode(payload),
  secretKey
)
```

## Password Hashing(bcrypt)

- Never store passwords as plain text!
- Use **bcrypt** to hash passwords before saving in DB.
- When user logs in, **compare hashed password**.

```js
const bcrypt = require("bcrypt");
const hashed = await bcrypt.hash("mypassword", 10); // hash password
const isValid = await bcrypt.compare("mypassword", hashed); // verify
```

**hash()**

```js
bcrypt.hash(plainPassword, saltRounds);
// Example output: $2b$10$EixZaYVK1fsbw1ZfbX3OXePaWxn96p36KZ5g8i4U3f5h2K1a6qC2
```

**`saltRounds`** → number of iterations to make hashing slower (more secure).

**Format**

```scss
$2b$10$EixZaYVK1fsbw1ZfbX3OXePaWxn96p36KZ5g8i4U3f5h2K1a6qC2
|  |  |
|  |  +--- 53 character hash + salt (Base64 encoded)
|  +------ cost factor (salt rounds = 10)
+--------- algorithm identifier (2b = bcrypt)
```

**Compare()**

- `bcrypt.compare()` does **not decrypt the hash** — it **re-hashes the input password** and checks for equality.

- Then it simply checks if the hashes match → no decryption is involved.


