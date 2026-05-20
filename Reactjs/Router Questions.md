
# 📌 Most Asked Interview Questions

---

## ❓ What is React Router?

### ✅ Answer:

React Router is a library used for client-side routing in React applications.

---

## ❓ Why use React Router?

### ✅ Answer:

React Router enables navigation between pages without reloading the browser.

---

## ❓ Difference Between BrowserRouter and Routes?

### ✅ Answer:

BrowserRouter enables routing, while Routes contains all route definitions.

---

## ❓ What is Dynamic Routing?

### ✅ Answer:

Dynamic routing allows routes to accept dynamic values using URL parameters.


# 📘 React Router — Important Interview Questions

---

# 📌 React Router Kya Hai?

## 🔹 Definition

React Router ek library hai jo React applications me routing/navigation provide karti hai.

Ye different pages/components ke beech navigation karne deta hai bina browser reload kiye.

---

# 📌 Why React Router Use Karte Hai?

Without React Router:

❌ Har page navigation par browser reload hota hai.

With React Router:

✅ Fast navigation
✅ Better user experience
✅ No full page refresh
✅ SPA support

---

# 📌 Example

```jsx id="jlwm1a"
<Route
  path="/about"
  element={<About />}
/>
```

Agar URL `/about` hoga to About component render hoga.

---

# 🎯 Interview Answer

## ❓ What is React Router?

### ✅ Answer:

React Router is a library used for client-side routing in React applications. It enables navigation between different pages/components without refreshing the browser.

---

# 📘 Difference Between SPA vs MPA

---

# 📌 What is SPA?

SPA = Single Page Application

Pure application ek hi HTML page par run hoti hai.

Sirf content dynamically update hota hai.

---

# 📌 Examples

* React
* Angular
* Vue

---

# 📌 SPA Features

✅ Fast navigation
✅ No page reload
✅ Better user experience

---

# 📌 What is MPA?

MPA = Multi Page Application

Har page request par new HTML page load hota hai.

---

# 📌 Examples

* Traditional PHP websites
* Old websites

---

# 📌 MPA Features

✅ Better SEO traditionally
❌ Full page reload
❌ Slower navigation

---

# 📌 SPA vs MPA Difference

| Feature         | SPA         | MPA         |
| --------------- | ----------- | ----------- |
| Page Reload     | ❌ No        | ✅ Yes       |
| Speed           | Fast        | Slower      |
| User Experience | Better      | Traditional |
| Rendering       | Client-side | Server-side |
| Example         | React       | PHP         |

---

# 🎯 Interview Answer

## ❓ Difference Between SPA and MPA?

### ✅ Answer:

SPA loads a single HTML page and updates content dynamically without page refresh, while MPA loads a new page from the server for every request.

---

# 📘 BrowserRouter vs HashRouter

---

# 📌 What is BrowserRouter?

BrowserRouter uses browser history API for clean URLs.

---

# 📌 Example URL

```txt id="jlwm2b"
/about
```

---

# 📌 Features

✅ Clean URLs
✅ SEO friendly
✅ Most commonly used

---

# 📌 What is HashRouter?

HashRouter uses hash (`#`) in URL.

---

# 📌 Example URL

```txt id="jlwm5c"
#/about
```

---

# 📌 Features

✅ Easy server setup
❌ URL not clean
❌ Less SEO friendly

---

# 📌 Difference

| BrowserRouter       | HashRouter       |
| ------------------- | ---------------- |
| Clean URLs          | Uses #           |
| Uses History API    | Uses hash        |
| Better SEO          | Poor SEO         |
| Needs server config | No server config |

---

# 🎯 Interview Answer

## ❓ Difference Between BrowserRouter and HashRouter?

### ✅ Answer:

BrowserRouter uses browser history API and provides clean URLs, while HashRouter uses hash-based URLs and does not require server configuration.

---

# 📘 Routes vs Switch (v5 vs v6)

---

# 📌 What was Switch in React Router v5?

`Switch` rendered only the first matching route.

---

# 📌 Example

```jsx id="jlwm9n"
<Switch>
  <Route path="/" component={Home} />
</Switch>
```

---

# 📌 What is Routes in React Router v6?

In v6:

# 👉 `Switch` replaced by `Routes`

---

# 📌 Example

```jsx id="jlwm4f"
<Routes>
  <Route
    path="/"
    element={<Home />}
  />
</Routes>
```

---

# 📌 Main Differences

| v5             | v6               |
| -------------- | ---------------- |
| Switch         | Routes           |
| component prop | element prop     |
| exact needed   | exact not needed |

---

## ❓ Difference Between Switch and Routes?

### ✅ Answer:

In React Router v5, Switch was used to render the first matching route. In v6, Switch was replaced with Routes which provides better routing behavior and simplified syntax.

---

# 📘 Route Kaise Kaam Karta Hai?

---

# 📌 What is Route?

`Route` URL path aur component ke beech mapping karta hai.

---

# 📌 Example

```jsx id="jlwm1u"
<Route
  path="/about"
  element={<About />}
/>
```

---

# 📌 How it Works?

Agar URL:

```txt id="jlwm7k"
/about
```

hoga to:

```jsx id="jlwm3m"
<About />
```

component render hoga.

---

# 📌 Route Matching

React Router current URL ko route path se compare karta hai.

Match hone par component render hota hai.

---

# 🎯 Interview Answer

## ❓ How does Route work?

### ✅ Answer:

Route matches the current URL with the defined path and renders the corresponding component.

---

# 📘 Link vs NavLink

---

# 📌 What is Link?

`Link` navigation ke liye use hota hai bina page reload ke.

---

# 📌 Example

```jsx id="jlwm8s"
<Link to="/about">
  About
</Link>
```

---

# 📌 What is NavLink?

`NavLink` bhi navigation ke liye use hota hai but active styling support deta hai.

---

# 📌 Example

```jsx id="jlwm5x"
<NavLink to="/about">
  About
</NavLink>
```

---

# 📌 Active Class Example

```jsx id="jlwm0h"
<NavLink
  to="/about"
  className={({ isActive }) =>
    isActive ? "active" : ""
  }
>
  About
</NavLink>
```

---

# 📌 Difference

| Link              | NavLink                     |
| ----------------- | --------------------------- |
| Simple navigation | Navigation + active styling |
| No active state   | Supports active state       |

---

# 🎯 Interview Answer

## ❓ Difference Between Link and NavLink?

### ✅ Answer:

Link is used for navigation, while NavLink provides additional active route styling features.

---

# 📘 useNavigate Kya Hai?

---

# 📌 Definition

`useNavigate` ek hook hai jo programmatic navigation ke liye use hota hai.

---

# 📌 Example

```jsx id="jlwm2x"
import {
  useNavigate
} from "react-router-dom";

function Home() {
  const navigate = useNavigate();

  return (
    <button
      onClick={() =>
        navigate("/about")
      }
    >
      Go
    </button>
  );
}
```

---

# 📌 Use Cases

✅ Login redirect
✅ Form submit redirect
✅ Conditional navigation

---

# 🎯 Interview Answer

## ❓ What is useNavigate?

### ✅ Answer:

useNavigate is a React Router hook used for programmatic navigation between routes.

---

# 📘 useParams Kya Karta Hai?

---

# 📌 Definition

`useParams` URL ke dynamic parameters ko access karta hai.

---

# 📌 Example Route

```jsx id="jlwm6p"
<Route
  path="/user/:id"
  element={<User />}
/>
```

---

# 📌 URL

```txt id="jlwm9y"
/user/10
```

---

# 📌 Access Parameter

```jsx id="jlwm4q"
import {
  useParams
} from "react-router-dom";

function User() {
  const { id } = useParams();

  return <h1>{id}</h1>;
}
```

---

# 📌 Output

```txt id="jlwm1j"
10
```

---

# 🎯 Interview Answer

## ❓ What does useParams do?

### ✅ Answer:

useParams is used to access dynamic route parameters from the URL.

---

# 📘 useLocation Ka Use Kya Hai?

---

# 📌 Definition

`useLocation` current URL aur route information provide karta hai.

---

# 📌 Example

```jsx id="jlwm7v"
import {
  useLocation
} from "react-router-dom";

function App() {
  const location = useLocation();

  console.log(location.pathname);
}
```

---

# 📌 Useful Properties

| Property | Meaning          |
| -------- | ---------------- |
| pathname | Current URL path |
| search   | Query parameters |
| hash     | URL hash         |

---

# 📌 Use Cases

✅ Current page detection
✅ Analytics
✅ Conditional rendering

---

# 🎯 Interview Answer

## ❓ What is useLocation used for?

### ✅ Answer:

useLocation is used to get information about the current URL and route in React Router.


# 📘 Advanced React Router Interview Notes

---

# 📌 Nested Routing Kaise Implement Karte Ho?

## 🔹 What is Nested Routing?

Nested routing means creating routes inside another route.

Used for layouts like:

* Dashboard
* Admin panel
* Profile sections

---

# 📌 Why Nested Routing?

Suppose dashboard has:

* Profile
* Settings
* Orders

Instead of separate layouts, we use nested routes.

---

# 📌 Example

## App.js

```jsx id="jlwm1n"
import {
  Routes,
  Route
} from "react-router-dom";

import Dashboard from "./Dashboard";
import Profile from "./Profile";
import Settings from "./Settings";

function App() {
  return (
    <Routes>
      <Route
        path="/dashboard"
        element={<Dashboard />}
      >
        <Route
          path="profile"
          element={<Profile />}
        />

        <Route
          path="settings"
          element={<Settings />}
        />
      </Route>
    </Routes>
  );
}

export default App;
```

---

# 📌 Dashboard Component

```jsx id="jlwm6x"
import { Outlet } from "react-router-dom";

function Dashboard() {
  return (
    <div>
      <h1>Dashboard</h1>

      <Outlet />
    </div>
  );
}

export default Dashboard;
```

---

# 📌 What is Outlet?

`Outlet` renders child routes inside parent component.

---

# 📌 URLs

| URL                   | Component |
| --------------------- | --------- |
| `/dashboard/profile`  | Profile   |
| `/dashboard/settings` | Settings  |

---

# 🎯 Interview Answer

## ❓ How to implement Nested Routing?

### ✅ Answer:

Nested routing is implemented by defining child routes inside parent routes and rendering them using the `Outlet` component.

---

# 📘 Dynamic Routing Kya Hota Hai?

---

# 📌 Definition

Dynamic routing allows routes to accept dynamic values from the URL.

---

# 📌 Example URL

```txt id="jlwm3r"
/product/10
/product/20
```

Here:

```txt id="jlwm8k"
10, 20
```

are dynamic values.

---

# 📌 Route Setup

```jsx id="jlwm5t"
<Route
  path="/product/:id"
  element={<Product />}
/>
```

---

# 📌 Access Parameter

```jsx id="jlwm0m"
import {
  useParams
} from "react-router-dom";

function Product() {
  const { id } = useParams();

  return <h1>{id}</h1>;
}
```

---

# 📌 Output

For:

```txt id="jlwm2w"
/product/10
```

Output:

```txt id="jlwm7d"
10
```

---

# 🎯 Interview Answer

## ❓ What is Dynamic Routing?

### ✅ Answer:

Dynamic routing allows routes to receive dynamic values from the URL using route parameters.

---

# 📘 Layout-Based Routing Kya Hai?

---

# 📌 Definition

Layout-based routing means sharing a common layout between multiple pages.

---

# 📌 Example

Common UI:

✅ Navbar
✅ Sidebar
✅ Footer

shared across pages.

---

# 📌 Layout Example

```jsx id="jlwm4v"
function Layout() {
  return (
    <>
      <Navbar />

      <Outlet />

      <Footer />
    </>
  );
}
```

---

# 📌 Routes

```jsx id="jlwm9b"
<Route
  path="/"
  element={<Layout />}
>
  <Route
    index
    element={<Home />}
  />

  <Route
    path="about"
    element={<About />}
  />
</Route>
```

---

# 📌 Benefit

No need to repeat:

```txt id="’winijlwm"
Navbar/Footer
```

on every page.

---

# 🎯 Interview Answer

## ❓ What is Layout-Based Routing?

### ✅ Answer:

Layout-based routing is a routing pattern where multiple pages share a common layout such as navbar, sidebar, or footer using parent routes and Outlet.

---

# 📘 Protected Routes Kaise Banate Ho?

---

# 📌 What are Protected Routes?

Protected routes restrict unauthorized users from accessing pages.

---

# 📌 Example

```jsx id="jlwm1c"
import {
  Navigate
} from "react-router-dom";

function ProtectedRoute({
  children
}) {
  const isAuth = true;

  if (!isAuth) {
    return (
      <Navigate to="/login" />
    );
  }

  return children;
}

export default ProtectedRoute;
```

---

# 📌 Usage

```jsx id="jlwm6n"
<Route
  path="/dashboard"
  element={
    <ProtectedRoute>
      <Dashboard />
    </ProtectedRoute>
  }
/>
```

---

# 📌 How it Works?

If user logged in:

✅ Dashboard render

Else:

✅ Redirect to login page

---

# 🎯 Interview Answer

## ❓ How to create Protected Routes?

### ✅ Answer:

Protected routes are created by checking authentication before rendering a route and redirecting unauthorized users using the Navigate component.

---

# 📘 Redirect Kaise Karte Ho React Router v6 Me?

---

# 📌 React Router v6 Redirect

React Router v6 uses:

# 👉 Navigate component

---

# 📌 Example

```jsx id="jlwm3g"
import {
  Navigate
} from "react-router-dom";

<Navigate to="/login" />
```

---

# 📌 Programmatic Redirect

```jsx id="jlwm8y"
const navigate = useNavigate();

navigate("/home");
```

---

# 📌 Common Use Cases

✅ Login success redirect
✅ Unauthorized redirect
✅ Form submit redirect

---

# 🎯 Interview Answer

## ❓ How to redirect in React Router v6?

### ✅ Answer:

React Router v6 uses the `Navigate` component and `useNavigate` hook for redirection.

---

# 📘 Route Params vs Query Params Difference

---

# 📌 Route Params

Dynamic values inside URL path.

---

# 📌 Example

```txt id="jlwm5u"
/product/10
```

---

# 📌 Access Using

```jsx id="jlwm0p"
useParams()
```

---

# 📌 Query Params

Extra information added after `?`

---

# 📌 Example

```txt id="jlwm2a"
/products?category=mobile
```

---

# 📌 Access Using

```jsx id="jlwm7x"
useSearchParams()
```

---

# 📌 Difference Table

| Route Params      | Query Params       |
| ----------------- | ------------------ |
| Part of URL path  | Added after `?`    |
| Mandatory usually | Optional usually   |
| useParams         | useSearchParams    |
| `/product/10`     | `?category=mobile` |

---

# 🎯 Interview Answer

## ❓ Difference Between Route Params and Query Params?

### ✅ Answer:

Route params are dynamic values inside the URL path, while query params are optional values added after `?` in the URL.

---

# 📘 Lazy Loading Routes Kaise Karte Ho?

---

# 📌 What is Lazy Loading?

Lazy loading loads components only when needed.

---

# 📌 Why Use Lazy Loading?

✅ Faster initial load
✅ Smaller bundle size
✅ Better performance

---

# 📌 Example

```jsx id="’winijlwm8"
const Product = React.lazy(() =>
  import("./Product")
);
```

---

# 📌 Complete Example

```jsx id="jlwm4h"
import React, {
  lazy,
  Suspense
} from "react";

const Product = lazy(() =>
  import("./Product")
);

function App() {
  return (
    <Suspense
      fallback={<h1>Loading...</h1>}
    >
      <Product />
    </Suspense>
  );
}

export default App;
```

---

# 📌 How it Works?

Initially:

❌ Product component not loaded

When needed:

✅ Component loads dynamically

---

# 📌 What is Suspense?

Suspense shows fallback UI while component loads.

---

# 🎯 Interview Answer

## ❓ How to implement Lazy Loading in React Router?

### ✅ Answer:

Lazy loading is implemented using `React.lazy()` and `Suspense` to load route components dynamically only when required.


# 📘 Advanced React Router Interview Notes

---

# 📌 Route Guards Kaise Implement Karte Ho?

## 🔹 What are Route Guards?

Route guards are used to protect routes from unauthorized access.

They check conditions before rendering a route.

---

# 📌 Common Checks

✅ User logged in or not
✅ User role
✅ Permissions

---

# 📌 Example

```jsx id="jlwm1f"
import {
  Navigate
} from "react-router-dom";

function ProtectedRoute({
  children
}) {
  const isAuthenticated = true;

  return isAuthenticated
    ? children
    : <Navigate to="/login" />;
}
```

---

# 📌 Usage

```jsx id="jlwm6d"
<Route
  path="/dashboard"
  element={
    <ProtectedRoute>
      <Dashboard />
    </ProtectedRoute>
  }
/>
```

---

# 📌 How it Works?

If authenticated:

✅ Dashboard render

Else:

✅ Redirect to login

---

# 🎯 Interview Answer

## ❓ How to implement Route Guards?

### ✅ Answer:

Route guards are implemented by checking authentication or permissions before rendering a route and redirecting unauthorized users using Navigate.

---

# 📘 Authentication Flow with Routing Kaise Handle Karte Ho?

---

# 📌 Basic Authentication Flow

---

# 🔥 Step 1

User logs in.

---

# 🔥 Step 2

Store authentication token:

```txt id="jlwm8n"
localStorage / cookies / state
```

---

# 🔥 Step 3

Protect private routes.

---

# 🔥 Step 4

If token exists:

✅ Allow access

Else:

❌ Redirect to login

---

# 📌 Example Flow

```txt id="jlwm3r"
Login → Token Save →
Protected Route Check →
Allow / Redirect
```

---

# 📌 Example

```jsx id="’winiijlwm"
const token =
  localStorage.getItem("token");
```

---

# 📌 Protected Route

```jsx id="jlwm9p"
function PrivateRoute({
  children
}) {
  const token =
    localStorage.getItem("token");

  return token
    ? children
    : <Navigate to="/login" />;
}
```

---

# 📌 Logout Flow

```jsx id="’winiijlwm7"
localStorage.removeItem("token");
navigate("/login");
```

---

# 🎯 Interview Answer

## ❓ How to handle Authentication Flow with Routing?

### ✅ Answer:

Authentication flow is handled by storing login tokens and checking authentication before rendering protected routes. Unauthorized users are redirected to the login page.

---

# 📘 Role-Based Routing Kaise Banate Ho?

---

# 📌 What is Role-Based Routing?

Different users get different route access based on role.

---

# 📌 Example Roles

* Admin
* User
* Manager

---

# 📌 Example

```jsx id="’winiijlwm2"
function RoleBasedRoute({
  children,
  role
}) {
  const userRole = "admin";

  if (userRole !== role) {
    return <Navigate to="/" />;
  }

  return children;
}
```

---

# 📌 Usage

```jsx id="’winiijlwm5"
<Route
  path="/admin"
  element={
    <RoleBasedRoute role="admin">
      <Admin />
    </RoleBasedRoute>
  }
/>
```

---

# 📌 How it Works?

If role matches:

✅ Route access allowed

Else:

❌ Redirect

---

# 🎯 Interview Answer

## ❓ How to implement Role-Based Routing?

### ✅ Answer:

Role-based routing is implemented by checking the user's role before rendering a route and restricting access to unauthorized roles.

---

# 📘 Code Splitting Ka Importance Kya Hai Routing Me?

---

# 📌 What is Code Splitting?

Code splitting divides large bundles into smaller chunks.

---

# 📌 Why Important in Routing?

Without code splitting:

❌ Entire app loads initially

With code splitting:

✅ Only required route component loads

---

# 📌 Example

```jsx id="’winiijlwm0"
const Product = React.lazy(() =>
  import("./Product")
);
```

---

# 📌 Benefits

✅ Faster initial load
✅ Smaller bundle size
✅ Better performance
✅ Faster routing

---

# 📌 With Suspense

```jsx id="’winiijlwm9"
<Suspense fallback={<h1>Loading...</h1>}>
  <Product />
</Suspense>
```

---

# 🎯 Interview Answer

## ❓ Why is Code Splitting important in Routing?

### ✅ Answer:

Code splitting improves routing performance by loading route components only when needed, reducing initial bundle size and improving application speed.

---

# 📘 MemoryRouter Kab Use Karte Ho?

---

# 📌 What is MemoryRouter?

MemoryRouter stores routing history in memory instead of browser URL.

---

# 📌 Main Use Cases

✅ Testing
✅ React Native
✅ Non-browser environments

---

# 📌 Important Point

It does NOT update browser URL.

---

# 📌 Example

```jsx id="’winiijlwm6"
import {
  MemoryRouter
} from "react-router-dom";

<MemoryRouter>
  <App />
</MemoryRouter>
```

---

# 🎯 Interview Answer

## ❓ When is MemoryRouter used?

### ✅ Answer:

MemoryRouter is mainly used in testing and non-browser environments where browser history is unavailable.

---

# 📘 SSR Me Routing Kaise Handle Hota Hai?

---

# 📌 What is SSR?

SSR = Server Side Rendering

Pages render on server before reaching browser.

---

# 📌 Why Special Routing Needed?

BrowserRouter depends on browser APIs.

Server environment me browser available nahi hota.

---

# 📌 SSR Uses

```txt id="’winiijlwm3"
StaticRouter
```

---

# 📌 Example

```jsx id="’winiijlwm8"
import {
  StaticRouter
} from "react-router-dom/server";

<StaticRouter location={req.url}>
  <App />
</StaticRouter>
```

---

# 📌 Benefits

✅ Better SEO
✅ Faster first paint
✅ Better performance

---

# 🎯 Interview Answer

## ❓ How is routing handled in SSR?

### ✅ Answer:

In SSR, routing is handled using StaticRouter because BrowserRouter depends on browser APIs that are unavailable on the server.

---

# 📘 404 Page Kaise Implement Karte Ho?

---

# 📌 Why 404 Page Needed?

When user enters invalid route:

✅ Show "Page Not Found"

---

# 📌 Example

```jsx id="’winiijlwm4"
<Route
  path="*"
  element={<NotFound />}
/>
```

---

# 📌 NotFound Component

```jsx id="’winiijlwm1"
function NotFound() {
  return <h1>404 Page Not Found</h1>;
}
```

---

# 📌 How it Works?

```txt id="’winiijlwmq"
* matches all invalid routes
```

---

# 🎯 Interview Answer

## ❓ How to implement 404 page in React Router?

### ✅ Answer:

A 404 page is implemented using `path="*"` which catches all unmatched routes and renders a Not Found component.


# 📘 replace: true Navigation Me Kya Karta Hai?

---

# 📌 Definition

`replace: true` current history entry ko replace karta hai instead of adding a new entry in browser history.

---

# 📌 Normal Navigation

```jsx id="’winiijlwm"
navigate("/dashboard");
```

---

# 📌 History Stack

```txt id="’winiijlwm7"
/login → /dashboard
```

Back button dabane par:

❌ User login page par wapas ja sakta hai.

---

# 📘 Using replace: true

```jsx id="’winiijlwm2"
navigate("/dashboard", {
  replace: true
});
```

---

# 📌 What Happens?

Current page history se replace ho jata hai.

---

# 📌 Result

```txt id="’winiijlwm5"
/dashboard
```

Back button se:

❌ Login page nahi open hoga.

---

# 📌 Common Use Cases

✅ Login redirect
✅ Logout redirect
✅ Payment success page

---

# 🎯 Interview Answer

## ❓ What does replace: true do in navigation?

### ✅ Answer:

`replace: true` replaces the current history entry instead of adding a new one, preventing users from going back to the previous page.

---
# 📌 What is Immutable Update?

Redux/React me original state directly modify nahi karte.

Instead:

# 👉 New copy create karke update karte hain.

---

# ❌ Wrong Way (Mutation)

```js id="’winiijlwm0"
state.count = 5;
```

Directly state modify ho raha hai.

---

# ✅ Correct Immutable Update

```js id="’winiijlwm8"
return {
  ...state,
  count: 5
};
```

---

# 📌 Array Immutable Update

## ✅ Add Item

```js id="’winiijlwm3"
return {
  ...state,
  users: [
    ...state.users,
    newUser
  ]
};
```

---

# 📌 Update Object

```js id="’winiijlwm6"
return {
  ...state,
  user: {
    ...state.user,
    name: "Krupa"
  }
};
```

---

# 📘 Why Immutable Updates Important?

✅ Predictable state
✅ React re-render detection
✅ Better debugging
✅ Performance optimization

---

# 📘 Important Point in Redux Toolkit

Redux Toolkit internally:

# 👉 Immer

use karta hai.

Isliye ye syntax allowed hota hai:

```js id="’winiijlwm1"
state.count += 1;
```

Lekin internally immutable update hi hota hai.

---

# 🎯 Interview Answer

## ❓ How do you perform immutable updates?

### ✅ Answer:

Immutable updates are done by creating new copies of objects or arrays using spread operators instead of directly modifying the original state.


