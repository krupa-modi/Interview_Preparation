# 📘 React Router — Complete Interview Notes
# 📌 What is React Router?

React Router is a library used for navigation in React applications.

It allows switching between pages/components without refreshing the browser.

---

# 📌 Why React Router is Needed?

React is a Single Page Application (SPA).

Without React Router:

❌ Full page reload happens

With React Router:

✅ Fast navigation
✅ Better user experience
✅ No page refresh

---

# 📌 Install React Router

```bash id="jlwm1q"
npm install react-router-dom
```

---

# 📘 BrowserRouter

---

# 📌 What is BrowserRouter?

`BrowserRouter` enables routing in React application.

It uses browser history API.

---

# 📌 Setup

```jsx id="jlwm5n"
import ReactDOM from "react-dom/client";
import App from "./App";

import {
  BrowserRouter
} from "react-router-dom";

const root = ReactDOM.createRoot(
  document.getElementById("root")
);

root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

---

# 🎯 Interview Answer

## ❓ What is BrowserRouter?

### ✅ Answer:

BrowserRouter is a React Router component that enables routing using the browser history API.

---

# 📘 Routes and Route

---

# 📌 What is Routes?

`Routes` is a container for all route definitions.

---

# 📌 What is Route?

`Route` defines path and component mapping.

---

# 📌 Example

```jsx id="jlwm8m"
import {
  Routes,
  Route
} from "react-router-dom";

import Home from "./Home";
import About from "./About";

function App() {
  return (
    <Routes>
      <Route
        path="/"
        element={<Home />}
      />

      <Route
        path="/about"
        element={<About />}
      />
    </Routes>
  );
}
```

---

# 📌 How it Works?

| URL      | Component |
| -------- | --------- |
| `/`      | Home      |
| `/about` | About     |

---

# 🎯 Interview Answer

## ❓ Difference Between Routes and Route?

### ✅ Answer:

`Routes` is used to group multiple routes, while `Route` defines individual path-to-component mapping.

---

# 📘 Link

---

# 📌 What is Link?

`Link` is used for navigation without page refresh.

---

# 📌 Example

```jsx id="jlwm2z"
import { Link } from "react-router-dom";

<Link to="/">Home</Link>

<Link to="/about">
  About
</Link>
```

---

# 📌 Why Not Use anchor `<a>` Tag?

`<a>` causes full page reload.

`Link` provides SPA navigation.

---

# 🎯 Interview Answer

## ❓ What is Link in React Router?

### ✅ Answer:

Link is used for client-side navigation in React applications without reloading the page.

---

# 📘 NavLink

---

# 📌 What is NavLink?

`NavLink` works like `Link` but provides active styling.

---

# 📌 Example

```jsx id="jlwm7r"
import {
  NavLink
} from "react-router-dom";

<NavLink to="/about">
  About
</NavLink>
```

---

# 📌 Active Class Example

```jsx id="jlwm4c"
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

# 🎯 Interview Answer

## ❓ Difference Between Link and NavLink?

### ✅ Answer:

NavLink provides active route styling, while Link is only used for navigation.

---

# 📘 useNavigate

---

# 📌 What is useNavigate?

`useNavigate` is used for programmatic navigation.

---

# 📌 Example

```jsx id="jlwm0v"
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

# 📘 Dynamic Routing

---

# 📌 What is Dynamic Routing?

Dynamic routing allows passing dynamic values in URL.

---

# 📌 Example

```txt id="jlwm9d"
/user/1
/user/2
```

---

# 📌 Route Setup

```jsx id="jlwm6b"
<Route
  path="/user/:id"
  element={<User />}
/>
```

---

# 📌 useParams Hook

```jsx id="jlwm1h"
import {
  useParams
} from "react-router-dom";

function User() {
  const { id } = useParams();

  return <h1>{id}</h1>;
}
```

---

# 🎯 Interview Answer

## ❓ What is useParams?

### ✅ Answer:

useParams is used to access dynamic route parameters from the URL.

---

# 📘 Nested Routing

---

# 📌 What is Nested Routing?

Route inside another route is called nested routing.

---

# 📌 Example

```jsx id="jlwm5k"
<Route
  path="/dashboard"
  element={<Dashboard />}
>
  <Route
    path="profile"
    element={<Profile />}
  />
</Route>
```

---

# 📌 Outlet

`Outlet` renders child routes.

---

# 📌 Example

```jsx id="jlwm2s"
import { Outlet } from "react-router-dom";

function Dashboard() {
  return (
    <>
      <h1>Dashboard</h1>

      <Outlet />
    </>
  );
}
```

---

# 🎯 Interview Answer

## ❓ What is Outlet?

### ✅ Answer:

Outlet is used to render nested child routes inside parent routes.

---

# 📘 Protected Routes

---

# 📌 What are Protected Routes?

Protected routes restrict unauthorized users.

---

# 📌 Example

```jsx id="jlwm8f"
import {
  Navigate
} from "react-router-dom";

function ProtectedRoute({
  children
}) {
  const isAuth = true;

  return isAuth
    ? children
    : <Navigate to="/login" />;
}
```

---

# 📌 Usage

```jsx id="jlwm3j"
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

# 🎯 Interview Answer

## ❓ What are Protected Routes?

### ✅ Answer:

Protected routes restrict access to certain pages unless the user is authenticated.

---

# 📘 Navigate Component

---

# 📌 What is Navigate?

`Navigate` redirects users to another route.

---

# 📌 Example

```jsx id="jlwm7y"
<Navigate to="/login" />
```

---

# 🎯 Interview Answer

## ❓ What is Navigate?

### ✅ Answer:

Navigate is used for redirecting users programmatically in React Router.

---

# 📘 useLocation

---

# 📌 What is useLocation?

Used to get current route information.

---

# 📌 Example

```jsx id="jlwm4n"
import {
  useLocation
} from "react-router-dom";

function App() {
  const location = useLocation();

  console.log(location.pathname);
}
```

---

# 🎯 Interview Answer

## ❓ What is useLocation?

### ✅ Answer:

useLocation provides information about the current URL and route.

---

# 📘 Lazy Loading Routes

---

# 📌 What is Lazy Loading?

Components load only when needed.

---

# 📌 Example

```jsx id="jlwm0m"
import React, {
  lazy,
  Suspense
} from "react";

const About = lazy(() =>
  import("./About")
);
```

---

# 📌 Suspense

```jsx id="jlwm9x"
<Suspense fallback={<h1>Loading...</h1>}>
  <About />
</Suspense>
```

---

# 🎯 Interview Answer

## ❓ Why use lazy loading in routing?

### ✅ Answer:

Lazy loading improves performance by loading route components only when required.

---

# 📘 Route Parameters vs Query Parameters

---

# 📌 Route Params

```txt id="jlwm5b"
/user/10
```

Accessed using:

```jsx id="jlwm2d"
useParams()
```

---

# 📌 Query Params

```txt id="jlwm6q"
/products?category=mobile
```

Accessed using:

```jsx id="jlwm1w"
useSearchParams()
```

---

# 📘 404 Page / Not Found Route

---

# 📌 Example

```jsx id="jlwm8k"
<Route
  path="*"
  element={<NotFound />}
/>
```

---

# 📌 Purpose

Handles invalid routes.

---

# 🎯 Interview Answer

## ❓ Why use `path="*"`?

### ✅ Answer:

`path="*"` is used to display a 404 page for unmatched routes.

---

# 📘 useSearchParams

---

# 📌 What is useSearchParams?

Used to read/update query parameters.

---

# 📌 Example

```jsx id="jlwm3u"
import {
  useSearchParams
} from "react-router-dom";

const [searchParams] =
  useSearchParams();

console.log(
  searchParams.get("category")
);
```

---

# 📘 Important React Router Hooks

| Hook            | Purpose        |
| --------------- | -------------- |
| useNavigate     | Navigation     |
| useParams       | Dynamic params |
| useLocation     | Current URL    |
| useSearchParams | Query params   |

---

# 📘 React Router v6 Important Changes

| Old Version    | v6           |
| -------------- | ------------ |
| Switch         | Routes       |
| component prop | element prop |
| useHistory     | useNavigate  |


# 📘 React Router Important Concepts

---

# 📌 navigate(-1) Kya Karta Hai?

## 🔹 Definition

`navigate(-1)` browser history me previous page par le jata hai.

It works like browser back button.

---

# 📌 Example

```jsx id="jlwm1a"
import {
  useNavigate
} from "react-router-dom";

function App() {
  const navigate = useNavigate();

  return (
    <button
      onClick={() => navigate(-1)}
    >
      Go Back
    </button>
  );
}
```

---

# 📌 How it Works?

Suppose user flow:

```txt id="’winiijlwm"
/home → /about → /contact
```

If user is on:

```txt id="’winiijlwm5"
/contact
```

then:

```jsx id="’winiijlwm8"
navigate(-1)
```

takes user to:

```txt id="’winiijlwm2"
/about
```

---

# 📌 Other Examples

| Code         | Meaning         |
| ------------ | --------------- |
| navigate(-1) | Go back         |
| navigate(1)  | Go forward      |
| navigate(-2) | Go back 2 pages |

---

# 🎯 Interview Answer

## ❓ What does navigate(-1) do?

### ✅ Answer:

`navigate(-1)` navigates the user to the previous page in browser history, similar to the browser back button.

---

# 📘 replace: true Navigation Me Kya Karta Hai?

---

# 📌 Definition

`replace: true` current history entry ko replace karta hai instead of adding a new entry.

---

# 📌 Syntax

```jsx id="’winiijlwm7"
navigate("/home", {
  replace: true
});
```

---

# 📌 Why Use replace: true?

Normally:

```jsx id="’winiijlwm1"
navigate("/home")
```

browser history me new entry add karta hai.

---

# 📌 Problem

Login page se dashboard gaye:

```txt id="’winiijlwm4"
/login → /dashboard
```

User back button dabaye to:

❌ Login page par wapas aa sakta hai.

---

# 📌 Solution

```jsx id="’winiijlwm9"
navigate("/dashboard", {
  replace: true
});
```

Now login page history se replace ho jayega.

---

# 📌 Result

Back button se user login page par nahi jayega.

---

# 📌 Common Use Cases

✅ Login redirects
✅ Logout redirects
✅ Payment success pages

---

# 🎯 Interview Answer

## ❓ What does replace: true do in navigation?

### ✅ Answer:

`replace: true` replaces the current history entry instead of adding a new one, preventing users from navigating back to the previous page.

---

# 📘 MemoryRouter

---

# 📌 What is MemoryRouter?

MemoryRouter stores routing history in memory instead of browser URL.

---

# 📌 Important Point

It does NOT update browser address bar.

---

# 📌 Example

```jsx id="’winiijlwm3"
import {
  MemoryRouter
} from "react-router-dom";

<MemoryRouter>
  <App />
</MemoryRouter>
```

---

# 📌 When to Use MemoryRouter?

Mainly used for:

✅ Testing
✅ React Native
✅ Non-browser environments

---

# 📌 Why?

Because browser history API may not be available there.

---

# 📌 Features

✅ Internal memory history
✅ Fast testing
❌ No URL changes

---

# 🎯 Interview Answer

## ❓ What is MemoryRouter?

### ✅ Answer:

MemoryRouter stores routing history in memory instead of the browser URL and is mainly used in testing and non-browser environments.

---

# 📘 StaticRouter

---

# 📌 What is StaticRouter?

StaticRouter is used for:

# 👉 Server Side Rendering (SSR)

---

# 📌 Why StaticRouter Needed?

BrowserRouter depends on browser APIs.

But server side me:

❌ Browser available nahi hota.

So SSR me StaticRouter use hota hai.

---

# 📌 Example

```jsx id="’winiijlwm6"
import {
  StaticRouter
} from "react-router-dom/server";

<StaticRouter location={req.url}>
  <App />
</StaticRouter>
```

---

# 📌 How it Works?

Server current request URL ko route match karta hai aur HTML generate karta hai.

---

# 📌 Benefits

✅ Better SEO
✅ Faster first page load
✅ Better SSR support


# 📘 useLoaderData in React Router

---

# 📌 What is useLoaderData?

`useLoaderData` is a React Router hook used to access data loaded by a route loader function.

It is introduced in:

# 👉 React Router v6.4+

---

# 📌 Simple Meaning

Before rendering a page, React Router can fetch data automatically using a loader function.

`useLoaderData()` is used to access that fetched data inside the component.

---

# 📌 Why useLoaderData is Used?

Normally in React:

❌ We fetch data inside `useEffect`.

But with React Router loaders:

✅ Data loads before component renders.

---

# 📌 Benefit

✅ Cleaner code
✅ Better routing-based data fetching
✅ No extra loading logic in component
✅ Better user experience

---

# 📌 Basic Flow

```txt id="jlwm1q"
Route Loader → Fetch Data →
useLoaderData() → Component
```

---

# 📌 Example

---

# 🔥 Step 1 — Create Loader Function

```jsx id="jlwm6n"
export async function userLoader() {
  const response = await fetch(
    "https://jsonplaceholder.typicode.com/users"
  );

  return response.json();
}
```

---

# 🔥 Step 2 — Add Loader in Route

```jsx id="’winiijlwm"
import {createBrowserRouter} from "react-router-dom";

import Users, {userLoader} from "./Users";

const router = createBrowserRouter([
  {
    path: "/users",
    element: <Users />,
    loader: userLoader
  }
]);
```

---

# 🔥 Step 3 — Access Data Using useLoaderData

```jsx id="’winiijlwm7"
import {
  useLoaderData
} from "react-router-dom";

function Users() {
  const users = useLoaderData();

  return (
    <div>
      {users.map((user) => (
        <h2 key={user.id}>
          {user.name}
        </h2>
      ))}
    </div>
  );
}

export default Users;
```

---

# 📌 How it Works?

---

# ✅ Route opens

```txt id="’winiijlwm2"
/users
```

---

# ✅ Loader function runs first

```jsx id="’winiijlwm5"
userLoader()
```

---

# ✅ Data fetched before render

---

# ✅ useLoaderData gets data

```jsx id="’winiijlwm0"
const users = useLoaderData();
```

---

# 📌 Difference Between useEffect and useLoaderData

| useEffect                | useLoaderData          |
| ------------------------ | ---------------------- |
| Fetch after render       | Fetch before render    |
| Manual loading state     | Router handles loading |
| Component-based fetching | Route-based fetching   |
| More boilerplate         | Cleaner approach       |

---

# 📌 Important Point

`useLoaderData()` only works with routes that have:

# 👉 loader property

---

# 📌 Real Use Cases

✅ Product details page
✅ User profile page
✅ Dashboard data
✅ Route-based API fetching

---

# 🎯 Interview Answers

---

# ❓ What is useLoaderData?

### ✅ Answer:

`useLoaderData` is a React Router hook used to access data loaded by a route loader function before the component renders.

---

# ❓ Why use useLoaderData instead of useEffect?

### ✅ Answer:

useLoaderData fetches data before rendering the component, resulting in cleaner code and better route-based data handling compared to useEffect.

---

# ❓ Which React Router version introduced useLoaderData?

### ✅ Answer:

`useLoaderData` was introduced in React Router v6.4.


# 📌 Difference Between BrowserRouter and StaticRouter

| BrowserRouter        | StaticRouter         |
| -------------------- | -------------------- |
| Client-side routing  | Server-side routing  |
| Uses browser history | Uses static location |
| Used in browser      | Used in SSR          |

---

# 🎯 Interview Answer

## ❓ What is StaticRouter?

### ✅ Answer:

StaticRouter is used for server-side rendering in React applications where browser APIs are unavailable.


# 📘 Difference Between `window.history.back()` and `navigate(-1)` in React Router

# 📌 window.history.back()

## 🔹 Definition

`window.history.back()` is a native JavaScript browser API.

It moves the browser to the previous page in history.

---

# 📌 Example

```js id="jlwm1p"
window.history.back();
```

---

# 📌 Features

✅ Native browser method
✅ Works outside React
✅ Direct browser history control

---

# 📌 Problem in React Apps

It bypasses React Router navigation system.

Sometimes React state/UI synchronization issues can happen.

---

# 📘 navigate(-1)

---

# 📌 Definition

`navigate(-1)` is a React Router navigation method.

It moves back one step in routing history.

---

# 📌 Example

```jsx id="jlwm6m"
const navigate = useNavigate();

navigate(-1);
```

---

# 📌 Features

✅ React Router aware
✅ Works properly with SPA routing
✅ Better integration with React

---

# 📌 Why Better in React?

Because it works with:

✅ React Router history
✅ Route state
✅ SPA navigation flow

---

# 📌 Main Difference

| window.history.back()        | navigate(-1)              |
| ---------------------------- | ------------------------- |
| Browser API                  | React Router API          |
| Outside React                | Inside React Router       |
| Bypasses router              | Router aware              |
| Less preferred in React apps | Recommended in React apps |

---

# 📌 Example Scenario

Suppose React app has:

```txt id="jlwm9t"
/home → /about → /contact
```

---

# ✅ Using navigate(-1)

```jsx id="jlwm3f"
navigate(-1);
```

React Router properly handles route transition.

---

# ❌ Using window.history.back()

```js id="’winiijlwm"
window.history.back();
```

Browser directly changes history without React Router control.

---

# 📌 Best Practice

In React applications:

# 👉 Prefer `navigate(-1)`

because it integrates properly with React Router.

---

# 🎯 Interview Answer

## ❓ Difference Between `window.history.back()` and `navigate(-1)`?

### ✅ Answer:

`window.history.back()` is a native browser API that moves back in browser history directly, while `navigate(-1)` is a React Router method that performs back navigation within React Router’s routing system.

In React applications, `navigate(-1)` is preferred because it works better with SPA routing and React Router state management.


# 📘 Very Important React Router Topics & Hooks (Interview Most Asked)

Ye topics bahot frequently React interviews me puchhe jate hain 👇

---

# 📌 1️⃣ useOutletContext

## 🔹 What is it?

Parent route se nested child routes ko data pass karne ke liye use hota hai.

---

# 📌 Example

## Parent

```jsx id="jlwm1a"
import {
  Outlet
} from "react-router-dom";

function Dashboard() {
  return (
    <Outlet context={"Krupa"} />
  );
}
```

---

## Child

```jsx id="’winiijlwm"
import {
  useOutletContext
} from "react-router-dom";

function Profile() {
  const data =
    useOutletContext();

  return <h1>{data}</h1>;
}
```

---

# 🎯 Interview Answer

`useOutletContext` nested routes me parent se child ko data pass karne ke liye use hota hai.

# 📘 4️⃣ RouterProvider


# 📌 What is it?

`createBrowserRouter` ke saath router provide karta hai.

---

# 📌 Example

```jsx id="’winiijlwm5"
<RouterProvider router={router} />
```

---

# 🎯 Interview Answer

`RouterProvider` application ko configured router provide karta hai.

---

# 📘 5️⃣ Loader Function

---

# 📌 What is Loader?

Component render hone se pehle data fetch karta hai.

---

# 📌 Example

```jsx id="’winiijlwm0"
export async function loader() {
  return fetch("/api/users");
}
```

---

# 🎯 Interview Answer

Loader function route render hone se pehle required data fetch karta hai.

---

# 📘 6️⃣ useLoaderData

---

# 📌 What is it?

Loader se fetched data access karne ke liye use hota hai.

---

# 📌 Example

```jsx id="’winiijlwm8"
const data = useLoaderData();
```

---

# 🎯 Interview Answer

`useLoaderData` loader function ke fetched data ko component me access karta hai.


# 📘 8️⃣ useMatch

# 📘 useMatch in React Router

---

# 📌 What is useMatch?

`useMatch` React Router hook hai jo check karta hai:

👉 Current URL kisi specific route se match ho raha hai ya nahi.

---

# 📌 Simple Meaning

Agar current page:

```txt id="’winiijlwm"
/about
```

hai aur hum check kare:

```jsx id="’winiijlwm7"
useMatch("/about")
```

to match mil jayega.

---

# 📌 Syntax

```jsx id="’winiijlwm2"
const match = useMatch("/about");
```

---

# 📌 Example

```jsx id="’winiijlwm5"
import {
  useMatch
} from "react-router-dom";

function About() {
  const match =
    useMatch("/about");

  return (
    <div>
      {match ? (
        <h1>Route Matched</h1>
      ) : (
        <h1>No Match</h1>
      )}
    </div>
  );
}

export default About;
```

---

# 📌 How it Works?

---

# ✅ If Current URL

```txt id="’winiijlwm0"
/about
```

then:

```jsx id="’winiijlwm8"
useMatch("/about")
```

returns:

```txt id="’winiijlwm3"
match object
```

---

# ❌ If URL Different

```txt id="’winiijlwm6"
/contact
```

then:

```jsx id="’winiijlwm1"
null
```

return hota hai.

---

# 📌 Return Value

| Result       | Meaning       |
| ------------ | ------------- |
| Match Object | Route matched |
| null         | No match      |

---

# 📌 Real Use Cases

✅ Active sidebar/menu
✅ Conditional rendering
✅ Route checking
✅ Custom navigation highlighting

---

# 📌 Example — Active Menu

```jsx id="’winiijlwm9"
import {
  Link,
  useMatch
} from "react-router-dom";

function Navbar() {
  const match =
    useMatch("/about");

  return (
    <div>
      <Link to="/about">
        About
      </Link>

      {match && (
        <p>About Page Active</p>
      )}
    </div>
  );
}
```

---

# 📌 Difference Between useMatch and NavLink

| useMatch              | NavLink                     |
| --------------------- | --------------------------- |
| Manual route matching | Automatic active link       |
| Used in custom logic  | Used for navigation styling |
| Returns match object  | Adds active class           |

---

# 📌 Important Point

`useMatch()` sirf current URL ko compare karta hai.

Ye navigation nahi karta.

---

# 🎯 Interview Answers

---

# ❓ What is useMatch?

### ✅ Answer:

`useMatch` is a React Router hook used to check whether the current URL matches a specific route path.

---

# ❓ What does useMatch return?

### ✅ Answer:

If the route matches, `useMatch` returns a match object; otherwise it returns null.

---

# ❓ Common use case of useMatch?

### ✅ Answer:

`useMatch` is commonly used for active route checking, conditional rendering, and custom navigation highlighting.




# 📘 9️⃣ defer()

---

# 📌 What is it?

Slow data ko deferred loading ke liye use karte hain.

---

# 📌 Benefit

✅ Faster UI rendering
✅ Partial loading

---

# 📌 Example

```jsx id="’winiijlwm9"
defer({
  users: fetchUsers()
});
```

---

# 🎯 Interview Answer

`defer()` asynchronous data ko delay karke better loading experience provide karta hai.

---

# 📘 🔟 Await Component

---

# 📌 What is it?

Deferred data render karne ke liye use hota hai.

---

# 📌 Example

```jsx id="’winiijlwm4"
<Await resolve={data.users}>
  {(users) => <Users users={users} />}
</Await>
```

---

# 🎯 Interview Answer

`Await` deferred asynchronous data ko render karne ke liye use hota hai.

---

# 📘 1️⃣1️⃣ ErrorElement

---

# 📌 What is it?

Route-level error handling ke liye use hota hai.

---

# 📌 Example

```jsx id="’winiijlwmq"
{
  path: "/",
  element: <Home />,
  errorElement: <ErrorPage />
}
```

---

# 🎯 Interview Answer

`errorElement` route errors handle karne ke liye use hota hai.

---


# 📌 MOST IMPORTANT React Router Hooks List

| Hook             | Purpose                 |
| ---------------- | ----------------------- |
| useNavigate      | Navigation              |
| useParams        | Dynamic params          |
| useLocation      | Current route info      |
| useSearchParams  | Query params            |
| useLoaderData    | Loader data             |
| useOutletContext | Parent-child route data |
| useNavigation    | Navigation state        |
| useMatch         | Route matching          |



# 📘 Difference Between useNavigate and useNavigation in React Router

---

# 📌 useNavigate

## 🔹 What is useNavigate?

`useNavigate` is used for:

👉 Programmatic Navigation

It changes routes/pages.

---

# 📌 Example

```jsx id="jlwm1x"
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
      Go To About
    </button>
  );
}
```

---

# 📌 What Does It Do?

When button clicked:

```txt id="’লwiniijlwm"
/about
```

page open ho jayega.

---

# 📌 Common Use Cases

✅ Login redirect
✅ Form submit redirect
✅ Back button navigation

---

# 📌 Example

```jsx id="’winiijlwm7"
navigate(-1);
```

Go back to previous page.

---

## ❓ What is useNavigate?

### ✅ Answer:

`useNavigate` is a React Router hook used for programmatic navigation between routes.

---

# 📘 useNavigation

---

# 📌 What is useNavigation?

`useNavigation` is used for:

👉 Tracking Navigation State

It tells whether navigation/loading is happening.

---

# 📌 Example

```jsx id="’winiijlwm2"
import {
  useNavigation
} from "react-router-dom";

function App() {
  const navigation =
    useNavigation();

  return (
    <>
      {navigation.state ===
      "loading" ? (
        <h1>Loading...</h1>
      ) : (
        <h1>Page Loaded</h1>
      )}
    </>
  );
}
```

---

# 📌 What Does It Do?

During route transition:

```txt id="’winiijlwm5"
loading state
```

track karta hai.

---

# 📌 Common Use Cases

✅ Global loading spinner
✅ Route transition loader
✅ API loading state

---

# 📌 navigation.state Values

| Value      | Meaning         |
| ---------- | --------------- |
| idle       | No navigation   |
| loading    | Route loading   |
| submitting | Form submitting |

---

# 🎯 Interview Answer

## ❓ What is useNavigation?

### ✅ Answer:

`useNavigation` is a React Router hook used to track the current navigation state such as loading or submitting during route transitions.

---

# 📘 Main Difference Between useNavigate and useNavigation

| useNavigate          | useNavigation                      |
| -------------------- | ---------------------------------- |
| Used for navigation  | Used for tracking navigation state |
| Changes route        | Monitors route transition          |
| Programmatic routing | Loading state handling             |
| navigate("/about")   | navigation.state                   |

---

# 📌 Simple Easy Understanding

---

# 🔥 useNavigate

👉 "Go to another page"

---

# 🔥 useNavigation

👉 "Check if page is loading while navigating"

---

# 📌 Real Interview Example

---

# ✅ useNavigate

```jsx id="’winiijlwm0"
navigate("/dashboard");
```

Moves user to dashboard.

---

# ✅ useNavigation

```jsx id="’winiijlwm8"
navigation.state === "loading"
```

Shows loader while page loads.

---

# 🎯 Final Interview Answer

## ❓ Difference Between useNavigate and useNavigation?

### ✅ Answer:

`useNavigate` is used to programmatically navigate between routes, while `useNavigation` is used to track the navigation/loading state during route transitions.

---


# BrowserRouter vs createBrowserRouter (Interview Notes)

## When to Use Which?

### BrowserRouter

Use when:

* Small Projects
* Learning React Router
* Simple Routing
* No Loader/Action needed

```jsx
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
  </Routes>
</BrowserRouter>
```

---

### createBrowserRouter

Use when:

* Large Scale Applications
* Data Fetching
* Nested Layouts
* Error Handling
* Modern React Router Projects

```jsx
const router = createBrowserRouter([
  {
    path: "/",
    element: <Home />,
  },
]);
```

---

# Main Differences

| Feature          | BrowserRouter | createBrowserRouter |
| ---------------- | ------------- | ------------------- |
| Setup            | JSX Based     | Config Based        |
| Nested Routes    | ✅             | ✅                   |
| Protected Routes | ✅             | ✅                   |
| Loader           | ❌             | ✅                   |
| Action           | ❌             | ✅                   |
| Error Page       | ❌             | ✅                   |
| Data Fetching    | ❌             | ✅                   |
| Recommended      | Old Pattern   | Modern Pattern      |

---

# Nesting in BrowserRouter

## Layout.jsx

```jsx
import { Outlet } from "react-router-dom";

function Layout() {
  return (
    <>
      <h1>Navbar</h1>
      <Outlet />
    </>
  );
}
```

## App.jsx

```jsx
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Layout />}>
      <Route index element={<Home />} />
      <Route path="about" element={<About />} />
    </Route>
  </Routes>
</BrowserRouter>
```

---

# Nesting in createBrowserRouter

```jsx
const router = createBrowserRouter([
  {
    path: "/",
    element: <Layout />,
    children: [
      {
        index: true,  // index: true ka matlab hota hai default child route.
        // Jab user sirf "/" par aata hai aur koi child path match nahi hota, tab index: true wala component render hota hai.
        element: <Home />,
      },
      {
        path: "about",
        element: <About />,
      },
    ],
  },
]);
```

---

# Protected Route

## BrowserRouter

```jsx
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

## createBrowserRouter

```jsx
{
  path: "/dashboard",
  element: (
    <ProtectedRoute>
      <Dashboard />
    </ProtectedRoute>
  )
}
```

---

# Loader (Only createBrowserRouter)

```jsx
const router = createBrowserRouter([
  {
    path: "/users",
    loader: async () => {
      return fetch("/api/users");
    },
    element: <Users />,
  },
]);
```

Inside Component:

```jsx
import { useLoaderData } from "react-router-dom";

function Users() {
  const data = useLoaderData();

  return <div>{data.length}</div>;
}
```

---

# Action (Only createBrowserRouter)

```jsx
{
  path: "/add-user",
  action: async ({ request }) => {
    const formData = await request.formData();

    return fetch("/api/users", {
      method: "POST",
      body: formData,
    });
  },
  element: <AddUser />
}
```

---

# Error Page (Only createBrowserRouter)

```jsx
{
  path: "/",
  element: <Home />,
  errorElement: <ErrorPage />
}
```

---

# Interview Answer

### Why createBrowserRouter over BrowserRouter?

Because it provides:

* Loader
* Action
* Error Handling
* Better Nested Routing
* Data Fetching before Component Render

Hence it is preferred in modern React applications.

### Quick Rule

```text
Small Project  -> BrowserRouter

Large Project  -> createBrowserRouter
```

---

# BrowserRouter vs createBrowserRouter

| Feature                  | BrowserRouter | createBrowserRouter       |
| ------------------------ | ------------- | ------------------------- |
| Setup                    | Easy          | Slightly Advanced         |
| Routes Definition        | Inside JSX    | Route Configuration Array |
| Loader Support           | No            | Yes                       |
| Action Support           | No            | Yes                       |
| Error Handling           | Limited       | Built-in                  |
| Recommended for New Apps | No            | Yes                       |
| React Router Version     | Old Pattern   | Modern Pattern            |

---

# Interview Questions

## What is BrowserRouter?

BrowserRouter enables routing in React applications using the browser history API.

---

## What is createBrowserRouter?

createBrowserRouter is the modern routing API introduced in React Router v6.4 that supports loaders, actions, error handling, and data fetching.

---

## Which one should we use in new projects?

Use `createBrowserRouter` because it provides more features and is the recommended approach in modern React Router applications.

---

# Quick Summary

Traditional Routing:

```jsx
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
  </Routes>
</BrowserRouter>
```

Modern Routing:

```jsx
const router = createBrowserRouter([
  {
    path: "/",
    element: <Home />,
  },
]);
import { RouterProvider } from 'react-router-dom';
<RouterProvider router={router} /> // default key name or variable name router
```

Modern React applications generally prefer:

```jsx
createBrowserRouter + RouterProvider
```

