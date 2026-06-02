
# Task 1 — Search with Debounce

# What is Debounce?

Debounce ka matlab hota hai:

> User typing complete hone ke baad hi API call karna.

Agar user continuously type kar raha hai to unnecessary API calls avoid hoti hain.

---

# Why Use Debounce?

Without debounce:

```text id="7pv2dj"
h → API
he → API
hel → API
hell → API
hello → API
```

Too many API calls ❌

---

# With Debounce

```text id="x1jw8y"
User typing...
Wait 500ms
Then API Call
```

Only one API call ✅

---

# Interview Use Cases

* Search Bar
* Product Search
* Auto Suggestions
* Filtering
* Global Search

---

# Next.js Practical Example

## File Structure

```text id="pmylc8"
app/
 └── search/
      └── page.js
```

---

# Code

```jsx id="z5imfy"
"use client";

import { useEffect, useState } from "react";

export default function SearchPage() {
  const [query, setQuery] = useState("");
  const [debouncedQuery, setDebouncedQuery] = useState("");

  // Debounce Logic
  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedQuery(query);
    }, 500);

    return () => clearTimeout(timer);
  }, [query]);

  // API Call
  useEffect(() => {
    if (debouncedQuery) {
      fetchData();
    }
  }, [debouncedQuery]);

  const fetchData = async () => {
    console.log("API Call:", debouncedQuery);

    const res = await fetch(
      `https://jsonplaceholder.typicode.com/users`
    );

    const data = await res.json();

    console.log(data);
  };

  return (
    <div>
      <h1>Search with Debounce</h1>

      <input
        type="text"
        placeholder="Search..."
        value={query}
        onChange={(e) => setQuery(e.target.value)}
      />
    </div>
  );
}
```

---

# Important Interview Points

* Performance optimization
* Reduces API calls
* Better UX
* Used in search inputs

---

# Task 2 — Pagination

# What is Pagination?

Large data ko small pages me divide karna.

Example:

```text id="0ljxg7"
Page 1
Page 2
Page 3
```

---

# Why Use Pagination?

* Faster loading
* Better performance
* Better UX
* Server load kam

---

# Interview Use Cases

* Product listing
* User table
* Blogs
* Admin dashboard

---

# Next.js Pagination Example

## File Structure

```text id="fy3x0z"
app/
 └── pagination/
      └── page.js
```

---

# Code

```jsx id="32xpjm"
"use client";

import { useEffect, useState } from "react";

export default function PaginationPage() {
  const [users, setUsers] = useState([]);
  const [page, setPage] = useState(1);

  useEffect(() => {
    fetchUsers();
  }, [page]);

  const fetchUsers = async () => {
    const res = await fetch(
      `https://jsonplaceholder.typicode.com/posts?_limit=5&_page=${page}`
    );

    const data = await res.json();

    setUsers(data);
  };

  return (
    <div>
      <h1>Pagination Example</h1>

      {users.map((user) => (
        <p key={user.id}>{user.title}</p>
      ))}

      <button onClick={() => setPage(page - 1)}>
        Prev
      </button>

      <span> Page {page} </span>

      <button onClick={() => setPage(page + 1)}>
        Next
      </button>
    </div>
  );
}
```

---

# Interview Points

* Pagination improves performance
* Avoids large rendering
* Server-side pagination possible
* Infinite scroll alternative

---

# Task 3 — Protected Route

# What is Protected Route?

Agar user logged in nahi hai:

```text id="11r5kf"
Redirect to login page
```

---

# Why Use?

Sensitive pages secure karne ke liye.

---

# Use Cases

* Dashboard
* Profile
* Admin panel
* Payment page

---

# Next.js Protected Route Example

## File Structure

```text id="0vwbj8"
app/
 ├── dashboard/
 │    └── page.js
 └── login/
      └── page.js
```

---

# Dashboard Page

```jsx id="n9x2se"
"use client";

import { useRouter } from "next/navigation";
import { useEffect } from "react";

export default function Dashboard() {
  const router = useRouter();

  useEffect(() => {
    const isLoggedIn =
      localStorage.getItem("token");

    if (!isLoggedIn) {
      router.push("/login");
    }
  }, []);

  return (
    <div>
      <h1>Dashboard Page</h1>
    </div>
  );
}
```

---

# Login Page

```jsx id="u85tqk"
"use client";

export default function Login() {
  const handleLogin = () => {
    localStorage.setItem("token", "123");

    alert("Logged In");
  };

  return (
    <button onClick={handleLogin}>
      Login
    </button>
  );
}
```

---

# Interview Points

* Authentication
* Authorization
* Route Security
* Middleware also used in Next.js

---

# Better Production Approach

Use:

* NextAuth
* JWT
* Middleware
* Cookies

instead of localStorage.

---

# Task 4 — Image Optimization

# What is Image Optimization?

Images ko optimized way me load karna.

---

# Why Important?

Large images slow website.

Optimization improves:

* Performance
* SEO
* Loading speed
* Core Web Vitals

---

# Next.js Image Component

```jsx id="m4o3e3"
import Image from "next/image";
```

---

# Basic Example

```jsx id="rlom3j"
import Image from "next/image";

export default function Home() {
  return (
    <div>
      <Image
        src="/img.png"
        width={200}
        height={200}
        alt="img"
      />
    </div>
  );
}
```

---

# Benefits of `next/image`

# 1. Lazy Loading

Image tabhi load hoti hai jab viewport me aaye.

---

# 2. Automatic Optimization

Size optimize automatically.

---

# 3. Faster Performance

Compressed images serve hoti hain.

---

# 4. Responsive Images

Different screen sizes ke liye optimize.

---

# 5. Better SEO

Improves Core Web Vitals.

---

# Advanced Example

```jsx id="9v0pff"
import Image from "next/image";

export default function Home() {
  return (
    <Image
      src="/img.png"
      alt="Profile"
      width={400}
      height={400}
      priority
      quality={80}
    />
  );
}
```

---

# Important Props

| Prop     | Purpose             |
| -------- | ------------------- |
| src      | Image path          |
| width    | Image width         |
| height   | Image height        |
| alt      | Accessibility       |
| priority | Fast loading        |
| quality  | Compression quality |

---

# Interview Questions

# Q1. Why use `next/image`?

Because it provides automatic image optimization, lazy loading, responsive images, and improves performance.

---

# Q2. Difference between `<img>` and `<Image>`?

| img             | next/image             |
| --------------- | ---------------------- |
| No optimization | Automatic optimization |
| No lazy loading | Lazy loading           |
| Slower          | Faster                 |
| Manual handling | Automatic handling     |

---

# Q3. What is lazy loading?

Image tab load hoti hai jab user us image ke paas scroll karta hai.

---

# Final Interview Revision

# Debounce

```text id="2q3hwy"
Delay API call
Reduce unnecessary requests
```

---

# Pagination

```text id="4q9d3y"
Load data page by page
Improve performance
```

---

# Protected Route

```text id="q52o6m"
If not logged in
Redirect user
```

---

# Image Optimization

```text id="04skdc"
Use next/image
Optimize performance
Improve SEO
```


