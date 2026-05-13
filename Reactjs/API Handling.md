# 🔹 What is API Handling?

API Handling means:

* Sending requests to a server
* Receiving data from backend/API
* Showing data in UI
* Handling errors
* Managing loading states

React applications commonly use APIs to fetch dynamic data from backend servers.

---

# 📌 Common API Operations

| Method | Purpose              |
| ------ | -------------------- |
| GET    | Fetch data           |
| POST   | Send new data        |
| PUT    | Update existing data |
| PATCH  | Partial update       |
| DELETE | Delete data          |

---

# 🔥 Example API

```txt id="1mb0sn"
https://jsonplaceholder.typicode.com/users
```

This API returns users data.

---

# 📌 Ways to Handle APIs in React

Mainly two methods:

1. Fetch API
2. Axios

---

# 🔥 1️⃣ Fetch API

---

# 📌 What is Fetch?

`fetch()` is a built-in JavaScript method used to make HTTP requests.

No external library required.

---

# ✅ Basic Fetch Syntax

```jsx id="qlm2zw"
fetch(url)
```

---

# ✅ GET Request Example

```jsx id="ic1ovm"
import { useEffect, useState } from "react";

function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => setUsers(data));
  }, []);

  return (
    <div>
      {users.map((user) => (
        <h3 key={user.id}>{user.name}</h3>
      ))}
    </div>
  );
}

export default App;
```

---

# 📌 How Fetch Works

1. Request sent to API
2. Response received
3. Convert response to JSON
4. Store data in state
5. Render UI

---

# 🔥 2️⃣ Axios

---

# 📌 What is Axios?

Axios is a popular third-party library used for API handling.

It is easier and cleaner than Fetch.

---

# ✅ Install Axios

```bash id="hzh5ui"
npm install axios
```

---

# ✅ GET Request Using Axios

```jsx id="rgqkpn"
import axios from "axios";
import { useEffect, useState } from "react";

function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        setUsers(response.data);
      });
  }, []);

  return (
    <div>
      {users.map((user) => (
        <h2 key={user.id}>{user.name}</h2>
      ))}
    </div>
  );
}

export default App;
```

---

# 📌 Fetch vs Axios

| Feature              | Fetch                      | Axios      |
| -------------------- | -------------------------- | ---------- |
| Built into Browser   | ✅ Yes                      | ❌ No       |
| Need Installation    | ❌ No                       | ✅ Yes      |
| JSON Conversion      | Manual (`response.json()`) | Automatic  |
| Error Handling       | Harder                     | Easier     |
| Request Cancellation | Limited                    | Better     |
| Interceptors         | ❌ No                       | ✅ Yes      |
| Timeout Support      | ❌ Manual                   | ✅ Built-in |
| Syntax               | More verbose               | Cleaner    |

---

# 🎯 Interview Answer

## ❓ Fetch vs Axios

### ✅ Answer:

Fetch is a built-in JavaScript API used for making HTTP requests, while Axios is a third-party library with additional features like automatic JSON parsing, interceptors, timeout handling, and better error handling.

Axios provides cleaner syntax and is commonly used in React applications.

---

# 📌 Error Handling in API Calls

---

# 🔥 Why Error Handling is Important?

API requests may fail because of:

* Network issues
* Server errors
* Invalid API endpoints
* Unauthorized access

Without error handling, app may crash.

---

# ✅ Error Handling Using Fetch

```jsx id="e23v7g"
import { useEffect, useState } from "react";

function App() {
  const [users, setUsers] = useState([]);
  const [error, setError] = useState("");

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        if (!response.ok) {
          throw new Error("Failed to fetch data");
        }

        return response.json();
      })
      .then((data) => setUsers(data))
      .catch((err) => {
        setError(err.message);
      });
  }, []);

  return (
    <div>
      {error && <h2>{error}</h2>}
    </div>
  );
}

export default App;
```

---

# ✅ Error Handling Using Axios

```jsx id="l2e5ep"
import axios from "axios";
import { useEffect, useState } from "react";

function App() {
  const [users, setUsers] = useState([]);
  const [error, setError] = useState("");

  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => {
        setUsers(response.data);
      })
      .catch((err) => {
        setError("Something went wrong");
      });
  }, []);

  return (
    <div>
      {error && <h2>{error}</h2>}
    </div>
  );
}

export default App;
```

---

# 📌 Best Practices for Error Handling

✅ Show user-friendly messages
✅ Use try-catch with async/await
✅ Handle network/server errors properly
✅ Avoid application crash

---

# 🔥 Loading States

---

# 📌 What is Loading State?

Loading state indicates that data is being fetched from API.

It improves user experience.

---

# ✅ Why Loading State is Important?

Without loading state:

* Blank screen appears
* User gets confused
* Bad user experience

---

# ✅ Loading State Example

```jsx id="nlmjlwm"
import { useEffect, useState } from "react";

function App() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => {
        setUsers(data);
        setLoading(false);
      });
  }, []);

  if (loading) {
    return <h1>Loading...</h1>;
  }

  return (
    <div>
      {users.map((user) => (
        <h2 key={user.id}>{user.name}</h2>
      ))}
    </div>
  );
}

export default App;
```

---

# 📌 Loading Flow

1. API request starts
2. `loading = true`
3. Show spinner/loading text
4. Data fetched
5. `loading = false`
6. Show actual UI

---

# 🔥 Using async/await (Best Practice)

---

# ✅ Example

```jsx id="vdbm3f"
import axios from "axios";
import { useEffect, useState } from "react";

function App() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState("");

  useEffect(() => {
    fetchUsers();
  }, []);

  const fetchUsers = async () => {
    try {
      const response = await axios.get(
        "https://jsonplaceholder.typicode.com/users"
      );

      setUsers(response.data);
    } catch (err) {
      setError("Failed to fetch users");
    } finally {
      setLoading(false);
    }
  };

  if (loading) {
    return <h1>Loading...</h1>;
  }

  if (error) {
    return <h1>{error}</h1>;
  }

  return (
    <div>
      {users.map((user) => (
        <h2 key={user.id}>{user.name}</h2>
      ))}
    </div>
  );
}

export default App;
```

---

# 📌 Why async/await is Better?

✅ Cleaner syntax
✅ Easier error handling
✅ More readable code
✅ Better for large applications

---

# 📌 Real Interview Important Points

---

# 🔥 Common API Interview Questions

---

## ❓ Why use `useEffect` for API calls?

### ✅ Answer:

Because API calls are side effects.
`useEffect` runs after component renders, making it ideal for fetching data.

---

## ❓ Why use loading state?

### ✅ Answer:

Loading state improves user experience by showing a loader while data is being fetched.

---

## ❓ Why use error handling?

### ✅ Answer:

Error handling prevents application crashes and shows meaningful messages to users when API requests fail.

---

## ❓ Which is better: Fetch or Axios?

### ✅ Answer:

Axios is generally preferred in React applications because of cleaner syntax, automatic JSON parsing, interceptors, and better error handling.

---
