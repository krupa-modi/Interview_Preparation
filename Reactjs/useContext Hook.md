## 📌 What is `useContext`?

`useContext` is a **React Hook** used to access data from a **Context API** without passing props manually through every component.

It helps solve the problem of **Prop Drilling**.

---

# 🤔 What is Prop Drilling?

Suppose you have data in a parent component and need it in a deeply nested child component.

Without Context:

```jsx
App → Parent → Child → GrandChild
```

You pass props at every level even if intermediate components don't need them.

This is called:

# ❌ Prop Drilling

Example:

```jsx
<App user="Krupa" />
```

Then:

```jsx
<Parent user={user} />
<Child user={user} />
<GrandChild user={user} />
```

This becomes messy in large applications.

---

# ✅ Solution → Context API + useContext

React Context lets you share data globally.

Examples:

* Theme
* User Login Data
* Language
* Auth
* Dark Mode
* Cart Data

---

# 🧠 Simple Definition

> `useContext` allows a component to directly access data from a Context without prop drilling.

---

# 📦 Syntax

```jsx
const value = useContext(MyContext)
```

---

# ⚙️ Steps to Use `useContext`

There are 3 main steps:

---

# 1️⃣ Create Context

```jsx
const UserContext = createContext()
```

---

# 2️⃣ Provide Context

Wrap components with Provider.

```jsx
<UserContext.Provider value={data}>
```

---

# 3️⃣ Consume Context

Use `useContext`.

```jsx
const value = useContext(UserContext)
```

---

# 🔥 Full Example

---

# 📁 File Structure

```bash
src/
 ├── App.js
 ├── UserContext.js
 └── Profile.js
```

---

# 📄 UserContext.js

```jsx
import { createContext } from "react";

const UserContext = createContext();

export default UserContext;
```

---

# 📄 App.js

```jsx
import UserContext from "./UserContext";
import Profile from "./Profile";

function App() {

  const user = "Krupa";

  return (
    <UserContext.Provider value={user}>
      <Profile />
    </UserContext.Provider>
  );
}

export default App;
```

---

# 📄 Profile.js

```jsx
import { useContext } from "react";
import UserContext from "./UserContext";

function Profile() {

  const user = useContext(UserContext);

  return (
    <h1>Hello {user}</h1>
  );
}

export default Profile;
```

---

# ✅ Output

```bash
Hello Krupa
```

---

# 🧠 Flow Diagram

```bash
createContext()
       ↓
Provider gives value
       ↓
useContext receives value
```

---

# 🎯 Real World Example – Dark Mode

---

# 📄 ThemeContext.js

```jsx
import { createContext } from "react";

const ThemeContext = createContext();

export default ThemeContext;
```

---

# 📄 App.js

```jsx
import ThemeContext from "./ThemeContext";
import Home from "./Home";

function App() {

  const theme = "dark";

  return (
    <ThemeContext.Provider value={theme}>
      <Home />
    </ThemeContext.Provider>
  );
}

export default App;
```

---

# 📄 Home.js

```jsx
import { useContext } from "react";
import ThemeContext from "./ThemeContext";

function Home() {

  const theme = useContext(ThemeContext);

  return (
    <div>
      Current Theme: {theme}
    </div>
  );
}

export default Home;
```

---

# 🔥 Using Object in Context

Context can store:

* String
* Number
* Array
* Object
* Function

Example:

```jsx
const user = {
  name: "Krupa",
  age: 22
}
```

Provider:

```jsx
<UserContext.Provider value={user}>
```

Consume:

```jsx
const user = useContext(UserContext)

console.log(user.name)
```

---

# 🔥 Passing Function Through Context

Very important interview concept.

---

# 📄 App.js

```jsx
import { createContext, useState } from "react";
import Child from "./Child";

export const CounterContext = createContext();

function App() {

  const [count, setCount] = useState(0);

  return (
    <CounterContext.Provider value={{ count, setCount }}>
      <Child />
    </CounterContext.Provider>
  );
}

export default App;
```

---

# 📄 Child.js

```jsx
import { useContext } from "react";
import { CounterContext } from "./App";

function Child() {

  const { count, setCount } = useContext(CounterContext);

  return (
    <div>
      <h1>{count}</h1>

      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
}

export default Child;
```

---

# ✅ Output

```bash
0
[Increment]
```

Click:

```bash
1
2
3
```

---

# 🧠 Why useContext is Powerful?

Because it avoids:

* Prop Drilling
* Repeated Props
* Complex component passing

---

# 🚫 Common Mistakes

---

# ❌ Forgetting Provider

Wrong:

```jsx
const value = useContext(UserContext)
```

Without Provider.

This gives:

```bash
undefined
```

---

# ❌ Using Outside Component

Wrong:

```jsx
const value = useContext(UserContext)
```

Outside component.

Hooks only work inside components/custom hooks.

---

# ❌ Re-render Problem

Whenever context value changes,
ALL consuming components re-render.

This can affect performance.

---

# ⚡ How Context Works Internally

React stores context globally in memory.

Provider updates value →
React notifies all consumers →
Consumers re-render.

---

# 🆚 useContext vs Props

| Props                | useContext           |
| -------------------- | -------------------- |
| Pass manually        | Access directly      |
| Good for small apps  | Good for global data |
| Causes prop drilling | Avoids prop drilling |

---

# 🆚 useContext vs Redux

| useContext        | Redux            |
| ----------------- | ---------------- |
| Small-medium apps | Large apps       |
| Simple            | Complex          |
| Built into React  | External library |
| Less boilerplate  | More boilerplate |

---

# ⚠️ Important Interview Points

---

## ✅ `useContext` is a Hook

---

## ✅ It works with Context API

---

## ✅ It avoids prop drilling

---

## ✅ Re-render happens when context changes

---

## ✅ Used for global/shared state

---

# 🔥 Most Asked Interview Questions

---

# 1️⃣ What problem does `useContext` solve?

Answer:

It solves prop drilling by allowing components to access shared data directly.

---

# 2️⃣ Difference between Context API and Redux?

Answer:

Context API is simpler and built into React.
Redux is better for large complex state management.

---

# 3️⃣ Can `useContext` replace Redux?

Answer:

For small-medium apps yes.
For very large apps Redux/Zustand may be better.

---

# 4️⃣ Does `useContext` improve performance?

Answer:

Not always.

When context updates, all consumers re-render.

---

# 5️⃣ Can multiple contexts be used?

Answer:

Yes.

Example:

```jsx
<AuthContext.Provider>
  <ThemeContext.Provider>
    <App />
  </ThemeContext.Provider>
</AuthContext.Provider>
```

---

# 🔥 Multiple Context Example

```jsx
const theme = useContext(ThemeContext);
const user = useContext(UserContext);
```

---

# 📌 Best Practices

---

## ✅ Create separate context files

---

## ✅ Keep context small

---

## ✅ Avoid storing everything in one context

---

## ✅ Use custom hooks for cleaner code

Example:

```jsx
export const useUser = () => {
  return useContext(UserContext);
};
```

Usage:

```jsx
const user = useUser();
```

---

# 🔥 Advanced Interview Concept

## Context + useReducer

Used for global state management.

Example:

```jsx
const StoreContext = createContext();
```

Then:

```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

Very common in large React apps.

---

# 🧠 Easy Way to Remember

```bash
createContext → Provider → useContext
```

OR

```bash
Create → Provide → Consume
```

---

# ✅ Final Summary

`useContext` is a React Hook used with Context API to share data globally between components without prop drilling.

It is commonly used for:

* Authentication
* Theme
* Language
* Cart
* User Data
* Global State

Main flow:

```bash
createContext()
   ↓
Provider
   ↓
useContext()
```
