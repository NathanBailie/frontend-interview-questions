<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/protocol.png">
  <h2>Protocols</h2>
</div>
<br />

<details>
<summary><span>1. What is <b>HTTP</b>?</span></summary>
<br />

It is a data transfer protocol used to exchange information between a client (usually a browser) and a server on the internet. It follows a request–response model: the client sends a request, and the server returns a response.

</details>

---

<details>
<summary><span>2. What is the difference between <b>HTTP</b> and <b>HTTPS</b>?</span></summary>
<br />

<b>HTTPS</b> is the secure version of HTTP. It uses encryption via TLS (formerly SSL) to ensure data is transmitted safely: it cannot be intercepted or altered. This protocol is especially important when sending logins, passwords, and other sensitive information.

</details>

---

<details>
<summary><span>3. What is the <b>structure of an HTTP request</b>?</span></summary>
<br />

The structure of an HTTP request includes three main parts:

1. <b>Request Line</b> — indicates the request method (e.g., `GET`, `POST`), the path to the resource, and the protocol version, e.g.:  
   `GET /index.html HTTP/1.1`

2. <b>Headers</b> — key-value parameters that provide additional information, for example:  
   &nbsp;&nbsp;`Host: example.com`  
   &nbsp;&nbsp;`User-Agent: Mozilla/5.0`

3. <b>Body</b> — mainly used in `POST`, `PUT` and similar methods to send data such as JSON, forms, or files.
   <br /><br />

Example:

```
GET /about HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: text/html
```

</details>

---

<details>
<summary><span>4. What <b>HTTP request headers</b> do you know and what are they for?</span></summary>
<br />

Here is a list of common HTTP request headers with brief descriptions:

- **`Host`** — specifies the domain name of the server the request is sent to (required in HTTP/1.1).  
  Example: `Host: example.com`

- **`User-Agent`** — provides information about the client (browser, OS, etc.) sending the request  
  Example: `User-Agent: Mozilla/5.0`

- **`Accept`** — indicates which content types the client can handle  
  Example: `Accept: text/html, application/json`

- **`Content-Type`** — describes the type of data in the request body (important for POST/PUT)  
  Example: `Content-Type: application/json`

- **`Authorization`** — sends credentials (token or basic auth) to access protected resources  
  Example: `Authorization: Bearer <token>`

- **`Accept-Encoding`** — indicates which compression methods the client supports  
  Example: `Accept-Encoding: gzip, deflate`

- **`Referer`** — indicates the URL from which the user came to the current resource  
  Example: `Referer: https://google.com`

- **`Cookie`** — sends cookies stored on the client  
  Example: `Cookie: sessionId=abc123`

- **`Cache-Control`** — controls request caching  
  Example: `Cache-Control: no-cache`

- **`Connection`** — controls connection parameters, such as `keep-alive` or `close`

</details>

---

<details>
<summary><span>5. What can be included in the <b>HTTP request body</b>?</span></summary>
<br />

The HTTP message body can contain various types of data depending on the type of request or response. Common formats include:

- **Form-encoded data** — e.g., `application/x-www-form-urlencoded` or `multipart/form-data` when uploading files
- **JSON** — a popular format for API requests and responses  
  Example: `{ "name": "Anton", "role": "developer" }`
- **XML** — used in some older APIs or specific systems
- **Plain text** — such as text, HTML, or markdown
- **Binary data** — images, video, audio files, etc.
- **Empty body** — e.g., for `GET` and `DELETE` requests, the body is often absent

The content type is specified in the `Content-Type` header so the receiving side knows how to interpret it.

</details>

---

<details>
<summary><span>6. What <b>HTTP request methods</b> do you know?</span></summary>
<br />

Here is a list of common HTTP request methods with brief descriptions:

- **`GET`** — retrieves data from the server
- **`POST`** — sends data to the server
- **`PUT`** — completely replaces an existing resource with the provided data
- **`PATCH`** — partially updates a resource
- **`DELETE`** — deletes the specified resource
- **`HEAD`** — like `GET`, but without the body, returns only headers
- **`OPTIONS`** — asks the server which methods and parameters are allowed for a specific resource
- **`CONNECT`** — establishes a tunnel to the server, typically used for HTTPS proxies
- **`TRACE`** — returns the received request for diagnostic purposes (rarely used, often disabled for security)

</details>

---

<details>
<summary><span>7. What is <b>HEAD</b> used for?</span></summary>
<br />

The `HEAD` method performs the same request as `GET` but without the response body — the server returns only headers. It allows:

- Checking if a resource exists without downloading the content
- Getting the file size (`Content-Length`) before downloading
- Checking if the resource has changed (using `Last-Modified` or `ETag`)
- Debugging, monitoring, or saving bandwidth

</details>

---

<details>
<summary><span>8. What is <b>OPTIONS</b> used for?</span></summary>
<br />

The `OPTIONS` method is used to ask the server which HTTP methods and capabilities are supported for a given resource. It's especially important in the context of CORS (cross-origin requests), where it helps determine whether a request is allowed and which headers/methods are permitted.

Use cases:

- Discover which methods (`GET`, `POST`, `PUT`, etc.) are supported for a resource
- Check allowed headers and origins in cross-origin requests
- Used by browsers for **preflight requests** in CORS to prevent unsafe requests from being sent without approval

</details>

---

<details>
<summary><span>9. What is a <b>preflight request</b>?</span></summary>
<br />

A **preflight request** is a preliminary request that a browser sends using the `OPTIONS` method before performing the actual request (e.g., `POST`, `PUT`) during cross-origin communication (CORS).

The goal is to determine whether the server permits such requests and which headers/methods are allowed.

Example: If `example.com` wants to send a `POST` request to `api.another-site.com` with custom headers or a JSON body, the browser first sends an `OPTIONS` request to check for permission.

</details>

---

<details>
<summary><span>10. What is <b>idempotency</b>?</span></summary>
<br />

It is a property of an HTTP method where repeated execution of the same request does not change the server's state after the first call.

</details>

---

<details>
<summary><span>11. Which HTTP request methods are idempotent?</span></summary>
<br />

- `GET`
- `PUT`
- `DELETE`
- `HEAD`
- `OPTIONS`
- `TRACE`

</details>

---

<details>
<summary><span>12. What <b>status codes</b> do you know?</span></summary>
<br />

HTTP status codes are divided into 5 main groups by the first digit:

### 1xx — **Informational**

- `100 Continue` — the server received the initial headers, and the client can send the body
- `101 Switching Protocols` — the client requested a protocol switch (e.g., to WebSocket), and the server agrees

### 2xx — **Success**

- `200 OK` — standard successful response
- `201 Created` — a new resource was successfully created (e.g., via `POST`)

### 3xx — **Redirection**

- `301 Moved Permanently` — the requested resource has been permanently moved to a new URL
- `302 Found` — temporary redirection (often used for authentication)

### 4xx — **Client Errors**

- `400 Bad Request` — malformed request (e.g., syntax error)
- `404 Not Found` — the resource could not be found at the specified path

### 5xx — **Server Errors**

- `500 Internal Server Error` — an error occurred on the server
- `502 Bad Gateway` — the server received an invalid response from an upstream server

</details>

---

<details>
<summary><span>13. What is the difference between <b>HTTP/1, HTTP/2, and HTTP/3</b>?</span></summary>
<br />

| Characteristic         | HTTP/1.1                            | HTTP/2                                  | HTTP/3                                          |
| ---------------------- | ----------------------------------- | --------------------------------------- | ----------------------------------------------- |
| **Transport Protocol** | TCP                                 | TCP                                     | **QUIC** over UDP                               |
| **Multiplexing**       | ✘ (only one request per connection) | ✔ (multiple requests in one connection) | ✔ (more efficient and no head-of-line blocking) |
| **Header Compression** | ✘                                   | ✔ (HPACK)                               | ✔ (QPACK)                                       |
| **Push Support**       | ✘                                   | ✔ (Server Push)                         | ✔ (with limited use)                            |
| **Loss Resilience**    | ❌ Packet loss blocks others        | ❌ Streams can block due to TCP         | ✔ Streams independent, fast recovery from loss  |
| **Default Encryption** | ✘ (optional, HTTPS over TLS)        | ✘                                       | ✔ (always encrypted, like TLS 1.3)              |
| **Adoption Status**    | Very widely used                    | Widely adopted                          | Growing rapidly                                 |

</details>

---

<details>
<summary><span>14. What is the <b>Host</b> header and why is it required in HTTP/1.1?</span></summary>
<br />

The `Host` header specifies the domain name (and, if needed, the port) of the server the request is sent to.  
Example: `Host: example.com`

It is required in HTTP/1.1 because multiple websites (virtual hosting) can be served from the same IP address, and the server needs to know which one the client is addressing.

Without `Host`, the server may not be able to correctly process the request, especially when handling multiple domains.

</details>

---

<details>
<summary><span>15. What is a <b>MIME</b> type?</span></summary>
<br />

**MIME type** (Multipurpose Internet Mail Extensions) is a designation for the format of transmitted data over the internet. It is specified in the `Content-Type` header and tells the recipient how to interpret the message body.

MIME type format: `type/subtype`, for example:

- `text/html` — HTML document
- `application/json` — JSON data
- `image/png` — PNG image
- `multipart/form-data` — form with files (e.g., for uploads)
- `text/plain` — plain text

</details>

---

<details>
<summary><span>16. What is <b>User-Agent</b>?</span></summary>
<br />

**User-Agent** is an HTTP request header that tells the server information about the client: browser type, operating system, version, device, etc.

Example:  
`User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) Chrome/125.0.0.0`

The server can use this data for content adaptation, logging, or analytics.

</details>

---

<details>
<summary><span>17. What is <b>Content-Type</b>?</span></summary>
<br />

**`Content-Type`** is a header that indicates the format of the request or response body.

Example: `Content-Type: application/json` means that JSON data is being sent.

</details>

---

<details>
<summary><span>18. What is <b>Accept</b>?</span></summary>
<br />

**`Accept`** is a header that tells the server which data formats the client is willing to receive in the response.

Example: `Accept: text/html, application/json` — the client is ready to receive either HTML or JSON.

</details>

---

<details>
<summary><span>19. How does <b>HTTP caching</b> work? Describe <b>Cache-Control</b>, <b>ETag</b>, and <b>Last-Modified</b></span></summary>
<br />

HTTP caching allows the browser to reuse already loaded resources. This speeds up page loading and reduces server load. Here are the key mechanisms:
<br /><br />

### `Cache-Control` — caching strategy management

Specifies whether the resource can be cached and for how long:

- `no-cache` — don’t use cache without rechecking the server
- `max-age=3600` — cache the resource for 3600 seconds (1 hour)  
  <br /><br />

### `ETag` — unique resource identifier

The server returns an `ETag`, which the browser saves. On the next request, the browser sends:

```
If-None-Match: <etag>
```

If the resource hasn't changed — the server responds `304 Not Modified`, and the browser uses the cache.
<br /><br />

### `Last-Modified` — resource last modification date

The server provides the last modified time. Later the browser sends:

```
If-Modified-Since: <date>
```

If unchanged — again `304`.
<br /><br />

These mechanisms **work together**:

- `Cache-Control` dictates caching behavior
- `ETag` and `Last-Modified` validate content freshness

</details>

---

<details>
<summary><span>19. What is <b>WebSocket</b>?</span></summary>
<br />

**WebSocket** is a network protocol that allows a persistent, bidirectional connection between a client and a server.

</details>

---

<details>
<summary><span>20. How does <b>WebSocket</b> differ from <b>HTTP</b>?</span></summary>
<br />

Here’s a table summarizing key differences between HTTP and WebSocket:

| Characteristic            | **HTTP**                               | **WebSocket**                                      |
| ------------------------- | -------------------------------------- | -------------------------------------------------- |
| **Communication model**   | Request → response                     | Persistent bidirectional connection                |
| **Connection durability** | Closed after response                  | Stays open until explicitly closed                 |
| **Data flow direction**   | Only client can initiate               | Both can send data anytime                         |
| **Built on**              | TCP (via HTTP/1.1, HTTP/2)             | TCP (via `Upgrade: websocket`)                     |
| **Overhead**              | Higher — full headers on every request | Lower — continuous stream without repeated headers |
| **Common use cases**      | APIs, pages, forms                     | Chats, notifications, games, real-time data        |

</details>

---

<details>
<summary><span>21. Which <b>ports</b> do <b>HTTP</b>, <b>HTTPS</b>, and <b>WebSocket</b> use?</span></summary>
<br />

Here are the standard ports for these protocols:

| Protocol    | Description                    | Standard Port |
| ----------- | ------------------------------ | ------------- |
| `HTTP`      | Unsecured web protocol         | `80`          |
| `HTTPS`     | HTTP with encryption (TLS/SSL) | `443`         |
| `WebSocket` | Unencrypted (`ws://`)          | `80`          |
| `WebSocket` | Encrypted (`wss://`)           | `443`         |

Note: WebSocket uses the same port as HTTP/HTTPS because the connection starts as a regular HTTP request with the `Upgrade: websocket` header.

</details>

---

<details>
<summary><span>22. Which HTTP header is used to initiate a WebSocket connection?</span></summary>
<br />

To establish a WebSocket connection, the client sends an **HTTP request** with several special headers. The most important ones are:

- **`Upgrade: websocket`** — indicates the client wants to switch from HTTP to WebSocket.
- **`Connection: Upgrade`** — confirms that the `Upgrade` header is applicable for this connection.
- **`Sec-WebSocket-Key`** — a random string used to authenticate the handshake.
- **`Sec-WebSocket-Version`** — the WebSocket protocol version (usually `13`).

Sample request:

```
GET /chat HTTP/1.1
Host: example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
Sec-WebSocket-Version: 13
```

The server then responds with status `101 Switching Protocols`, and a persistent WebSocket connection is established.

</details>

---

<details>
<summary><span>23. What method is used to send data through WebSocket?</span></summary>
<br />

The **`send()`** method is used to send data through a WebSocket.

After establishing the connection (e.g., via `new WebSocket()` in JavaScript), the client can transmit data to the server like this:

```js
const socket = new WebSocket('wss://example.com');
socket.onopen = () => {
	socket.send('Hello, server!');
};
```

The `send()` method can transmit:

- strings (text data),
- binary data (`Blob`, `ArrayBuffer`, etc.).

Important: you should wait for the `onopen` event before calling `send()` to ensure the connection is established.

</details>

---

<details>
<summary><span>24. What method is used to close a WebSocket connection?</span></summary>
<br />

The **`close()`** method is used to close a WebSocket connection.

Example:

```js
const socket = new WebSocket('wss://example.com');

// Closing the connection
socket.close();
```

You can call the `close()` method:

- without arguments — just close the connection,
- with a code and message: `socket.close(1000, "Closing up")`  
  where `1000` is the standard closing code (normal closure), and `"Closing up"` is the optional reason.

After calling `close()`, the `onclose` event is triggered, where you can handle the disconnection.

</details>

---

<details>
<summary><span>25. What data can be sent through WebSocket?</span></summary>
<br />

- **Text strings** — plain text, often in JSON format.
- **JSON objects** — sent as strings (after `JSON.stringify`).
- **ArrayBuffer** — binary data as a byte array.
- **Blob** — for sending files and other binary content (in the browser).
- **TypedArray** — like `Uint8Array`, `Float32Array`, etc.
- **Buffer** — used in Node.js for binary data handling.

</details>

---

<details>
<summary><span>26. What happens if a WebSocket connection is interrupted?</span></summary>
<br />

When a WebSocket connection is interrupted, the **`onclose`** event is automatically triggered on the client.

```js
socket.onclose = event => {
	console.log('Connection closed');
	console.log('Code:', event.code); // e.g., 1000 — normal closure
	console.log('Reason:', event.reason); // Reason, if specified
	console.log('Was clean:', event.wasClean); // true/false
};
```

---

### What you can do when disconnected:

- **Show a notification to the user** — to indicate the connection is lost.
- **Implement reconnection logic** — e.g., with delay or retries.
- **Analyze the close code** — to decide whether to restore the connection (`1000` = normal, `1006` = failure).
- **Clean up associated resources** — stop timers, reset state, hide UI, etc.

</details>

---

<details>
<summary><span>27. What event is used to handle incoming messages in WebSocket?</span></summary>
<br />

The **`onmessage`** event is used to handle incoming messages in a WebSocket.

This event is triggered every time a new message arrives from the server.  
Inside the handler, you can access the data through `event.data`.

### Example:

```js
const socket = new WebSocket('wss://example.com');

socket.onmessage = event => {
	console.log('Message received:', event.data);
};
```

The `event.data` field may contain:

- a string (e.g., JSON),
- binary data (if the server sends `ArrayBuffer` or `Blob`).

</details>

---

<details>
<summary><span>28. What event occurs when a WebSocket connection is successfully established?</span></summary>
<br />

After a WebSocket connection is successfully established with the server, the **`onopen`** event is triggered on the client.

This event indicates that the communication channel is open and ready for data exchange.

### Example:

```js
const socket = new WebSocket('wss://example.com');

socket.onopen = () => {
	console.log('Connection established!');
	socket.send('Hello, server!');
};
```

</details>

---

<details>
<summary><span>29. What WebSocket close code indicates a normal connection termination?</span></summary>
<br />

Code **`1000`** indicates a **normal termination** of a WebSocket connection.

</details>

<!-- <details>
<summary><span></span></summary>
<br />

</details>

--- -->
