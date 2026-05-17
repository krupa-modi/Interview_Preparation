# Next.js Important Concepts (Easy Interview Notes)

# 1. SSR (Server Side Rendering)

## Definition

Page renders on the server on every request.

Fresh data comes every time.

---

## Use Case

* Dashboard
* Live data
* User profile
* Stock market data

---

## Easy Example

```js id="2j32q0"
// pages/users.js

export async function getServerSideProps() {
  const res = await fetch(
    "https://jsonplaceholder.typicode.com/users"
  );

  const users = await res.json();

  return {
    props: { users }
  };
}

export default function Users({ users }) {
  return (
    <div>
      {users.map((u) => (
        <h2 key={u.id}>{u.name}</h2>
      ))}
    </div>
  );
}
```

---

## Interview Line

> “SSR generates HTML on every request, so users always get fresh data.”

---

# 2. SSG (Static Site Generation)

## Definition

Page is generated once at build time.

Very fast performance.

---

## Use Case

* Blog
* Documentation
* Static pages

---

## Easy Example

```js id="gwddjh"
// pages/blog.js

export async function getStaticProps() {
  const res = await fetch(
    "https://jsonplaceholder.typicode.com/posts"
  );

  const posts = await res.json();

  return {
    props: { posts }
  };
}

export default function Blog({ posts }) {
  return (
    <div>
      {posts.map((p) => (
        <h2 key={p.id}>{p.title}</h2>
      ))}
    </div>
  );
}
```

---

## Interview Line

> “SSG creates pages during build time, which improves speed and SEO.”

---

# 3. ISR (Incremental Static Regeneration)

## Definition

Static page updates automatically after some time.

Combination of SSG + fresh data.

---

## Use Case

* Ecommerce product page
* News website
* Frequently updated blog

---

## Easy Example

```js id="kdn95z"
// pages/products.js

export async function getStaticProps() {
  const res = await fetch(
    "https://jsonplaceholder.typicode.com/posts"
  );

  const products = await res.json();

  return {
    props: { products },
    revalidate: 10
  };
}

export default function Products({ products }) {
  return (
    <div>
      {products.map((p) => (
        <h2 key={p.id}>{p.title}</h2>
      ))}
    </div>
  );
}
```

---

## Meaning

```js id="t6wxxe"
revalidate: 10
```

Page regenerates every 10 seconds.

---

## Interview Line

> “ISR allows static pages to update automatically without rebuilding the entire application.”

---

# 4. Middleware

## Definition

Middleware runs before request completes.

Used for:

* Authentication
* Redirects
* Route protection

---

## Easy Example

```js id="7fc7su"
// middleware.js

import { NextResponse } from "next/server";

export function middleware(req) {
  const isLoggedIn = false;

  if (!isLoggedIn) {
    return NextResponse.redirect(
      new URL("/login", req.url)
    );
  }
}
```

---

## What Happens?

If user is not logged in:

```bash id="1g1vb5"
/dashboard
```

Redirects to:

```bash id="8ks0h4"
/login
```

---

## Interview Line

> “Middleware is used to intercept requests before rendering pages, mainly for authentication and redirects.”

---

# 5. GET API Example

## Definition

GET method fetches data.

---

## Easy Example

```js id="jjnt1m"
// app/api/users/route.js

export async function GET() {
  return Response.json({
    message: "Users fetched successfully"
  });
}
```

---

## URL

```bash id="pq9d1z"
/api/users
```

---

## Interview Line

> “GET method is used to retrieve data from the server.”

---

# 6. POST API Example

## Definition

POST method sends data to server.

---

## Easy Example

```js id="8f2d9u"
// app/api/users/route.js

export async function POST(req) {
  const body = await req.json();

  return Response.json({
    message: "User added",
    data: body
  });
}
```

---

## Example Request Body

```json id="e3bq1m"
{
  "name": "Krupa"
}
```

---

## Response

```json id="qgf5zv"
{
  "message": "User added",
  "data": {
    "name": "Krupa"
  }
}
```

---

## Interview Line

> “POST method is used to send or create data on the server.”

---

# Most Important Difference Table

| Concept | When Generated | Best For           |
| ------- | -------------- | ------------------ |
| SSR     | Every request  | Dynamic data       |
| SSG     | Build time     | Static pages       |
| ISR     | After interval | Semi-dynamic pages |

---

# Quick Revision (Very Important)

| Topic      | One-Line Answer                   |
| ---------- | --------------------------------- |
| SSR        | Server renders page every request |
| SSG        | Page generated at build time      |
| ISR        | Static page auto-updates          |
| Middleware | Runs before request               |
| GET        | Fetch data                        |
| POST       | Send/create data                  |

---

# Best Final Interview Answer

## Q: Difference between SSR, SSG, and ISR?

### Answer

> “SSR generates pages on every request for fresh data, SSG generates pages during build time for better performance, and ISR updates static pages automatically after a specific interval.”
