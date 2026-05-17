# Server Components in React (Basic Idea)

## What are Server Components?

Server Components are components that render on the server instead of the browser.

They were introduced to improve:
- Performance
- Faster loading
- Smaller bundle size

Server Components send only the final HTML/UI to the client.

# Simple Interview Definition

> Server Components are React components that run on the server and send rendered UI to the client, reducing JavaScript bundle size and improving performance.

---

# Why Use Server Components?

Normally in React:
- All components run in browser
- Large JS bundle gets downloaded

Problem:
- Slower performance

Server Components solve this by:
- Running heavy logic on server
- Sending only required UI

---

# Benefits

- Smaller bundle size
- Faster page load
- Better SEO
- Secure server-side code
- Can directly access database/API

---

# Basic Example

## Server Component

```jsx
async function Users() {
  const res = await fetch("https://api.example.com/users");
  const users = await res.json();

  return (
    <div>
      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))}
    </div>
  );
}

export default Users;
````

---

# How It Works

1. Component runs on server
2. Fetches data on server
3. HTML is generated
4. Browser receives ready UI

Client does less work.

---

# Important Point

## Server Components cannot use:

* useState
* useEffect
* Browser APIs

Because they run on server.

---

# Client Component Example

If interactivity needed:

```jsx
"use client";

import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  );
}
```

---

# Interview Question

## Q: Difference between Server Component and Client Component?

| Server Component   | Client Component       |
| ------------------ | ---------------------- |
| Runs on server     | Runs in browser        |
| Smaller bundle     | Larger bundle          |
| Better performance | Used for interactivity |
| Cannot use hooks   | Can use hooks          |

---

# Short Interview Answer

> Server Components run on the server instead of the browser. They improve performance by reducing JavaScript sent to the client and are mainly used for data fetching and rendering static UI.

---

---

# Suspense for Data Fetching

## What is Suspense?

Suspense allows React to wait for something before rendering UI.

Mostly used for:

* Data fetching
* Lazy loading
* Async operations

While waiting, React shows fallback UI like loading spinner.

---

# Simple Interview Definition

> Suspense lets React pause rendering until async work like data fetching is complete, while showing a fallback loading UI.

---

# Why Suspense Needed?

Without Suspense:

* Manual loading state handling needed

Example:

```jsx
if (loading) return <p>Loading...</p>
```

With Suspense:

* React handles waiting automatically

Cleaner code.

---

# Basic Example

```jsx
import { Suspense } from "react";

function App() {
  return (
    <Suspense fallback={<h2>Loading...</h2>}>
      <Users />
    </Suspense>
  );
}

export default App;
```

---

# Users Component

```jsx
async function Users() {
  const res = await fetch("https://api.example.com/users");
  const users = await res.json();

  return (
    <div>
      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))}
    </div>
  );
}
```

---

# How Suspense Works

1. React starts rendering
2. Data is not ready
3. Suspense shows fallback UI
4. Data arrives
5. Actual component renders

---

# Benefits

* Better user experience
* Cleaner async code
* Easier loading handling
* Works well with Server Components

---

# Important Interview Point

Suspense itself does NOT fetch data.

It only handles waiting/loading UI.

---

# Short Interview Answer

> Suspense in React is used to handle asynchronous rendering. It shows fallback UI while waiting for data or lazy-loaded components, improving user experience and making loading states easier to manage.
