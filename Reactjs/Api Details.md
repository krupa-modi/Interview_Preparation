# API Complete Interview Notes 🚀

---

# 📌 What is API?

API = **Application Programming Interface**

API frontend aur backend ke beech communication karne ke liye use hoti hai.

Example:

```txt id="qz70rb"
React Frontend ↔ Backend API ↔ Database
```

---

# 🔥 HTTP Methods (Very Important)

| Method | Use             | Example         |
| ------ | --------------- | --------------- |
| GET    | Data fetch      | Get users       |
| POST   | New data create | Register user   |
| PUT    | Full update     | Update profile  |
| PATCH  | Partial update  | Update username |
| DELETE | Remove data     | Delete user     |

---

# 📌 GET Method

## ✅ Use

Server se data fetch karna.

## ✅ Example

```js id="3z95u7"
fetch("/users");
```

---

# 📌 POST Method

## ✅ Use

New data send/create karna.

## ✅ Example

```js id="jrx4u7"
fetch("/users", {
  method: "POST",
  body: JSON.stringify(data),
});
```

---

# 📌 PUT Method

## ✅ Use

Pure resource ko update karta hai.

---

# 📌 PATCH Method

## ✅ Use

Sirf specific field update karta hai.

---

# 📌 DELETE Method

## ✅ Use

Data remove karta hai.

---

# 🔥 Important Status Codes

| Status Code | Meaning      |
| ----------- | ------------ |
| 200         | Success      |
| 201         | Created      |
| 204         | No content   |
| 400         | Bad request  |
| 401         | Unauthorized |
| 403         | Forbidden    |
| 404         | Not found    |
| 500         | Server error |

---

# 📌 Status Code Explanation

## ✅ 200

Request successful.

---

## ✅ 201

New resource created.

Mostly POST request.

---

## ✅ 401

Authentication missing.

Token invalid ho sakta hai.

---

## ✅ 403

User authenticated hai but permission nahi hai.

---

## ✅ 404

API/resource nahi mila.

---

## ✅ 500

Backend/server crash.

---

# 🔥 JSON Methods

# 📌 JSON.stringify()

## ✅ Use

JavaScript object → JSON string convert.

---

## ✅ Example

```js id="ofqeq8"
const user = {
  name: "John",
};

JSON.stringify(user);
```

## ✅ Output

```js id="x10bzi"
'{"name":"John"}'
```

---

# 📌 JSON.parse()

## ✅ Use

JSON string → JavaScript object convert.

---

## ✅ Example

```js id="8ffk3x"
const jsonData =
  '{"id":1,"name":"John","age":25}';

const user = JSON.parse(jsonData);

console.log(user);
```
## ✅ Output

```js id="x10bzi"
{
  id: 1,
  name: "John",
  age: 25
}
```
# JSON.parse() and JSON.stringify() with Dummy Data 🚀

---

# 📌 JSON.stringify()

## ✅ Use

JavaScript Object → JSON String convert karta hai.

---

# ✅ Syntax

```js id="h0g02q"
JSON.stringify(value);
```

---

# ✅ Dummy Data Example

```js id="e6s0j4"
const user = {
  id: 1,
  name: "John",
  age: 25,
  city: "Pune",
};

const jsonData = JSON.stringify(user);

console.log(jsonData);
```

---

# ✅ Output

```js id="1zd0vp"
'{"id":1,"name":"John","age":25,"city":"Pune"}'
```

---

# 📌 Why Use stringify()?

API ko data bhejne ke liye.

Backend mostly JSON string accept karta hai.

---

# ✅ API Example

```js id="7z8fgx"
const user = {
  name: "John",
  email: "john@gmail.com",
};

fetch("/users", {
  method: "POST",

  headers: {
    "Content-Type": "application/json",
  },

  body: JSON.stringify(user),
});
```

---

# 📌 JSON.parse()

## ✅ Use

JSON String → JavaScript Object convert karta hai.

---

# ✅ Syntax

```js id="4e61j4"
JSON.parse(value);
```

---

# ✅ Dummy Data Example

```js id="h3ns4q"
const jsonData =
  '{"id":1,"name":"John","age":25}';

const user = JSON.parse(jsonData);

console.log(user);
```

---

# ✅ Output

```js id="9dq5vf"
{
  id: 1,
  name: "John",
  age: 25
}
```

---

# 📌 Why Use parse()?

Backend/API se jo data aata hai usko JavaScript object me convert karne ke liye.

---

# ✅ API Response Example

```js id="w3s0ta"
const response = await fetch("/users");

const data = await response.json();

console.log(data);
```

---

# 🔥 Behind the Scene

```js id="pnatc5"
response.json()
```

internally JSON.parse jaisa kaam karta hai.

---

# 📌 Easy Difference

| JSON.stringify()     | JSON.parse()         |
| -------------------- | -------------------- |
| Object → JSON String | JSON String → Object |

---

# 🧠 Easy Memory Trick

| Function  | Meaning                |
| --------- | ---------------------- |
| stringify | Convert to string      |
| parse     | Convert back to object |

---
> “JSON.stringify() JavaScript object ko JSON string me convert karta hai, mostly API request bhejne ke liye. JSON.parse() JSON string ko JavaScript object me convert karta hai, mostly API response read karne ke liye.”

---

# 🔥 Why stringify important in API?

Backend mostly JSON format me data accept karta hai.

---

# 📌 API Headers (Very Important)

Headers extra information bhejte hain.

---

# ✅ Common Headers

| Header        | Use                    |
| ------------- | ---------------------- |
| Content-Type  | Data type batata hai   |
| Authorization | Token bhejne ke liye   |
| Accept        | Expected response type |

---

# 🔥 Content-Type

## ✅ JSON Data

```js id="rnvqk3"
headers: {
  "Content-Type": "application/json"
}
```

---

# 🔥 Authorization Header

## ✅ Bearer Token

```js id="4duz6d"
headers: {
  Authorization: "Bearer TOKEN"
}
```

---

# 📌 What is Bearer Token?

Authentication token hota hai.

Mostly JWT token use hota hai.

---

# 🔥 Full API Boilerplate (Most Important)

```js id="0eg4wj"
async function getUsers() {
  try {
    const response = await fetch(
      "https://api.com/users",
      {
        method: "GET",

        headers: {
          "Content-Type":
            "application/json",

          Authorization:
            "Bearer token_here",
        },
      }
    );

    if (!response.ok) {
      throw new Error("API Failed");
    }

    const data = await response.json();

    console.log(data);
  } catch (error) {
    console.log(error);
  }
}
```

---

# 📌 response.json()

## ✅ Use

JSON response ko JavaScript object me convert karta hai.

---

## ✅ Example

```js id="r6mqyi"
const data = await response.json();
```

---

# 🔥 async/await in API

## ✅ async

Function asynchronous banata hai.

---

## ✅ await

Promise resolve hone ka wait karta hai.

---

# 📌 Why try-catch?

API failure handle karne ke liye.

---

# 🔥 Fetch vs Axios

| Fetch               | Axios            |
| ------------------- | ---------------- |
| Built-in            | External library |
| Manual JSON parsing | Automatic        |
| Less features       | More features    |

---

# 📌 Axios Example

```js id="48sj4l"
import axios from "axios";

const response = await axios.get("/users");

console.log(response.data);
```

---

# 🔥 Query Parameters

## ✅ Example

```txt id="x6wsdy"
/users?page=1
```

---

# 📌 Path Parameters

## ✅ Example

```txt id="dxf7qm"
/users/10
```

---

# 🔥 REST API

REST API HTTP methods use karti hai.

---

# 📌 CRUD Operations

| Operation | Method    |
| --------- | --------- |
| Create    | POST      |
| Read      | GET       |
| Update    | PUT/PATCH |
| Delete    | DELETE    |

---

# 🔥 API Lifecycle

```txt id="imn2ln"
Frontend Request
       ↓
Backend API
       ↓
Database
       ↓
Response
       ↓
Frontend UI
```

---

# 📌 Important Interview Questions

# ❓ Difference between PUT and PATCH?

| PUT         | PATCH          |
| ----------- | -------------- |
| Full update | Partial update |

---

# ❓ Difference between Authentication and Authorization?

| Authentication | Authorization        |
| -------------- | -------------------- |
| Who are you?   | What can you access? |

---

# ❓ Why use Bearer token?

Secure authentication ke liye.

---

# ❓ Why use async-await?

Readable asynchronous code.

---

# ❓ Difference between JSON.parse and JSON.stringify?

| parse         | stringify     |
| ------------- | ------------- |
| JSON → Object | Object → JSON |

---

# 🎯 Final Interview Answer

> “API frontend aur backend ke beech communication ka medium hoti hai. APIs mostly HTTP methods like GET, POST, PUT, PATCH, DELETE use karti hain. Data generally JSON format me send hota hai and headers authentication aur content type define karte hain.”
