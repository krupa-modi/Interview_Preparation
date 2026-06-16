# React Todo Application (Add, Edit, Delete)

# Features

✅ Add Task
✅ Edit Task
✅ Delete Task
✅ Empty input field after adding task
✅ Empty task cannot be added
✅ Beginner Friendly
✅ Interview Ready

---

# Full Code

## App.js

```jsx id="wh7v4m"
import React, { useState } from "react";

function App() {

  // Store input value
  const [input, setInput] = useState("");

  // Store all tasks
  const [tasks, setTasks] = useState([]);

  // Store edit index
  const [editIndex, setEditIndex] = useState(null);

  // Add Task Function
  const addTask = () => {

    // Prevent empty task
    if (input.trim() === "") {
      return;
    }

    // Edit Task
    if (editIndex !== null) {

      const updatedTasks = [...tasks];

      updatedTasks[editIndex] = input;

      setTasks(updatedTasks);

      setEditIndex(null);

    } else {

      // Add New Task
      setTasks([...tasks, input]);
    }

    // Empty input field
    setInput("");
  };

  // Delete Task
  const deleteTask = (index) => {

    const updatedTasks = tasks.filter((item, i) => i !== index);

    setTasks(updatedTasks);
  };

  // Edit Task
  const editTask = (index) => {

    setInput(tasks[index]);

    setEditIndex(index);
  };

  return (
    <div style={{ padding: "20px" }}>

      <h1>Todo App</h1>

      <input
        type="text"
        placeholder="Enter Task"
        value={input}
        onChange={(e) => setInput(e.target.value)}
      />

      <button onClick={addTask}>
        {editIndex !== null ? "Update" : "Add"}
      </button>

      <ul>

        {tasks.map((task, index) => (
          <li key={index}>

            {task}

            <button onClick={() => editTask(index)}>
              Edit
            </button>

            <button onClick={() => deleteTask(index)}>
              Delete
            </button>

          </li>
        ))}

      </ul>

    </div>
  );
}

export default App;
```

---

# Step-by-Step Explanation

# 1. useState for Input

```jsx id="pm7v8k"
const [input, setInput] = useState("");
```

Stores input field value.

---

# 2. useState for Tasks

```jsx id="k7x4bv"
const [tasks, setTasks] = useState([]);
```

Stores all todo tasks in array.

---

# 3. useState for Edit

```jsx id="xj2qpe"
const [editIndex, setEditIndex] = useState(null);
```

Stores which task is being edited.

---

# 4. Prevent Empty Task

```jsx id="3vpk2d"
if (input.trim() === "") {
  return;
}
```

* `trim()` removes spaces
* Empty task will not add

Example:

```js id="j9n2pw"
"   ".trim() // ""
```

---

# 5. Add Task

```jsx id="k6r1mn"
setTasks([...tasks, input]);
```

Adds new task into array.

Example:

```js id="b5r2zt"
["HTML", "CSS"]
```

after adding:

```js id="t8f7qw"
["HTML", "CSS", "React"]
```

---

# 6. Empty Input After Add

```jsx id="w3m8ds"
setInput("");
```

Clears input field.

---

# 7. Delete Task

```jsx id="d9v4qo"
const updatedTasks = tasks.filter((item, i) => i !== index);
```

Removes selected task.

---

# 8. Edit Task

```jsx id="q7y1an"
setInput(tasks[index]);
setEditIndex(index);
```

* Puts old value into input
* Stores edit index

---

# 9. Update Task

```jsx id="u2k9xp"
updatedTasks[editIndex] = input;
```

Updates old task with new value.



# React Debounce Search (Interview Question)

---

# Full React Code

```jsx
import React, { useState, useEffect } from "react";

function App() {

  const users = [
    "React",
    "Angular",
    "Vue",
    "JavaScript",
    "TypeScript",
    "NodeJS",
    "NextJS",
    "Redux",
    "MongoDB",
    "Express"
  ];

  const [search, setSearch] = useState("");
  const [debouncedSearch, setDebouncedSearch] = useState("");
  const [result, setResult] = useState(users);

  // Debounce Logic
  useEffect(() => {

    const timer = setTimeout(() => {
      setDebouncedSearch(search);
    }, 500);

    return () => clearTimeout(timer);

  }, [search]);

  // Search Logic
  useEffect(() => {

    const filteredData = users.filter((item) =>
      item.toLowerCase().includes(
        debouncedSearch.toLowerCase()
      )
    );

    setResult(filteredData);

  }, [debouncedSearch]);

  return (
    <div style={{ padding: "20px" }}>

      <h2>Debounce Search</h2>

      <input
        type="text"
        placeholder="Search..."
        value={search}
        onChange={(e) => setSearch(e.target.value)}
      />

      <ul>
        {result.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>

    </div>
  );
}

export default App;
```


# React Debounce Search with Dummy API (Interview Ready)

```jsx
import React, { useEffect, useState } from "react";

function App() {

  const [search, setSearch] = useState("");
  const [debouncedSearch, setDebouncedSearch] = useState("");

  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(false);

  // Debounce Logic
  useEffect(() => {

    const timer = setTimeout(() => {
      setDebouncedSearch(search);
    }, 500);

    return () => clearTimeout(timer);

  }, [search]);

  // API Call After Debounce
  useEffect(() => {

    if (!debouncedSearch) {
      setUsers([]);
      return;
    }

    fetchUsers();

  }, [debouncedSearch]);

  const fetchUsers = async () => {

    try {

      setLoading(true);

      const response = await fetch(
        "https://jsonplaceholder.typicode.com/users"
      );

      const data = await response.json();

      const filteredUsers = data.filter((user) =>
        user.name
          .toLowerCase()
          .includes(
            debouncedSearch.toLowerCase()
          )
      );

      setUsers(filteredUsers);

    } catch (error) {

      console.log(error);

    } finally {

      setLoading(false);
    }
  };

  return (
    <div style={{ padding: "20px" }}>

      <h2>User Search</h2>

      <input
        type="text"
        placeholder="Search User..."
        value={search}
        onChange={(e) =>
          setSearch(e.target.value)
        }
      />

      {loading && <p>Loading...</p>}

      {users.map((user) => (
        <div key={user.id}>
          {user.name}
        </div>
      ))}

    </div>
  );
}

export default App;
```

# Building a Custom React Hook for Debouncing User Input

## What is a Custom Hook?

A Custom Hook is a JavaScript function that starts with `use` and allows you to reuse stateful logic across components.

Example:

```js
useDebounce()
useFetch()
useLocalStorage()
```

---

# Step 1: Create useDebounce Hook

## useDebounce.js

```jsx
import { useState, useEffect } from "react";

function useDebounce(value, delay) {

  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {

    const timer = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => clearTimeout(timer);

  }, [value, delay]);

  return debouncedValue;
}

export default useDebounce;
```


# Step 2: Use Hook in Component

## App.js

```jsx
import React, { useState } from "react";
import useDebounce from "./useDebounce";

function App() {

  const [search, setSearch] = useState("");

  const debouncedSearch = useDebounce(search, 500);

  const technologies = [
    "React",
    "Angular",
    "Vue",
    "JavaScript",
    "TypeScript",
    "NextJS",
    "NodeJS",
    "Redux"
  ];

  const filteredData = technologies.filter((item) =>
    item.toLowerCase().includes(
      debouncedSearch.toLowerCase()
    )
  );

  return (
    <div>

      <h2>Search Technology</h2>

      <input
        type="text"
        placeholder="Search..."
        value={search}
        onChange={(e) => setSearch(e.target.value)}
      />

      <ul>
        {filteredData.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>

    </div>
  );
}

export default App;
```


## Counter App 
```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  const decrement = () => {
    setCount(count - 1);
  };

  const reset = () => {
    setCount(0);
  };

  return (
    <div>
      <h2>Counter: {count}</h2>

      <button onClick={increment}>Increment</button>

      <button onClick={decrement}>Decrement</button>

      <button onClick={reset}>Reset</button>
    </div>
  );
}

export default Counter;
```


### Simple Pagination (React + useState)

```jsx
import React, { useState } from "react";

function Pagination() {
  const data = [
    "User 1",
    "User 2",
    "User 3",
    "User 4",
    "User 5",
    "User 6",
    "User 7",
    "User 8",
    "User 9",
    "User 10",
  ];

  const [page, setPage] = useState(1);

  const itemsPerPage = 3;

  const start = (page - 1) * itemsPerPage;
  const end = start + itemsPerPage;

  const currentData = data.slice(start, end);

  const totalPages = Math.ceil(
    data.length / itemsPerPage
  );

  return (
    <div>
      <h2>Pagination Example</h2>

      {currentData.map((item, index) => (
        <p key={index}>{item}</p>
      ))}

      <button
        disabled={page === 1}
        onClick={() => setPage(page - 1)}
      >
        Previous
      </button>

      <span>
        {" "}
        Page {page} of {totalPages}{" "}
      </span>

      <button
        disabled={page === totalPages}
        onClick={() => setPage(page + 1)}
      >
        Next
      </button>
    </div>
  );
}

export default Pagination;
```

# React Form Validation (Name + Email)

```jsx
import React, { useState } from "react";

function FormValidation() {
  const [formData, setFormData] = useState({
    name: "",
    email: "",
  });

  const [errors, setErrors] = useState({});

  const handleChange = (e) => {
    const { name, value } = e.target;

    setFormData({
      ...formData,
      [name]: value,
    });
  };

  const handleSubmit = (e) => {
    e.preventDefault();

    let newErrors = {};

    // Name Validation
    if (!formData.name.trim()) {
      newErrors.name = "Name is required";
    }

    // Email Validation
    if (!formData.email.trim()) {
      newErrors.email = "Email is required";
    } else if (
      !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(
        formData.email
      )
    ) {
      newErrors.email = "Invalid Email";
    }

    setErrors(newErrors);

    if (Object.keys(newErrors).length === 0) {
      alert("Form Submitted Successfully");
      console.log(formData);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <input
          type="text"
          name="name"
          placeholder="Enter Name"
          value={formData.name}
          onChange={handleChange}
        />

        {errors.name && (
          <p style={{ color: "red" }}>
            {errors.name}
          </p>
        )}
      </div>

      <div>
        <input
          type="text"
          name="email"
          placeholder="Enter Email"
          value={formData.email}
          onChange={handleChange}
        />

        {errors.email && (
          <p style={{ color: "red" }}>
            {errors.email}
          </p>
        )}
      </div>

      <button type="submit">
        Submit
      </button>
    </form>
  );
}

export default FormValidation;
```

# React Modal Popup

```jsx
import React, { useState } from "react";

function App() {
  const [isModalOpen, setIsModalOpen] = useState(false);

  return (
    <div>
      <button
        onClick={() => setIsModalOpen(true)}
      >
        Open Modal
      </button>

      {isModalOpen && (
        <div style={overlayStyle}>
          <div style={modalStyle}>
            <h2>Modal Title</h2>

            <p>
              This is a simple modal popup.
            </p>

            <button
              onClick={() =>
                setIsModalOpen(false)
              }
            >
              Close
            </button>
          </div>
        </div>
      )}
    </div>
  );
}

const overlayStyle = {
  position: "fixed",
  top: 0,
  left: 0,
  width: "100%",
  height: "100%",
  backgroundColor:
    "rgba(0,0,0,0.5)",
  display: "flex",
  justifyContent: "center",
  alignItems: "center",
};

const modalStyle = {
  background: "#fff",
  padding: "20px",
  borderRadius: "8px",
  width: "300px",
};

export default App;
```
