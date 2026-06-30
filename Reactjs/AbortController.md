# AbortController - React Interview Notes

## What is AbortController?

**AbortController** is a browser API used to cancel or abort ongoing API requests.

It is commonly used when:

* Component unmounts before API response arrives.
* User triggers a new API request before the previous one completes.
* We want to avoid unnecessary API calls.
* We want to prevent memory leaks and state update warnings.

---

# Why Do We Need AbortController?

Suppose an API request is taking 5 seconds.

```text
Component Mounted
      ↓
API Call Started
      ↓
User Navigates Away
      ↓
Component Unmounted
      ↓
API Response Arrives
      ↓
setState() Tries To Run
```

This can cause:

* Memory leaks
* Unnecessary state updates
* React warnings

To prevent this, we cancel the API request using AbortController.

---

# Example

```jsx
import { useEffect, useState } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    const controller = new AbortController();

    fetch("https://jsonplaceholder.typicode.com/users", {
      signal: controller.signal,
    })
      .then((res) => res.json())
      .then((data) => setUsers(data))
      .catch((err) => {
        if (err.name !== "AbortError") {
          console.log(err);
        }
      });

    return () => {
      controller.abort(); // abort means cancel
    };
  }, []);

  return <div>{users.length}</div>;
}
```

---

# How It Works?

### Step 1

Create AbortController.

```js
const controller = new AbortController();
```

### Step 2

Pass signal to fetch request.

```js
signal: controller.signal;
```

### Step 3

When component unmounts, cleanup function runs.

```js
return () => {
  controller.abort();
};
```

### Step 4

Pending API request gets cancelled.

---

# Real Interview Scenario

### Search API

User types:

```text
r
re
rea
react
```

Every key press triggers an API call.

When a new request starts, cancel the previous request using AbortController.

Benefits:

* Prevents duplicate requests.
* Saves network bandwidth.
* Improves performance.

---

# Benefits of AbortController

* Cancels pending API requests.
* Prevents memory leaks.
* Avoids unnecessary state updates.
* Improves application performance.
* Reduces server load.

---

# Interview Question

## When Would You Use AbortController?

### Answer

> I use AbortController when an API request may still be running while the component unmounts or when a new request replaces the previous one. It helps cancel pending requests and prevents unnecessary state updates and memory leaks.

---

# Interview Question

## What Problem Does AbortController Solve?

### Answer

> AbortController prevents pending API requests from completing after a component has unmounted. This avoids memory leaks, unnecessary state updates, and improves application performance.

---

# Short Interview Answer (30 Seconds)

> AbortController is used to cancel ongoing API requests. I mainly use it inside the useEffect cleanup function when a component unmounts or when a new request is triggered before the previous one completes. This helps prevent memory leaks and unnecessary state updates.

---

# One-Line Answer

> AbortController is used to cancel pending API requests and prevent memory leaks or unnecessary state updates in React applications.

### Most Common Interview Answer

**Q: API call chal rahi hai aur component unmount ho gaya. State update warning kaise avoid karoge?**

**Answer:**

> I will use AbortController inside the useEffect cleanup function. When the component unmounts, I will abort the pending API request, preventing unnecessary state updates and memory leaks. ✅
