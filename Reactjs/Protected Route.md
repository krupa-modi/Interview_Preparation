# Protected Route in React

## What is a Protected Route?

A Protected Route is a route that can only be accessed by authenticated (logged-in) users.

If a user is not authenticated, they are redirected to another page, usually the Login page.

### Example

✅ Logged-in User → Can access Dashboard

❌ Not Logged-in User → Redirected to Login Page

---

# Why Do We Need Protected Routes?

Without Protected Routes, anyone can access private pages by typing the URL directly.

For example:

/dashboard
/profile
/settings
/admin

These pages should only be accessible after login.

Protected Routes help secure the frontend navigation.

---

# When Should We Use Protected Routes?

Use Protected Routes for:

- Dashboard Page
- User Profile
- Settings Page
- Order History
- Admin Panel
- Employee Portal
- Any page requiring authentication

Example:

```jsx
/dashboard
/profile
/admin
```

These routes should be protected.

---

# How Protected Route Works

Step 1:
Check if user is authenticated.

Step 2:
If authenticated → Render requested page.

Step 3:
If not authenticated → Redirect to Login Page.

Flow:

```text
User Requests Dashboard
        |
        v
Check Authentication
        |
   +----+----+
   |         |
  Yes       No
   |         |
   v         v
Dashboard   Login Page
```

---

# Basic Protected Route Example

## ProtectedRoute.jsx

```jsx
import { Navigate } from "react-router-dom";

function ProtectedRoute({ children }) {
  const isAuth = true;

  if (!isAuth) {
    return <Navigate to="/login" />;
  }

  return children;
}

export default ProtectedRoute;
```

---

# Using Protected Route

```jsx
import { Routes, Route } from "react-router-dom";
import ProtectedRoute from "./ProtectedRoute";
import Dashboard from "./Dashboard";

function App() {
  return (
    <Routes>
      <Route
        path="/dashboard"
        element={
          <ProtectedRoute>
            <Dashboard />
          </ProtectedRoute>
        }
      />
    </Routes>
  );
}

export default App;
```

---

# Real Project Example

Usually authentication is checked using:

- JWT Token
- Access Token
- User Data
- Redux State
- Context API

Example:

```jsx
import { Navigate } from "react-router-dom";

function ProtectedRoute({ children }) {
  const token = localStorage.getItem("token");

  return token ? children : <Navigate to="/login" />;
}

export default ProtectedRoute;
```

---

# Using JWT Token

After login:

```js
localStorage.setItem("token", response.data.token);
```

Protected Route:

```jsx
const token = localStorage.getItem("token");

if (!token) {
  return <Navigate to="/login" />;
}

return children;
```

---

# Role Based Protected Route

Sometimes only Admin users should access a page.

Example:

```jsx
import { Navigate } from "react-router-dom";

function AdminRoute({ children }) {
  const role = localStorage.getItem("role");

  if (role !== "admin") {
    return <Navigate to="/unauthorized" />;
  }

  return children;
}
```

Usage:

```jsx
<Route
  path="/admin"
  element={
    <AdminRoute>
      <AdminPanel />
    </AdminRoute>
  }
/>
```

---

# React Router v6 Protected Route Pattern

```jsx
import { Navigate } from "react-router-dom";

const ProtectedRoute = ({ children }) => {
  const token = localStorage.getItem("token");

  return token ? children : <Navigate to="/login" replace />;
};

export default ProtectedRoute;
```

The `replace` prop prevents users from going back to the protected page using the browser back button.

---

# Interview Questions

## Q1. What is a Protected Route?

A Protected Route is a route that allows access only to authenticated users and redirects unauthenticated users to the login page.

---

## Q2. Why do we use Protected Routes?

To prevent unauthorized users from accessing private pages like Dashboard, Profile, Settings, and Admin Panel.

---

## Q3. How do you implement Protected Routes in React?

By creating a wrapper component that checks authentication status and either renders children or redirects using Navigate.

---

## Q4. Which React Router component is used for redirection?

```jsx
<Navigate />
```

Example:

```jsx
<Navigate to="/login" />
```

---

## Q5. Where is authentication data usually stored?

- localStorage
- sessionStorage
- Redux Store
- Context API
- Cookies

---

## Q6. Can we create role-based Protected Routes?

Yes.

Example:

```jsx
if (user.role !== "admin") {
  return <Navigate to="/unauthorized" />;
}
```

---

# Summary

Protected Route = Authentication Check + Conditional Rendering

```jsx
return token
  ? children
  : <Navigate to="/login" />;
```

This is one of the most common React Router interview questions and is used in almost every production React application.
````

This level of explanation is usually enough for React Developer interviews from beginner to 3+ years experience.
