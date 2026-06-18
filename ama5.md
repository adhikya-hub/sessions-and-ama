# AMA

## 1. What is an API?

**API (Application Programming Interface)** is a set of rules that allows two software applications to communicate with each other.

---

## 2. What is REST Framework / REST API?

**REST (Representational State Transfer)** is an architectural style for building web APIs.

REST APIs use:

- HTTP methods
- URLs (endpoints)
- Stateless communication

### REST Constraints

1. **Client-Server** – The client handles the user interface while the server manages data and business logic.

2. **Stateless** – Every request must contain all information needed because the server does not store client state.

3. **Cacheable** – Responses should indicate whether they can be cached to improve performance.

4. **Uniform Interface** – APIs should use consistent resource URLs and standard HTTP methods.

5. **Layered System** – Clients should not know whether they are communicating directly with the server or through intermediaries.

6. **Code on Demand (Optional)** – A server may send executable code, such as JavaScript, to the client.

---

## 3. Difference Between HTTP and HTTPS

| HTTP | HTTPS |
|--------|--------|
| HyperText Transfer Protocol | HyperText Transfer Protocol Secure |
| Data sent in plain text | Data encrypted |
| Less secure | More secure |
| Port 80 | Port 443 |
| No SSL/TLS | Uses SSL/TLS |

### Example

```text
http://example.com
```

Anyone on the network can potentially read the data.

```text
https://example.com
```

Data is encrypted before transmission.

---

## 4. Why Do We Use Memoization?

**Memoization** stores results of expensive function calls so they can be reused.

This avoids recalculating the same result multiple times.

---

## 5. Difference Between `append()` and `appendChild()`

| append() | appendChild() |
|-----------|--------------|
| Can append text and nodes | Can append only nodes |
| Multiple arguments allowed | Only one argument |
| Returns undefined | Returns appended node |
| Modern API | Older API |

### Example

```js
div.append("Hello");
```

Works.

```js
div.appendChild("Hello");
```

Throws error because it's not a node.

```js
const p = document.createElement("p");
div.appendChild(p);
```

Valid.

---

## 6. Can Built-in Array/Object Methods Be Called APIs?

Technically yes, because an API is an interface provided by software.

Examples:

```js
arr.push()
arr.map()
Object.keys()
```

These are part of the JavaScript API.

---

## 7. When Does a Promise Enter the Rejected State?

A Promise becomes rejected when:

- `reject()` is called
- An error is thrown inside the Promise

### Example 1

```js
new Promise((resolve, reject) => {
  reject("Something went wrong");
});
```

### Example 2

```js
new Promise(() => {
  throw new Error("Failed");
});
```

Both become rejected.

### Handling Rejection

```js
promise.catch(err => {
  console.log(err);
});
```

---

## 8. What Is the Use of `Content-Type` in an HTTP Request?

The `Content-Type` header tells the server what type of data is being sent.

### Example

```http
Content-Type: application/json
```

Means JSON data is being sent.

Request body:

```json
{
  "name": "John"
}
```

### Common Content Types

```text
application/json
text/plain
text/html
multipart/form-data
application/x-www-form-urlencoded
```

---

## 9. Does JavaScript Support Multiple Inheritance?

**No.**

A class can extend only one parent class.

### Example

```js
class A {}
class B {}

// Not allowed
class C extends A, B {}
```

### Similar behavior achieved using

Using:

```js
Object.assign(User.prototype, canWalk, canEat);
```

---

## 10. What Is Fetch?

`fetch()` is a browser API used to make HTTP requests.

### Example

```js
fetch("/users")
  .then(res => res.json())
  .then(data => console.log(data));
```

Returns a Promise.

- Calling APIs
- Sending form data
- Retrieving server data

---

## 11. What Is the Role of Postman?

Postman is an API testing tool.

It allows developers to:

- Send HTTP requests
- Test APIs
- Inspect responses
- Debug backend services

### Example

Instead of writing:

```js
fetch("/users");
```

You can manually send:

```http
GET /users
```

from Postman and inspect:

- Status code
- Headers
- Response body
- Response time

### Benefits

- Faster API testing
- No frontend needed
- Easy debugging

---

## 12. What Is a Cookie?

A cookie is a small piece of data stored by the browser.

Used for:

- Authentication
- Session management
- User preferences
- Tracking

### Example

After login:

```text
sessionId=abc123
```

may be stored as a cookie.

The browser automatically sends it with future requests.

---

## 13. If We Login on a Website and Open Another Tab, How Does the Website Know We Are Logged In?

Because login information is stored in:

- Cookies
- Session storage
- Local storage
- Authentication tokens

Most commonly, cookies.

### Flow

1. User logs in.
2. Server sends a session cookie.

```text
sessionId=abc123
```

3. Browser stores it.
4. New tab shares the same cookies.
5. Browser automatically sends the cookie.

```http
Cookie: sessionId=abc123
```

6. Server recognizes the session and knows the user is logged in.

Tabs share cookies for the same website.

Therefore login remains active across tabs.

---

## 14. What Is a Header in an HTTP Request?

Headers contain metadata about the request.

They provide additional information to the server.

### Example

```http
GET /users HTTP/1.1
Host: example.com
Content-Type: application/json
Authorization: Bearer token123
```

### Common Headers

#### Content-Type

```http
Content-Type: application/json
```

Type of data being sent.

#### Authorization

```http
Authorization: Bearer token123
```

Authentication information.

#### Accept

```http
Accept: application/json
```

Expected response format.

#### Cookie

```http
Cookie: sessionId=abc123
```

Session information.
