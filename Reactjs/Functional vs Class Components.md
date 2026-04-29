
# ⚛️ React Interview Notes (Core Concepts)

---

## 1. Functional vs Class Components

### 🔹 Functional Components

* Simple JavaScript functions
* Use **Hooks** (useState, useEffect)
* Preferred in modern React

### Example:

```jsx
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count  1)}>Increment</button>
    </div>
  );
}

export default Counter;
```

---

### 🔹 Class Components

* ES6 classes
* Use **this.state** and lifecycle methods
* Older approach (less used now)
* class component are es6 classes that extend React.component and use a render() method to return jsx.

### Example:

```jsx
import React, { Component } from "react";

class Counter extends React.Component{
render()
return{
<h1>hello</h1>
  }
}
OR
class Counter extends Component {
  constructor() {
    super();
    this.state = { count: 0 };
  }

  render() {
    return (
      <div>
        <p>{this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Increment
        </button>
      </div>
    );
  }
}

export default Counter;
```

---

### 🔥 Key Differences

| Feature     | Functional Component | Class Component   |
| ----------- | -------------------- | ----------------- |
| Syntax      | Simple function      | ES6 class         |
| State       | useState Hook        | this.state        |
| Lifecycle   | useEffect Hook       | Lifecycle methods |
| Performance | Faster & cleaner     | Slightly complex  |
| Usage       | Modern React         | Legacy            |

👉 **Interview Tip:** Always prefer **Functional Components + Hooks**

---


---
