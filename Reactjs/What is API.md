# ✅ What is API in JavaScript/Web Development?

# 🎯 Definition

API stands for:

```txt
Application Programming Interface
````

API is a way for two applications/systems to communicate with each other.

---

# ✅ Simple Real-Life Example

Suppose:

* You use a food app
* App sends request to restaurant server
* Server sends food data back

👉 This communication happens using APIs.

---

# ✅ In Web Development

Frontend and backend communicate using APIs.

```txt
Frontend → API → Backend/Database
```

---

# ✅ Example

```js
fetch("https://api.example.com/users")
  .then(res => res.json())
  .then(data => console.log(data));
```

---

# 🔍 What Happens?

1. Request goes to server
2. Server sends data
3. Frontend uses data

---

# ✅ API Response Example

```json
{
  "name": "Aman",
  "age": 25
}
```

Mostly APIs return:

```txt
JSON data
```

---

# ✅ Types of APIs

| Type        | Purpose                |
| ----------- | ---------------------- |
| REST API    | Most common web API    |
| SOAP API    | XML-based API          |
| GraphQL API | Flexible data fetching |

---

# ✅ Common HTTP Methods

| Method | Purpose     |
| ------ | ----------- |
| GET    | Fetch data  |
| POST   | Send data   |
| PUT    | Update data |
| DELETE | Delete data |

---

# ✅ Interview Definition

> API is a medium that allows different applications to communicate and exchange data.

---

# ✅ Real Use Cases

✅ Login system
✅ Weather app
✅ Payment gateway
✅ Social media feed

---

# 🚀 Quick Revision

| Concept        | Meaning              |
| -------------- | -------------------- |
| API            | Communication bridge |
| Mostly Returns | JSON                 |
| Used Between   | Frontend & Backend   |

---

# 💡 One-Line Memory Trick

```txt
API = Messenger between frontend and backend
```
