# 📘 HOC (Higher Order Component) in React

---
# 📌 What is HOC?

## 🔹 Definition

HOC stands for:

# 👉 Higher Order Component

A Higher Order Component is a function that takes a component as input and returns a new enhanced component.
* higher-order component is a function that takes a component and returns a new component.
* Higher-order components are not commonly used in modern React code. 

---

# 📌 Simple Meaning

HOC is used to reuse component logic.

Instead of repeating same logic in multiple components, we wrap components inside an HOC.

---

# 📌 Syntax

```jsx id="jlwmx9"
const EnhancedComponent = HOC(OriginalComponent);
```

---

# 📌 Real Life Analogy

Suppose:

* Mobile = Component
* Mobile Cover = HOC

Cover adds extra protection/features without changing original mobile.

Similarly HOC adds extra functionality to components.

---

# 📌 Why HOC is Used?

HOCs help with:

✅ Code Reusability
✅ Shared Logic
✅ Cleaner Code
✅ Separation of Concerns

---

# 📌 Common Use Cases of HOC

| Use Case       | Example                   |
| -------------- | ------------------------- |
| Authentication | Protected routes          |
| Loading Logic  | Loader wrapper            |
| Logging        | Track component rendering |
| Permissions    | Role-based access         |
| Data Fetching  | Shared API logic          |

---

# 📌 Basic Example of HOC

---

# 🔥 Step 1 — Normal Component

```jsx id="jlwmv2"
function User() {
  return <h1>User Component</h1>;
}

export default User;
```

---

# 🔥 Step 2 — Create HOC

```jsx id="jlwmc5"
function withMessage(WrappedComponent) {
  return function EnhancedComponent() {
    return (
      <div>
        <h2>Welcome User</h2>

        <WrappedComponent />
      </div>
    );
  };
}

export default withMessage;
```

🔥 First Function Purpose
function withMessage(WrappedComponent)

This function:

✅ Receives the original component
✅ Adds extra functionality
✅ Returns a new component

🔥 Second Function Purpose
function EnhancedComponent()

This is the actual React component that gets rendered on screen.

React can render only components/functions that return JSX.

So HOC must return a component.


# 🔥 Step 3 — Wrap Component

```jsx id="jlwmr4"
import User from "./User";
import withMessage from "./withMessage";

const EnhancedUser = withMessage(User);

export default EnhancedUser;
```

---

# 📌 Output

```txt id="jlwm2g"
Welcome User
User Component
```

---

# 📌 How HOC Works?

---

# 🔥 Flow

```txt id="jlwm1x"
Component → HOC → Enhanced Component
```

---

# 📌 Important Point

HOC does NOT modify original component.

It returns a new enhanced component.

---

# 📌 Real Interview Example — Authentication HOC

---

# 🔥 Problem

Suppose many pages need login protection.

Without HOC:

❌ Repeating auth logic everywhere

---

# ✅ Solution Using HOC

---

## withAuth.js

```jsx id="jlwm4m"
function withAuth(WrappedComponent) {
  return function AuthComponent(props) {
    const isLoggedIn = true;

    if (!isLoggedIn) {
      return <h1>Please Login</h1>;
    }

    return <WrappedComponent {...props} />;
  };
}

export default withAuth;
```

---

## Dashboard.jsx

```jsx id="jlwmq7"
function Dashboard() {
  return <h1>Dashboard</h1>;
}

export default Dashboard;
```

---

## Protected Dashboard

```jsx id="jlwm3k"
import Dashboard from "./Dashboard";
import withAuth from "./withAuth";

export default withAuth(Dashboard);
```

---

# 📌 Benefit

Now authentication logic is reusable.

No need to repeat code.

---

# 📌 HOC with Props

HOCs can also pass props.

---

# ✅ Example

```jsx id="jlwmw1"
function withUser(Component) {
  return function(props) {
    return (
      <Component
        {...props}
        name="Krupa"
      />
    );
  };
}
```

---

# 📌 HOC vs Normal Component

| Normal Component | HOC                 |
| ---------------- | ------------------- |
| Renders UI       | Enhances components |
| Used directly    | Wraps components    |
| UI focused       | Logic reuse focused |

---

# 📌 HOC vs Custom Hooks

---

# 🔥 Modern React

Nowadays developers often prefer:

# 👉 Custom Hooks

instead of HOCs.

---

# 📌 Why Hooks Replaced Many HOCs?

Hooks provide:

✅ Simpler code
✅ Better readability
✅ Less nesting
✅ Easier logic sharing

---

# 📌 Example

Instead of:

```jsx id="jlwm0f"
withAuth(Component)
```

Modern React often uses:

```jsx id="jlwm8u"
useAuth()
```

---

# 📌 Disadvantages of HOC

❌ Wrapper nesting ("Wrapper Hell")
❌ Hard debugging
❌ Props collision possible
❌ Complex hierarchy

---

# 📌 Popular Real HOCs

Older React libraries used HOCs heavily.

Examples:

* `connect()` from Redux
* `withRouter()`
* `memo()`

---

# 📌 React.memo as HOC

```jsx id="jlwm6t"
export default React.memo(MyComponent);
```

It prevents unnecessary re-renders.

---

# 🎯 Interview Answers

---

# ❓ What is HOC in React?

### ✅ Answer:

A Higher Order Component (HOC) is a function that takes a component as input and returns a new enhanced component with additional functionality.

---

# ❓ Why use HOC?

### ✅ Answer:

HOCs are used for code reuse, shared logic, authentication, logging, permissions, and other cross-cutting concerns in React applications.

---

# ❓ Does HOC modify original component?

### ✅ Answer:

No. HOC does not modify the original component. It returns a new enhanced component.

---

# ❓ Difference Between HOC and Hooks?

### ✅ Answer:

HOCs wrap components to reuse logic, while Hooks reuse logic directly inside functional components. Modern React generally prefers Hooks because they are simpler and cleaner.

---
### HOC Kya Hai?

> A Higher Order Component is a function that takes a component as input and returns a new component with additional functionality.

---

# Easy Interview Example: withAuth

### HOC

```jsx id="q35e3x"
function withAuth(WrappedComponent) {
  return function EnhancedComponent(props) {
    const isLoggedIn = true;

    if (!isLoggedIn) {
      return <h2>Please Login First</h2>;
    }

    return <WrappedComponent {...props} />;
  };
}
```

---

### Dashboard Component

```jsx id="q1e7fr"
function Dashboard() {
  return <h1>Welcome to Dashboard</h1>;
}
```

---

### Enhanced Component

```jsx id="krv4rz"
const ProtectedDashboard = withAuth(Dashboard);
```

---

### Usage

```jsx id="l7px26"
function App() {
  return <ProtectedDashboard />;
}
```

---

## Flow

```text
Dashboard
    ↓
withAuth(Dashboard)
    ↓
ProtectedDashboard
    ↓
Extra Authentication Logic Added
```