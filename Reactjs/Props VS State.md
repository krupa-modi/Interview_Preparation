
##  What are Props?

Props (short for **properties**) are used to **pass data from parent to child component**.

* Read-only (immutable)
* Used for communication between components

### Example:

```jsx
function Child(props) {
  return <h1>Hello {props.name}</h1>;
}

function App() {
  return <Child name="Krupa" />;
}
```

👉 Props = Input to a component

---

## What is State?

State is used to store **dynamic data inside a component**.

* Mutable (can change)
* Triggers re-render when updated

### Example:

```jsx
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increase</button>
    </>
  );
}
```

👉 State = Internal data of component

---

## 🔥 Props vs State (Important Interview Question)

| Feature    | Props              | State                    |
| ---------- | ------------------ | ------------------------ |
| Mutability | Read-only          | Mutable                  |
| Usage      | Passed from parent | Managed inside component |
| Control    | External           | Internal                 |
| Re-render  | Yes                | Yes                      |

👉 Props = external data
👉 State = internal data

---

## 🔥 Quick Revision

* Functional Components → Modern, use Hooks
* Class Components → Old, use lifecycle methods
* Controlled → React handles form data
* Uncontrolled → DOM handles form data
* Props → Data from parent
* State → Internal dynamic data

---
