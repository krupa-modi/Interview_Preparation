
# ⚛️ Shallow Comparison in React (Interview Guide)

## 📌 What is Shallow Comparison?

👉 **Shallow comparison** means checking whether **two values are equal by comparing only their top-level references**, not their deep/nested values.

### 🧠 Simple Definition

> React checks:
> **Old value === New value (reference check)**

If equal → ❌ No re-render
If different → ✅ Re-render

---

## 🔍 How It Works

React uses shallow comparison in:

* `PureComponent`
* `React.memo`

👉 It compares:

```js
oldProps === newProps
oldState === newState
```

---

## 🧪 Example 1: Primitive Values

```js
let a = 10;
let b = 10;

console.log(a === b); // ✅ true
```

👉 Same value → No re-render (in PureComponent)

---

## 🧪 Example 2: Objects (Important)

```js
let obj1 = { name: "Krupa" };
let obj2 = { name: "Krupa" };

console.log(obj1 === obj2); // ❌ false
```

👉 Why false?

* Because references are different
* Even though values look same

---

## 📦 Visual Understanding

```js
obj1 → memory address A
obj2 → memory address B
```

👉 A !== B → React thinks data changed → re-render

---

## 🔴 Problem Case (Mutation)

```js
this.state.user.name = "Modi"; // ❌ mutation

this.setState({
  user: this.state.user
});
```

👉 Reference SAME → shallow compare says NO change
👉 ❌ UI will NOT update

---

## 🟢 Correct Way (Immutable Update)

```js
this.setState({
  user: { ...this.state.user, name: "Modi" }
});
```

👉 New object created → new reference
👉 ✅ React detects change → re-render

---

## 🔥 Real Example in PureComponent

```js
class App extends React.PureComponent {
  render() {
    console.log("Rendered");
    return <h1>{this.props.data.name}</h1>;
  }
}
```

👉 If parent sends:

```js
data = { name: "Krupa" }
```

Even if same value but new object → re-render happens

---

## ⚡ Key Points

* Shallow comparison checks **only 1 level deep**
* Works with **reference equality**
* Fast & efficient
* Does NOT check nested values

---

## ❌ Limitation

```js
let obj1 = { user: { name: "Krupa" } };
let obj2 = { user: { name: "Krupa" } };

obj1 === obj2 // ❌ false
```

👉 Deep values same, but shallow compare fails

---

## 🧠 Shallow vs Deep Comparison

| Feature       | Shallow | Deep    |
| ------------- | ------- | ------- |
| Level         | 1 level | Nested  |
| Speed         | Fast ⚡  | Slow 🐢 |
| Used in React | ✅ Yes   | ❌ No    |

---

## 🎯 Interview Tips

* Used in **PureComponent & React.memo**
* Based on **reference equality (===)**
* Works best with **immutable data**
* Does NOT detect deep changes

---

## 🚀 Final Summary

* Shallow comparison = top-level check
* React uses it for performance optimization
* Immutable updates are required
* Key concept for React interviews 🔥

---


Just tell me 👍
