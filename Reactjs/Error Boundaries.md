# 📌 What are Error Boundaries?

## 🔹 Definition
Error Boundaries are React components used to catch JavaScript errors in child components during rendering.

They prevent the entire application from crashing.

Error Boundary ek React component hota hai jo apne child components me aane wali JavaScript errors ko catch karta hai aur fallback UI show karta hai.

Simple words me:

👉 Agar child component crash ho jaye 👉 To pura app crash na ho 👉 Sirf ek safe UI show ho

---

# 📌 Simple Meaning

If one component crashes:

❌ Without Error Boundary → Whole app may crash
✅ With Error Boundary → Show fallback UI instead

---

🔥 Problem kya thi?
React 16 se pehle:

Agar ek component me error aa gaya
To pura React app crash ho jata tha

React 16 ke baad:

👉 Error Boundaries introduce hue

⚠️ Important:

Error Boundary sirf Class Component me ban sakta hai

# 📌 Why Error Boundaries are Needed?

In large applications, runtime errors can break the UI.

Error Boundaries help:

✅ Catch errors gracefully
✅ Show fallback UI
✅ Improve user experience
✅ Prevent full app crash

---

# 📌 Example Without Error Boundary

```jsx id="jlwm9f"
function BuggyComponent() {
  throw new Error("App Crashed");
}
```

Entire React app may crash.

---

# 📌 Error Boundary Example

```jsx id="jlwm1d"
import React from "react";

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      hasError: false
    };
  }

  static getDerivedStateFromError(error) {
    return {
      hasError: true
    };
  }

  componentDidCatch(error, info) {
    console.log("Error:", error);
    console.log("Info:", info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong</h1>;
    }

    return this.props.children;
  }
}

export default ErrorBoundary;
```

---

# 📌 Usage

```jsx id="jlwm4x"
<ErrorBoundary>
  <BuggyComponent />
</ErrorBoundary>
```

---

# 📌 Lifecycle Methods Used in Error Boundaries

React Error Boundaries use 2 lifecycle methods:

---

# 🔥 1️⃣ getDerivedStateFromError()

## 📌 Purpose

Updates state when error occurs.

Used for showing fallback UI.

---

## ✅ Example

```jsx id="jlwm2p"
static getDerivedStateFromError(error) {
  return {
    hasError: true
  };
}
```

---

# 🔥 2️⃣ componentDidCatch()

## 📌 Purpose

Used for:

* Logging errors
* Reporting errors
* Debugging

---

## ✅ Example

```jsx id="jlwm6q"
componentDidCatch(error, info) {
  console.log(error);
}
```

---

# 📌 What Errors Do Error Boundaries Catch?

✅ Errors during rendering
✅ Errors in lifecycle methods
✅ Errors in child components

---

# 📌 What Errors Do They NOT Catch?

❌ Event handlers
❌ Async code (`setTimeout`, API calls)
❌ Server-side rendering errors
❌ Errors inside Error Boundary itself

---

# 📌 Important Point

Error Boundaries work only in:

# 👉 Class Components

Not directly in functional components.

---

# 📌 Modern React

Functional components usually use:

* try-catch
* react-error-boundary library

for error handling.

---

# 🎯 Interview Answers

---

# ❓ What are Error Boundaries?

### ✅ Answer:

Error Boundaries are React class components that catch JavaScript errors in child components during rendering and display fallback UI instead of crashing the entire application.

---

# ❓ Which lifecycle methods are used in Error Boundaries?

### ✅ Answer:

Error Boundaries use:

* `static getDerivedStateFromError()`
* `componentDidCatch()`

to handle errors and show fallback UI.

---

# ❓ Why are Error Boundaries used?

### ✅ Answer:

Error Boundaries improve application stability by preventing the entire React app from crashing when a component throws an error.

---

