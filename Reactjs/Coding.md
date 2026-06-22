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

# How do you implement Search Filter on a Table in React?

### Example

```jsx
import { useState } from "react";

function SearchTable() {
  const [search, setSearch] = useState("");

  const users = [
    { id: 1, name: "Krupa", city: "Pune" },
    { id: 2, name: "Rahul", city: "Mumbai" },
    { id: 3, name: "Amit", city: "Delhi" },
    { id: 4, name: "Neha", city: "Pune" },
  ];

  const filteredUsers = users.filter((user) =>
    user.name.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div>
      <input
        type="text"
        placeholder="Search User"
        value={search}
        onChange={(e) => setSearch(e.target.value)}
      />

      <table border="1">
        <thead>
          <tr>
            <th>Name</th>
            <th>City</th>
          </tr>
        </thead>

        <tbody>
          {filteredUsers.map((user) => (
            <tr key={user.id}>
              <td>{user.name}</td>
              <td>{user.city}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
}

export default SearchTable;
```
## Multiple Columns Search

Agar Name aur City dono par search karna ho:

```js
const filteredUsers = users.filter(
  (user) =>
    user.name.toLowerCase().includes(search.toLowerCase()) ||
    user.city.toLowerCase().includes(search.toLowerCase())
);
```
## Large Data Interview Point

Agar table me 10,000+ records ho to:

```js
const filteredUsers = useMemo(() => {
  return users.filter((user) =>
    user.name.toLowerCase().includes(search.toLowerCase())
  );
}, [users, search]);
```


# React Interview Task: Car Brands and Models Filter

## Problem Statement

Build a basic UI using provided APIs.

### Requirements

* Fetch Car Brands and Models from APIs
* Display data on the UI
* Filter cars based on selected brand
* Handle API integration and state management

---

## Approach

1. Fetch car data using `useEffect`.
2. Store data in state using `useState`.
3. Create a dropdown for car brands.
4. Filter models based on selected brand.
5. Display filtered data in a list.

---

## Example API Response

```javascript
[
  {
    id: 1,
    brand: "Toyota",
    model: "Camry"
  },
  {
    id: 2,
    brand: "Honda",
    model: "City"
  },
  {
    id: 3,
    brand: "Toyota",
    model: "Corolla"
  }
]
```

---

## React Code

```jsx
import React, { useEffect, useState } from "react";

function App() {
  const [cars, setCars] = useState([]);
  const [selectedBrand, setSelectedBrand] = useState("");

  useEffect(() => {
    fetch("YOUR_API_URL")
      .then((res) => res.json())
      .then((data) => setCars(data))
      .catch((err) => console.log(err));
  }, []);

  const filteredCars = selectedBrand
    ? cars.filter((car) => car.brand === selectedBrand)
    : cars;

  const brands = [...new Set(cars.map((car) => car.brand))];

  return (
    <div>
      <h2>Car Brands & Models</h2>

      <select
        value={selectedBrand}
        onChange={(e) => setSelectedBrand(e.target.value)}
      >
        <option value="">All Brands</option>

        {brands.map((brand) => (
          <option key={brand} value={brand}>
            {brand}
          </option>
        ))}
      </select>

      <ul>
        {filteredCars.map((car) => (
          <li key={car.id}>
            {car.brand} - {car.model}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;



****************************************************** OR ***************************************************************
# withput Api

import React from 'react';
import { useState ,useEffect} from 'react'

function App() {
  const cars = [
  {
    id: 1,
    brand: "Toyota",
    model: "Camry"
  },
  {
    id: 2,
    brand: "Honda",
    model: "City"
  },
  {
    id: 3,
    brand: "Toyota",
    model: "Corolla"
  }
]

  const[selectedbrand,setSelectedBrand] = useState("")

 
    const filterdata = selectedbrand
    ? cars.filter((car) => car.brand === selectedbrand)
    : cars;

  const brand = [...new Set(cars.map((item) => item.brand))]
  
  return (
    <div>
    <h1> Display Car Data</h1>
    <select value = {selectedbrand} 
    onChange = {(e) => setSelectedBrand(e.target.value)}
    >
    <option value="">All Brands</option>
    {
      brand.map((val) => (
         <option key = {val}>{val}</option>
      ))
    }
     
    </select>
    <ul>
    {filterdata?.map((item,index) => {
      return(
        <li key = {item.id}>{item.brand}-{item.model}</li>
      )
    })}
    </ul>
      
    </div>
  )
}

export default App
```

---

## Output

### All Cars

```text
Toyota - Camry
Honda - City
Toyota - Corolla
```

### After Selecting Toyota

```text
Toyota - Camry
Toyota - Corolla
```



Interview mein React CRUD (Create, Read, Update, Delete) bahut common question hai. Agar tum ye simple pattern yaad rakh lo to easily bana sakte ho.

# 1. CRUD Kya Hota Hai?

* **Create** → Naya data add karna
* **Read** → Data dikhana
* **Update** → Existing data edit karna
* **Delete** → Data remove karna

---

# Simple React CRUD Example

```jsx
import { useState } from "react";

function CrudApp() {
  const [name, setName] = useState("");
  const [users, setUsers] = useState([]);
  const [editId, setEditId] = useState(null);

  // CREATE & UPDATE
  const handleSubmit = () => {
    if (!name.trim()) return;

    if (editId !== null) {
      // Update
      const updatedUsers = users.map((user) =>
        user.id === editId ? { ...user, name } : user
      );

      setUsers(updatedUsers);
      setEditId(null);
    } else {
      // Create
      const newUser = {
        id: Date.now(),
        name,
      };

      setUsers([...users, newUser]);
    }

    setName("");
  };

  // DELETE
  const handleDelete = (id) => {
    const filteredUsers = users.filter((user) => user.id !== id);
    setUsers(filteredUsers);
  };

  // EDIT
  const handleEdit = (user) => {
    setName(user.name);
    setEditId(user.id);
  };

  return (
    <div>
      <h2>CRUD Operation</h2>

      <input
        type="text"
        value={name}
        placeholder="Enter Name"
        onChange={(e) => setName(e.target.value)}
      />

      <button onClick={handleSubmit}>
        {editId !== null ? "Update" : "Add"}
      </button>

      <ul>
        {users.map((user) => (
          <li key={user.id}>
            {user.name}

            <button onClick={() => handleEdit(user)}>
              Edit
            </button>

            <button onClick={() => handleDelete(user.id)}>
              Delete
            </button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default CrudApp;
```

# without api

```jsx
import { useState } from "react";

function App() {
  const [users, setUsers] = useState([
    { id: 1, name: "Krupa" },
    { id: 2, name: "Rahul" },
  ]);

  const [name, setName] = useState("");
  const [editId, setEditId] = useState(null);

  const handleSubmit = () => {
    if (editId) {
      // Update
      setUsers(
        users.map((user) =>
          user.id === editId
            ? { ...user, name }
            : user
        )
      );
      setEditId(null);
    } else {
      // Create
      setUsers([
        ...users,
        {
          id: Date.now(),
          name,
        },
      ]);
    }

    setName("");
  };

  const handleDelete = (id) => {
    setUsers(users.filter((user) => user.id !== id));
  };

  const handleEdit = (user) => {
    setName(user.name);
    setEditId(user.id);
  };

  return (
    <div>
      <input
        value={name}
        onChange={(e) => setName(e.target.value)}
      />

      <button onClick={handleSubmit}>
        {editId ? "Update" : "Add"}
      </button>

      {users.map((user) => (
        <div key={user.id}>
          {user.name}

          <button onClick={() => handleEdit(user)}>
            Edit
          </button>

          <button onClick={() => handleDelete(user.id)}>
            Delete
          </button>
        </div>
      ))}
    </div>
  );
}

export default App;
```

