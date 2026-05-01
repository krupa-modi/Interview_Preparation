
# ⚛️ React PureComponent – Complete Interview Guide

## 📌 What is PureComponent?

**PureComponent** is a special type of class component in React that **automatically implements `shouldComponentUpdate()` with a shallow comparison** of props and state.

👉 It helps in **performance optimization** by preventing unnecessary re-renders.

---

## 🧠 Simple Definition

> A **PureComponent** only re-renders when there is a **change in props or state (shallow comparison)**.

---

## ⚙️ How It Works

Normally, a React component re-renders every time:

* Props change ✅
* State changes ✅
* Parent re-renders ❗ (even if data didn’t change)

👉 But **PureComponent prevents unnecessary re-renders** by checking:

```
Old Props === New Props ?
Old State === New State ?
```

If both are same → ❌ No re-render
If different → ✅ Re-render

---

## 🔍 What is Shallow Comparison?

Shallow comparison means:

* It checks only **top-level values**
* It does NOT check deeply nested objects

### Example:

```js
const obj1 = { name: "Krupa" };
const obj2 = { name: "Krupa" };

console.log(obj1 === obj2); // ❌ false (different reference)
```

👉 Even if values look same, references are different → re-render happens.

---

## 🧱 Syntax of PureComponent

```js
import React, { PureComponent } from "react";

class MyComponent extends PureComponent {
  render() {
    console.log("Rendered");
    return <h1>Hello {this.props.name}</h1>;
  }
}

export default MyComponent;
```

---

## 🧪 Example: Normal Component vs PureComponent

### ❌ Normal Component

```js
class NormalComp extends React.Component {
  render() {
    console.log("Normal Component Rendered");
    return <h1>{this.props.value}</h1>;
  }
}
```

```
# ⚛️ React Example: Component vs PureComponent (Based on Your Code)

## 🔴 1. Normal Component Example

```js
import './App.css';
import React from 'react';

class App extends React.Component {
  constructor() {
    super();
    this.state = {
      count: 1
    };
  }

  render() {
    console.warn("check re-rendering");

    return (
      <div className="App">
        <h1>Normal Component in React {this.state.count}</h1>

        <button onClick={() => this.setState({ count: 1 })}>
          Update Count
        </button>
      </div>
    );
  }
}

export default App;
```

---

## ❗ Behavior (Important)

👉 Even if `count` value is SAME (`1 → 1`),
React **will still re-render** the component.

👉 Console Output:

```
check re-rendering
check re-rendering
check re-rendering
```

➡️ Because normal `Component` does NOT check for changes.



---

### ✅ PureComponent

```js
class PureComp extends React.PureComponent {
  render() {
    console.log("Pure Component Rendered");
    return <h1>{this.props.value}</h1>;
  }
}
```

👉 Re-renders ONLY if value changes.

# 🟢 2. PureComponent Example (Your Given Code)

```js
import './App.css';
import React from 'react';

class App extends React.PureComponent {
  constructor() {
    super();
    this.state = {
      count: 1
    };
  }

  render() {
    console.warn("check re-rendering");

    return (
      <div className="App">
        <h1>Pure Component in React {this.state.count}</h1>

        <button onClick={() => this.setState({ count: 1 })}>
          Update Count
        </button>
      </div>
    );
  }
}

export default App;
```

---

## ✅ Behavior (Key Difference)

👉 When you click button:

```js
this.setState({ count: 1 });
```

👉 Old value = 1
👉 New value = 1

👉 PureComponent does **shallow comparison**

➡️ Since value SAME → ❌ No re-render

---

## 🧪 Console Output

```
check re-rendering
```

👉 Only once (initial render)

---

# 🔥 Final Difference (Interview Ready)

| Feature      | Component | PureComponent        |
| ------------ | --------- | -------------------- |
| Re-render    | Always    | Only if data changes |
| Optimization | ❌ No      | ✅ Yes                |
| Comparison   | ❌ None    | ✅ Shallow compare    |
| Performance  | Normal    | Optimized            |

---

# 🧠 Important Concept Used Here

👉 PureComponent checks:

```js
oldState.count === newState.count
```

If TRUE → ❌ skip render
If FALSE → ✅ re-render

---

# ⚠️ Interview Trap

👉 This works because:

```js
count: 1 → primitive value
```

👉 But if you use objects:

```js
this.setState({ user: { name: "Krupa" } });
```

Even if same value → it may re-render
because object reference changes.


👉 Re-renders even if same value is passed.

---

## ⚡ When to Use PureComponent?

Use it when:

* Props and state are **simple (primitive values)**
* You want **performance optimization**
* Component re-renders frequently

---

## ❌ When NOT to Use PureComponent?

Avoid when:

* You have **complex objects or nested data**
* You mutate state directly (bad practice ❗)

### ❌ Problem Example:

```js
this.state.user.name = "New Name"; // mutation ❌
this.setState({ user: this.state.user });
```

👉 PureComponent may NOT detect change → UI won't update

---

## ✅ Correct Way (Immutable Update)

```js
this.setState({
  user: { ...this.state.user, name: "New Name" }
});
```

---

## 🔥 PureComponent vs Component

| Feature               | Component      | PureComponent        |
| --------------------- | -------------- | -------------------- |
| Re-render             | Always         | Only if data changes |
| Performance           | Less optimized | More optimized       |
| shouldComponentUpdate | Manual         | Automatic            |
| Comparison            | No check       | Shallow comparison   |

---

## 🧠 PureComponent vs React.memo

| Feature      | PureComponent   | React.memo           |
| ------------ | --------------- | -------------------- |
| Type         | Class Component | Functional Component |
| Optimization | Yes             | Yes                  |
| Comparison   | Shallow         | Shallow              |

👉 React.memo is functional equivalent of PureComponent

---

## 💡 Interview Tips

* PureComponent = **automatic shouldComponentUpdate**
* Uses **shallow comparison**
* Improves **performance**
* Works best with **immutable data**
* Functional alternative → **React.memo**

---

## 🎯 Final Summary

* PureComponent helps avoid unnecessary renders
* It compares old vs new props/state
* Works best with simple & immutable data
* Important for performance optimization in React apps



Just tell me 👍
