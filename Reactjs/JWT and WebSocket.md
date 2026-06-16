## What is JWT?

JWT (JSON Web Token) is a secure way to transfer data between client and server.

Mostly used for:
Authentication
Authorization
Secure API communication

Example:
After login, server gives a token.
Frontend stores token and sends it in every request.

After user login:

* Server gives token
* Frontend stores token
* Frontend sends token with API requests

---

# JWT Flow (Frontend)

```text id="1"
1. User Login
2. Frontend sends email/password
3. Backend returns JWT token
4. Frontend stores token
5. Token sent in protected API requests
```

---

# JWT Structure

JWT has 3 parts:

```text id="2"
Header.Payload.Signature
```

Example:

```text id="3"
abc.xyz.123
```

---

# Store JWT Token

## Local Storage

```js id="4"
localStorage.setItem("token", token)
```

Get token:

```js id="5"
const token = localStorage.getItem("token")
```

Remove token:

```js id="6"
localStorage.removeItem("token")
```

---

# Send JWT in API

```js id="7"
fetch("https://api.com/user", {
  headers: {
    Authorization: `Bearer ${token}`
  }
})
```

---

# Axios Example

```js id="8"
axios.get("/profile", {
  headers: {
    Authorization: `Bearer ${token}`
  }
})
```

---

# Protected Route Example (React)

```jsx id="9"
{
  token ? <Home /> : <Login />
}
```

---

# JWT Advantages

* Secure authentication
* Stateless
* Easy to use
* Works with React apps

---

# JWT Disadvantages

* Token can expire
* If token stolen → security issue

---

# JWT Interview Questions

## What is JWT?

JWT is a token used for authentication.

---

## Why JWT used?

Used to identify logged-in users.

---

## Where token stored?

Mostly:

* Local Storage
* Cookies

---

## What is Bearer Token?

```text id="10"
Authorization: Bearer token_here
```

---

## What happens after token expires?

User needs to login again or refresh token.

---

# WebSocket (Frontend Interview Notes)

## What is WebSocket?

WebSocket is used for real-time communication.

Client and server can send messages continuously.

---

# Where WebSocket Used?

* Chat apps
* Notifications
* Live updates
* Online games

---

# HTTP vs WebSocket

| HTTP              | WebSocket             |
| ----------------- | --------------------- |
| Request-response  | Two-way communication |
| Connection closes | Connection stays open |

---

# WebSocket Flow

```text id="11"
1. Frontend connects to server
2. Connection stays open
3. Messages sent anytime
```

---

# Create WebSocket Connection

```js id="12"
const socket = new WebSocket("ws://localhost:3000")
```

---

# WebSocket Events

## onopen

```js id="13"
socket.onopen = () => {
  console.log("Connected")
}
```

---

## send message

```js id="14"
socket.send("Hello")
```

---

## receive message

```js id="15"
socket.onmessage = (event) => {
  console.log(event.data)
}
```

---

## close connection

```js id="16"
socket.onclose = () => {
  console.log("Disconnected")
}
```

---

# Full Example

```js id="17"
const socket = new WebSocket("ws://localhost:3000")

socket.onopen = () => {
  console.log("Connected")

  socket.send("Hello Server")
}

socket.onmessage = (event) => {
  console.log(event.data)
}

socket.onclose = () => {
  console.log("Connection Closed")
}
```

---

# Advantages of WebSocket

* Real-time communication
* Fast
* Live updates

---

# Disadvantages of WebSocket

* More complex
* Connection handling needed

---

# Polling vs WebSocket

| Polling           | WebSocket         |
| ----------------- | ----------------- |
| Repeated requests | Single connection |
| Slower            | Faster            |

---

# WebSocket Interview Questions

## What is WebSocket?

WebSocket is a protocol for real-time communication.

---

## Why WebSocket used?

Used for instant live updates.

---

## What is real-time communication?

Data updates instantly without page refresh.

---

## What is full duplex communication?

Both client and server send messages simultaneously.

---

# Real Project Usage

## JWT

* Login authentication
* Protected pages
* User sessions

---

## WebSocket

* Chat system
* Live notification
* Live tracking
* Real-time dashboard
