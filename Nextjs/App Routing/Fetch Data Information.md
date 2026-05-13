# App Router in Next.js (New Way 🔥)

## What is App Router?

App Router Next.js 13+ ka new routing system hai.

Ye:

* React Server Components use karta hai
* better performance deta hai
* layouts support karta hai
* easy data fetching provide karta hai

---

# Folder Structure

```bash id="dkgjlwm"
app/
 ├── page.tsx
 ├── about/
 │    └── page.tsx
 └── layout.tsx
```

---

# Important Files

| File        | Purpose    |
| ----------- | ---------- |
| page.tsx    | Route page |
| layout.tsx  | Shared UI  |
| loading.tsx | Loading UI |
| error.tsx   | Error UI   |

---

# Server Components in App Router

By default:

```tsx id="63zup4"
All components are Server Components
```

Means:

* server pe render hote hain
* browser bundle kam hota hai
* performance better hoti hai

---

# Client Component

Agar browser features chahiye:

```tsx id="jzjlwm"
"use client";
```

use karna padta hai.

Example:

```tsx id="epvpxg"
"use client";

import { useState } from "react";
```

---

# How to Fetch Data in Server Components?

App Router mein directly component ke andar fetch kar sakte hain.

No need:

* getServerSideProps
* getStaticProps

---

# Example

```tsx id="g9r1cx"
async function getUsers() {

  const res = await fetch(
    "https://jsonplaceholder.typicode.com/users"
  );

  return res.json();
}

export default async function Page() {

  const users = await getUsers();

  return (
    <div>
      {users.map((user: any) => (
        <p key={user.id}>
          {user.name}
        </p>
      ))}
    </div>
  );
}
```

---

# Important Point

```tsx id="zwjlwm"
page component async ho sakta hai
```

because Server Components async support karte hain.

---

# What are Async Components?

Async Components wo components hain jo:

```tsx id="f9v1yf"
async function
```

use karte hain.

---

# Example

```tsx id="nlmrlj"
export default async function Page() {

  const data = await fetchData();

  return <div>{data.name}</div>;
}
```

---

# Why Useful?

Because:

* directly await use kar sakte
* clean code
* server-side data fetching easy

---

# Important Interview Point

## Client Components async nahi ho sakte

Wrong:

```tsx id="ljjlwm"
"use client";

async function Component() {}
```

Server Components async ho sakte hain.

---

# What is Fetch Caching?

Next.js App Router mein fetch automatically cache hota hai.

Means:

> same data dubara fetch nahi hota unnecessarily.

Performance improve hoti hai.

---

# Default Behavior

```tsx id="l49jwa"
fetch()
```

by default cached hota hai.

---

# Example

```tsx id="zrq4jt"
await fetch("https://api.com/users");
```

Static data cache ho jayega.

---

# Disable Cache

```tsx id="6iq1v2"
await fetch(
  "https://api.com/users",
  {
    cache: "no-store"
  }
);
```

---

# Meaning

```tsx id="jlwm5n"
cache: "no-store"
```

Means:

> har request pe fresh data fetch karo

---

# Fetch Cache Options

| Option      | Meaning           |
| ----------- | ----------------- |
| force-cache | Default cache     |
| no-store    | Always fresh data |

---

# What is Revalidation?

Revalidation ka matlab:

> cached data ko certain time ke baad refresh karna.

ISR (Incremental Static Regeneration) jaisa concept.

---

# Example

```tsx id="q9sltu"
await fetch(
  "https://api.com/users",
  {
    next: {
      revalidate: 60
    }
  }
);
```

---

# Meaning

```tsx id="jlwm0f"
revalidate: 60
```

Means:

* 60 seconds tak cached data
* uske baad fresh fetch

---

# Benefits

* fast performance
* fresh data
* reduced API calls

---

# Real World Example

```tsx id="jlwmc2"
async function getProducts() {

  const res = await fetch(
    "https://api.com/products",
    {
      next: {
        revalidate: 300
      }
    }
  );

  return res.json();
}
```

---

# Important Interview Difference

| Concept    | Meaning                 |
| ---------- | ----------------------- |
| no-store   | Always fresh            |
| revalidate | Refresh after some time |
| cache      | Store fetched data      |

---

# Interview Important Points

| Topic             | Important                     |
| ----------------- | ----------------------------- |
| App Router        | New Next.js routing           |
| Default Component | Server Component              |
| Async Components  | Allowed in server             |
| Data Fetching     | Direct fetch inside component |
| Fetch Caching     | Automatic caching             |
| Revalidation      | Refresh cached data           |

---

# Quick Revision

## Async Server Component

```tsx id="jlwm0r"
export default async function Page() {}
```

---

## No Cache

```tsx id="qg3b4u"
cache: "no-store"
```

---

## Revalidation

```tsx id="jlwm7d"
next: {
  revalidate: 60
}
```

---

# Interview Definition

## App Router

> App Router Next.js 13+ ka new routing system hai jo Server Components aur modern data fetching support karta hai.

---

## Fetch Caching

> Next.js fetched data ko automatically cache karta hai performance improve karne ke liye.

---

## Revalidation

> Revalidation cached data ko fixed time ke baad refresh karta hai.
