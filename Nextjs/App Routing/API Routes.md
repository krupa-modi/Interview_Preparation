# 🚀 API Routes in Next.js – Complete Interview Guide (VERY IMPORTANT 🔥)

---

# 1. What are API Routes in Next.js?

API Routes allow us to create backend APIs directly inside a Next.js application.

👉 Means:

* No separate Express server needed
* Backend + Frontend in same project

---

# 🔥 Simple Definition

👉 “API Routes are server-side functions that allow Next.js to work like a backend server.”

---

# 2. Why Use API Routes?

Used for:

* Database operations
* Authentication
* Form handling
* CRUD APIs
* Secure server-side logic

---

# 🔥 Example Use Cases

| Use Case          | Example            |
| ----------------- | ------------------ |
| Login API         | `/api/login`       |
| User API          | `/api/users`       |
| Payment API       | Stripe integration |
| Database Fetching | MongoDB queries    |

---

# 3. API Routes in Pages Router (`pages/api`)

In older Next.js routing system:
👉 APIs are created inside:

```bash id="q7m2xt"
pages/api
```

---

# 🔍 Example Folder Structure

```bash id="m3v8qp"
pages/
 ├── api/
 │     ├── users.js
```

---

# 🔍 API Example

```js id="x5m9vr"
export default function handler(req, res) {
  res.status(200).json({
    message: "Hello API"
  });
}
```

---

# 🔥 URL

```text id="w8x2pk"
/api/users
```

---

# 4. How GET / POST Handling Works in pages/api

---

# 🔥 GET Request

```js id="r2v7qm"
export default function handler(req, res) {
  if (req.method === 'GET') {
    res.status(200).json({
      message: "GET Request"
    });
  }
}
```

---

# 🔥 POST Request

```js id="y4m8zt"
export default function handler(req, res) {
  if (req.method === 'POST') {
    const body = req.body;

    res.status(201).json({
      data: body
    });
  }
}
```

---

# 🔥 Important Objects

| Object | Purpose          |
| ------ | ---------------- |
| req    | Incoming request |
| res    | Server response  |

---

# 5. API Routes in App Router (`app/api`) 🔥🔥

In modern Next.js App Router:
👉 APIs are created using:

```bash id="t9x3vp"
app/api
```

with:

```bash id="n6v2qm"
route.js
```

---

# 🔍 Folder Structure

```bash id="j3m8xt"
app/
 ├── api/
 │     ├── users/
 │     │     ├── route.js
```

---

# 🔍 GET Example

```js id="f8x2wr"
export async function GET() {
  return Response.json({
    message: "GET API"
  });
}
```

---

# 🔍 POST Example

```js id="p4m9qt"
export async function POST(req) {
  const body = await req.json();

  return Response.json({
    data: body
  });
}
```

---

# 🔥 URL

```text id="v7x3mp"
/api/users
```

---

# 6. Difference: `pages/api` vs `app/api` 🔥🔥

| Feature          | pages/api    | app/api           |
| ---------------- | ------------ | ----------------- |
| Router Type      | Pages Router | App Router        |
| File             | `users.js`   | `route.js`        |
| Request Handling | req, res     | Request, Response |
| Type             | Old ❌        | Modern ✅          |
| Edge Runtime     | ❌ Limited    | ✅ Supported       |

---

# 🔥 Example Comparison

---

## pages/api

```js id="z5m8qp"
export default function handler(req, res) {
  res.status(200).json({});
}
```

---

## app/api

```js id="u2x7vt"
export async function GET() {
  return Response.json({});
}
```

---

# 7. Dynamic API Routes

---

# 📂 Pages Router

```bash id="q8m4xp"
pages/api/users/[id].js
```

---

# 📂 App Router

```bash id="f3v9qt"
app/api/users/[id]/route.js
```

---

# 🔍 Example

```js id="r7m2vk"
export async function GET(req, { params }) {
  return Response.json({
    id: params.id
  });
}
```

---

# 🔥 URL

```text id="w2x8pm"
/api/users/101
```

---

# 8. Can Next.js Replace Backend? 🔥🔥🔥

## 👉 Short Answer

✅ Yes for many applications.

BUT:
❌ Not always for large enterprise systems.

---

# 🔥 Next.js Can Handle

✅ APIs
✅ Authentication
✅ Database queries
✅ CRUD operations
✅ Server-side logic

---

# 🔥 Example Stack

```text id="p8m3vq"
Frontend → Next.js
Backend → Next.js API Routes
Database → MongoDB
```

👉 Full-stack app possible.

---

# 9. When Next.js Backend is Enough?

| Application      | Suitable? |
| ---------------- | --------- |
| Portfolio        | ✅ Yes     |
| Blog             | ✅ Yes     |
| Admin Panel      | ✅ Yes     |
| SaaS App         | ✅ Yes     |
| Small E-commerce | ✅ Yes     |

---

# 10. When Dedicated Backend Needed?

For:

* Microservices
* Heavy real-time systems
* Complex enterprise architecture
* Large-scale distributed systems

👉 Use:

* Node.js
* NestJS
* Spring Boot
* Django

---

# 11. Advantages of Next.js API Routes

| Advantage          | Explanation                 |
| ------------------ | --------------------------- |
| Full Stack         | Frontend + backend together |
| Easy Setup         | No separate server          |
| Fast Development   | Single codebase             |
| Serverless Support | Easy deployment             |

---

# 12. Limitations of Next.js API Routes

| Limitation                   | Explanation        |
| ---------------------------- | ------------------ |
| Not ideal for huge backends  | Scalability limits |
| Long-running tasks difficult | Serverless timeout |
| Less backend structure       | Compared to NestJS |

---

# 13. Real Interview Questions 🔥

---

## ❓ What are API Routes?

👉 Server-side backend functions inside Next.js.

---

## ❓ Difference between pages/api and app/api?

👉 `pages/api` uses old Pages Router.
👉 `app/api` uses modern App Router with Route Handlers.

---

## ❓ Can Next.js act as full-stack framework?

✅ Yes

---

## ❓ Which is better now?

👉 `app/api` (Route Handlers)

Because:

* Modern
* Better performance
* Edge support

---

# 🎯 Final Interview Answer

👉 API Routes in Next.js allow developers to create backend APIs directly inside the application.

👉 In Pages Router:

```text id="m4x7qt"
pages/api
```

👉 In App Router:

```text id="v9m2xp"
app/api + route.js
```

👉 Next.js can act as a full-stack framework for many applications by handling:

* APIs
* Authentication
* Database operations
* Server-side logic

---

# 💡 MNC Interview Pro Tip

Say this 👇

👉 “Next.js API Routes enable full-stack development by allowing frontend and backend logic inside a single application.” 🚀
