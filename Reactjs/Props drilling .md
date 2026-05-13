# 📌 What is Props Drilling in React?

## 🔹 Definition

**Props Drilling** means passing data from a parent component to a deeply nested child component through multiple intermediate components using `props`.

Even if intermediate components do not use that data, they still have to pass it forward.

---

# 🔥 Simple Example

Suppose we have:

```txt
App
 └── Parent
      └── Child
           └── GrandChild
```

If `App` wants to send data to `GrandChild`, the data must pass through:

* Parent
* Child
* Then GrandChild

This is called **Props Drilling**.

---

# ✅ Example Code

## App.jsx

```jsx id="djlwmq"
import Parent from "./Parent";

function App() {
  const user = "Krupa";

  return <Parent user={user} />;
}

export default App;
```

---

## Parent.jsx

```jsx id="bh8v2u"
import Child from "./Child";

function Parent({ user }) {
  return <Child user={user} />;
}

export default Parent;
```

---

## Child.jsx

```jsx id="k43jji"
import GrandChild from "./GrandChild";

function Child({ user }) {
  return <GrandChild user={user} />;
}

export default Child;
```

---

## GrandChild.jsx

```jsx id="2pm2g9"
function GrandChild({ user }) {
  return <h1>Hello {user}</h1>;
}

export default GrandChild;
```

---

# 📌 What is the Props Drilling Problem?

Props drilling becomes a problem when:

* Application becomes large
* Components become deeply nested
* Too many props are passed
* Code becomes hard to manage

---

# ❌ Problems Caused by Props Drilling

---

# 1️⃣ Unnecessary Prop Passing

Intermediate components pass props they don't even use.

Example:

```jsx id="kgfdce"
function Child({ user }) {
  return <GrandChild user={user} />;
}
```

Here `Child` does not use `user`.

Still it must pass it.

---

# 2️⃣ Code Becomes Messy

Too many props make components difficult to read and maintain.

---

# 3️⃣ Difficult Debugging

Tracking data flow becomes harder in large applications.

---

# 4️⃣ Tight Coupling

Components become dependent on parent structure.

Changing hierarchy can break prop flow.

---

# 5️⃣ Poor Scalability

Large apps become difficult to scale with excessive prop passing.

---

# 🎯 Interview Definition

## ❓ What is Props Drilling Problem?

### ✅ Answer:

Props drilling problem occurs when data is passed through multiple nested components only to reach a deeply nested child component.

Intermediate components may not use the data, but they still need to forward it, making code harder to maintain and manage.

---

# 📌 How to Avoid Props Drilling?

There are multiple ways to avoid props drilling in React.

---

# ✅ 1️⃣ Context API (Most Common)

React Context API allows sharing data globally without passing props manually at every level.

---

# 🔥 Example Using Context API

---

## Step 1 — Create Context

```jsx id="e9gl56"
import { createContext } from "react";

export const UserContext = createContext();
```

---

## Step 2 — Provide Context

```jsx id="m6l12k"
import { UserContext } from "./UserContext";
import Parent from "./Parent";

function App() {
  return (
    <UserContext.Provider value={"Krupa"}>
      <Parent />
    </UserContext.Provider>
  );
}

export default App;
```

---

## Step 3 — Consume Context

```jsx id="syjlwm"
import { useContext } from "react";
import { UserContext } from "./UserContext";

function GrandChild() {
  const user = useContext(UserContext);

  return <h1>Hello {user}</h1>;
}

export default GrandChild;
```

---

# ✅ Benefit

Now data directly reaches `GrandChild`.

No need to pass props through Parent and Child.

---

# ✅ 2️⃣ State Management Libraries

For large applications we use:

* Redux
* Zustand
* Recoil
* MobX

These provide centralized state management.

---

# ✅ 3️⃣ Component Composition

Instead of passing props deeply, pass components as children.

---

## Example

```jsx id="gtyvt0"
<Layout>
  <Profile />
</Layout>
```

This reduces unnecessary prop passing.

---

# 📌 When to Use Context API?

Use Context API for:

* Theme
* Authentication
* Language
* User Data
* Global Settings

---

# ❌ When NOT to Use Context API?

Do not use Context for every small state.

Too much Context can also cause unnecessary re-renders.

---

# 📌 Props Drilling vs Context API

| Feature                 | Props Drilling | Context API  |
| ----------------------- | -------------- | ------------ |
| Data Passing            | Manual         | Automatic    |
| Easy for Small Apps     | ✅ Yes          | ✅ Yes        |
| Good for Large Apps     | ❌ No           | ✅ Yes        |
| Code Maintainability    | Hard           | Easier       |
| Intermediate Components | Required       | Not Required |

---

# 🎯 Short Interview Answer

## ❓ What is Props Drilling?

### ✅ Answer:

Props drilling is the process of passing data from a parent component to deeply nested child components through multiple intermediate components using props.

---

## ❓ What is Props Drilling Problem?

### ✅ Answer:

Props drilling becomes a problem when many nested components pass props unnecessarily, making the application harder to maintain and scale.

---

## ❓ How to Avoid Props Drilling?

### ✅ Answer:

We can avoid props drilling using:

* Context API
* Redux or other state management libraries
* Component composition

Context API is the most common solution for small to medium applications.

---
