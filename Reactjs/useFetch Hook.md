# useFetch Custom Hook in React JS

## What is useFetch Hook?

`useFetch` is a custom React hook used to fetch API data and reuse fetching logic in multiple components.
It helps:

* Reduce duplicate code
* Make API handling reusable
* Improve clean code structure

---

# Basic Syntax

```js id="q1h3m8"
const { data, loading, error } = useFetch(url);
```

---

# Why use Custom Hook?

Without custom hook:

```js id="xtv4v0"
useEffect(() => {
  fetch("API_URL")
    .then((res) => res.json())
    .then((data) => setData(data));
}, []);
```

If multiple components need API calls, same code repeats.

So we create reusable hook → `useFetch`

---

# Complete useFetch Hook

## useFetch.js

```js id="rwv2p6"
import { useEffect, useState } from "react";

function useFetch(url) {

  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {

    const fetchData = async () => {
      try {
        setLoading(true);
        const response = await fetch(url);

        if (!response.ok) {
          throw new Error("Failed to fetch");
        }

        const result = await response.json();
        setData(result);

      } catch (err) {
        setError(err.message)
      } finally {
        setLoading(false);
      }
    };

    fetchData();

  }, [url]);

  return { data, loading, error };
}

export default useFetch;
```

---

# How to Use

## App.js

```js id="kw2s0j"
import useFetch from "./useFetch";

function App() {

  const {data,loading,error} = useFetch("https://jsonplaceholder.typicode.com/users");

  if (loading) {
    return <h1>Loading...</h1>;
  }

  if (error) {
    return <h1>{error}</h1>;
  }

  return (
    <div>
      <h1>User List</h1>

      {
        data.map((user) => (
          <p key={user.id}>
            {user.name}
          </p>
        ))
      }
    </div>
  );
}

export default App;
```

---

# Output

```js id="gf2jcm"
User List

Leanne Graham
Ervin Howell
Clementine Bauch
...
```

# Real Interview Explanation

> `useFetch` is a reusable custom hook used for API calling in React applications. It helps separate fetching logic from UI components and improves code reusability, readability, and maintainability.

---

# Advantages

* Reusable code
* Cleaner components
* Easy loading/error handling
* Better maintainability

---


# Why AbortController Used?

To prevent:

* Memory leaks
* State updates after component unmount

Very important in interview.

---

# Common Interview Questions

---

## Q1. What is custom hook in React?

> Custom hooks are reusable JavaScript functions starting with `use` that can use React hooks internally.

---

## Q2. Why use useFetch hook?

* Reusability
* Clean code
* Centralized API logic

---

## Q3. Can we use hooks inside normal functions?

❌ No

Hooks can only be used:

* Inside React components
* Inside custom hooks

---

## Q4. Why custom hooks start with `use`?

React identifies them as hooks using naming convention.

Example:

* `useFetch`
* `useAuth`
* `useForm`

---

# Real Company Use Cases

* Fetch users
* Product list
* Dashboard APIs
* Infinite scrolling
* Search APIs
* Notifications

---

# Short Interview Answer

> `useFetch` is a reusable custom hook in React used to handle API calls. It manages loading, error, and response states separately and keeps components clean and reusable.
