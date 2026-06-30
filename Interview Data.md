Copy this directly into your `.md` file:

# React Interview Question: How to Stop Multiple Continuous API Calls?

## Question

**"If multiple API calls are happening continuously and the component gets unmounted or a new request is triggered, how will you stop the previous API calls?"**

---

# Why is this a Problem?

When multiple API requests are fired continuously:

* Unnecessary network requests are sent.
* Server load increases.
* Application performance becomes slow.
* Memory leaks can occur.
* React may show state update warnings.
* Old API responses may overwrite new data.

To avoid these issues, we can use:

1. AbortController
2. Debouncing
3. React Query (TanStack Query)
4. Proper useEffect dependency management
5. React performance optimization techniques

---

# 1. AbortController (Most Common Interview Answer)

## Definition

AbortController is a browser API used to cancel pending API requests.

It is commonly used when:

* Component unmounts before API response arrives.
* User triggers another request before the previous one finishes.
* We want to stop unnecessary API calls.

---

## Example

```jsx
import { useEffect, useState } from "react";

function Users() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    const controller = new AbortController();

    fetch("https://jsonplaceholder.typicode.com/users", {
      signal: controller.signal,
    })
      .then((res) => res.json())
      .then((data) => setUsers(data))
      .catch((err) => {
        if (err.name !== "AbortError") {
          console.log(err);
        }
      });

    return () => {
      controller.abort();
    };
  }, []);

  return <div>{users.length}</div>;
}
```

---

## Explanation

### Step 1

Create AbortController.

```js
const controller = new AbortController();
```

### Step 2

Attach signal to API request.

```js
signal: controller.signal;
```

### Step 3

When component unmounts, cleanup function runs.

```js
return () => {
  controller.abort();
};
```

### Step 4

Pending API request gets cancelled.

Benefits:

* Prevents memory leaks.
* Prevents unnecessary state updates.
* Improves performance.
* Saves network bandwidth.

---

# Interview Answer

> If a component unmounts before the API response arrives, I use AbortController inside the useEffect cleanup function. It cancels the pending request and prevents unnecessary state updates and memory leaks.

---

# Real Interview Scenario

## Search Input

User types:

```text
r
re
rea
react
```

Without optimization:

```text
r      → API Call
re     → API Call
rea    → API Call
react  → API Call
```

Total = 4 API Calls ❌

This creates unnecessary requests.

---

# 2. Debouncing

## Definition

Debouncing delays API execution until the user stops typing for a specified amount of time.

Instead of calling the API on every key press, it waits for a pause.

---

## Example

```jsx
import { useEffect, useState } from "react";

function Search() {
  const [search, setSearch] = useState("");

  useEffect(() => {
    const timer = setTimeout(() => {
      fetchData(search);
    }, 500);

    return () => clearTimeout(timer);
  }, [search]);

  return (
    <input
      value={search}
      onChange={(e) => setSearch(e.target.value)}
    />
  );
}
```

---

## Explanation

### User types:

```text
r
re
rea
react
```

Every time user types:

```js
clearTimeout(timer);
```

Previous timer gets cancelled.

API is called only after user stops typing for 500ms.

Benefits:

* Reduces API calls.
* Improves performance.
* Reduces server load.
* Better user experience.

---

# Interview Answer

> For search inputs, I use debouncing so that API requests are triggered only after the user stops typing for a short period. This prevents unnecessary API calls and improves performance.

---

# 3. React Query (TanStack Query)

## Definition

TanStack Query is a library used for managing server state efficiently.

It automatically handles:

* Caching
* Deduplication
* Background refetching
* Loading states
* Error handling

---

## Example

```jsx
const { data } = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
  staleTime: 5000,
});
```

---

## Benefits

### Caching

Previously fetched data is reused.

### Deduplication

Duplicate API requests are automatically prevented.

### Background Refetching

Keeps data fresh.

### Better Server State Management

Less manual code.

---

# Interview Answer

> In larger applications, I prefer TanStack Query because it provides caching, request deduplication, background refetching, and better server-state management out of the box.

---

# Another Common Interview Question

## Question

**"If APIs are continuously firing because of re-renders, how will you stop them?"**

---

# Root Cause

Usually this happens because:

* Wrong useEffect dependency array.
* Frequent component re-renders.
* Functions recreated on every render.
* State updates triggering re-renders.

---

# Wrong Example

```jsx
useEffect(() => {
  fetchUsers();
});
```

This runs after every render.

Result:

```text
Render
→ API Call

Render
→ API Call

Render
→ API Call
```

Infinite API calls ❌

---

# Correct Example

```jsx
useEffect(() => {
  fetchUsers();
}, []);
```

Runs only once when component mounts.

✅ Correct

---

# React.memo

## Definition

React.memo prevents unnecessary re-renders of child components when props do not change.

---

## Example

```jsx
const Child = React.memo(({ name }) => {
  console.log("Rendered");

  return <h1>{name}</h1>;
});
```

Benefits:

* Avoids unnecessary rendering.
* Improves performance.

---

# useCallback

## Definition

useCallback memoizes functions and prevents recreation on every render.

---

## Example

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

Benefits:

* Prevents unnecessary re-renders.
* Useful with React.memo.

---

# useMemo

## Definition

useMemo memoizes expensive calculations.

---

## Example

```jsx
const filteredUsers = useMemo(() => {
  return users.filter((user) =>
    user.name.includes(search)
  );
}, [users, search]);
```

Benefits:

* Avoids recalculating values.
* Improves performance.

---

# Complete Interview Answer

> If multiple API calls are happening continuously, I first identify the reason. For search-based requests, I use debouncing to reduce unnecessary API calls. If a component unmounts or a new request is triggered before the previous one completes, I use AbortController to cancel the pending request. If APIs are firing because of re-renders, I optimize the component using React.memo, useCallback, useMemo, and proper useEffect dependency arrays. In larger applications, I prefer TanStack Query because it provides caching, request deduplication, background refetching, and efficient server-state management.

---

# Short Interview Answer (30 Seconds)

> To stop continuous API calls, I use debouncing for search inputs and AbortController to cancel pending requests. I also optimize re-renders using React.memo, useCallback, useMemo, and proper useEffect dependencies. In large applications, I use TanStack Query for caching, request deduplication, and better server-state management.

---

# One-Line Answer

> I use Debouncing, AbortController, proper useEffect dependencies, React.memo, useCallback, useMemo, and TanStack Query to prevent unnecessary API calls and improve application performance.


Ye directly `.md` file me save kar sakti ho:


**"How do you optimize bundle size in a React application?"**

---

# What is Bundle Size?

Bundle size refers to the total JavaScript, CSS, images, and other assets that are downloaded by the browser when the application loads.

A larger bundle size can cause:

* Slow page load time
* Poor user experience
* Higher network usage
* Lower Lighthouse scores
* Reduced application performance

Therefore, bundle size optimization is important for improving application performance.

---

# 1. Code Splitting (Most Important)

## Definition

Instead of loading the entire application in a single JavaScript bundle, split it into smaller chunks and load them only when needed.

---

## Example

```jsx
import React, { Suspense, lazy } from "react";

const Dashboard = lazy(() => import("./Dashboard"));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <Dashboard />
    </Suspense>
  );
}
```

---

## Explanation

Without Code Splitting:

```text
App Bundle
├── Home
├── Dashboard
├── Profile
├── Settings
└── Reports
```

Everything loads initially ❌

With Code Splitting:

```text
Initial Bundle
├── App
└── Home

Dashboard Bundle
Profile Bundle
Settings Bundle
Reports Bundle
```

Only required code loads ✅

---

## Benefits

* Faster initial load time
* Smaller JavaScript bundle
* Better performance

---

# 2. Lazy Loading Routes

## Definition

Load route components only when the user visits that route.

---

## Example

```jsx
const Home = lazy(() => import("./pages/Home"));
const Profile = lazy(() => import("./pages/Profile"));
const Dashboard = lazy(() => import("./pages/Dashboard"));
```

---

## Explanation

If user visits Home page:

```text
Only Home Bundle Downloaded
```

Profile and Dashboard bundles are loaded later.

Benefits:

* Faster application startup
* Reduced initial bundle size

---

# 3. Tree Shaking

## Definition

Tree Shaking removes unused code from the final production bundle.

Modern bundlers like:

* Webpack
* Vite
* Rollup

automatically remove unused code.

---

## Bad Example

```js
import * as lodash from "lodash";
```

Entire lodash library is imported ❌

---

## Good Example

```js
import debounce from "lodash/debounce";
```

Only debounce function is imported ✅

---

## Benefits

* Smaller bundle size
* Less unused code

---

# 4. Remove Unused Dependencies

## Definition

Many projects contain packages that are no longer used.

Unused dependencies increase bundle size unnecessarily.

---

## Check Installed Packages

```bash
npm ls
```

---

## Remove Package

```bash
npm uninstall package-name
```

---

## Benefits

* Smaller node_modules
* Reduced bundle size
* Faster builds

---

# 5. Dynamic Imports

## Definition

Load heavy libraries only when they are required.

---

## Example

```jsx
const generatePdf = async () => {
  const jsPDF = await import("jspdf");

  const pdf = new jsPDF.default();
};
```

---

## Explanation

Without Dynamic Import:

```text
jsPDF loads on page load
```

With Dynamic Import:

```text
jsPDF loads only when user clicks Generate PDF
```

Benefits:

* Faster initial page load
* Smaller initial bundle

---

# 6. Optimize Images

Images often consume more size than JavaScript.

---

## Best Practices

### Use Modern Formats

```text
WebP
AVIF
```

Instead of:

```text
PNG
JPEG
```

---

### Compress Images

Use:

* TinyPNG
* ImageOptim
* Squoosh

---

### Lazy Load Images

```html
<img
  src="image.webp"
  loading="lazy"
  alt="Image"
/>
```

---

## Benefits

* Faster page loading
* Reduced bandwidth usage

---

# 7. Memoization

## Definition

Prevent unnecessary re-renders and calculations.

---

## React.memo

```jsx
const Child = React.memo(() => {
  return <div>Child</div>;
});
```

---

## useMemo

```jsx
const filteredData = useMemo(() => {
  return users.filter(user =>
    user.name.includes(search)
  );
}, [users, search]);
```

---

## useCallback

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

---

## Benefits

* Reduced re-renders
* Better runtime performance

---

# 8. Analyze Bundle Size

## Definition

Before optimizing, identify which package is increasing bundle size.

---

## Webpack Bundle Analyzer

Install:

```bash
npm install webpack-bundle-analyzer
```

---

## Result

You can visualize:

```text
React
Redux
Lodash
Moment
Charts
```

and see which package consumes the most space.

---

# Vite Bundle Analyzer

Install:

```bash
npm install rollup-plugin-visualizer
```

---

## Benefits

* Identifies large dependencies
* Helps find optimization opportunities

---

# 9. Use Production Build

Development builds contain:

* Source maps
* Debugging code
* Development warnings

Production builds remove unnecessary code.

---

## Command

```bash
npm run build
```

---

## Benefits

* Minified code
* Smaller bundle
* Better performance

---

# 10. Replace Heavy Libraries

## Example

### Bad

```text
Moment.js
```

Size:

```text
~200KB+
```

---

### Better

```text
Day.js
```

Size:

```text
~2KB
```

---

## Other Examples

| Heavy Library        | Lightweight Alternative        |
| -------------------- | ------------------------------ |
| Moment.js            | Day.js                         |
| Lodash               | Native JS Methods              |
| Axios (simple cases) | Fetch API                      |
| Full Calendar        | Lightweight Calendar Libraries |

---

# Additional Optimization Techniques

## Virtualization

For large lists use:

```text
react-window
react-virtualized
```

Only visible items render.

---

## Gzip/Brotli Compression

Enable compression on server.

Benefits:

* Smaller download size
* Faster loading

---

## CDN Usage

Serve static assets through CDN.

Benefits:

* Faster asset delivery
* Better caching

---

# Real Interview Answer (2-3 Lines)

> To optimize bundle size, I use code splitting and lazy loading for routes and large components, remove unused dependencies, leverage tree shaking through selective imports, optimize images, and use dynamic imports for heavy libraries. I also analyze bundle size using webpack-bundle-analyzer or rollup-plugin-visualizer and always deploy production builds.

---

# Follow-Up Question

## How Do You Check Bundle Size?

### Step 1

Generate production build.

```bash
npm run build
```

---

### Step 2

Use Bundle Analyzer.

For Webpack:

```bash
npm install webpack-bundle-analyzer
```

For Vite:

```bash
npm install rollup-plugin-visualizer
```

---

### Step 3

Analyze the report.

Check:

* Largest packages
* Duplicate dependencies
* Unused libraries
* Large images

Then optimize or replace them.

---

# Short Interview Answer (30 Seconds)

> To optimize bundle size, I use code splitting, lazy loading, tree shaking, dynamic imports, image optimization, and remove unused dependencies. I also analyze bundles using webpack-bundle-analyzer or rollup-plugin-visualizer and use production builds to ensure the application remains fast and lightweight.

---

# One-Line Interview Answer

> I optimize bundle size using code splitting, lazy loading, tree shaking, dynamic imports, image optimization, bundle analysis tools, and by removing unused dependencies.

> In my projects, I reduced bundle size by implementing route-based code splitting using React.lazy and Suspense, replacing heavy libraries where possible, optimizing images, and analyzing builds using bundle analyzer tools. This improved initial page load time and overall application performance. ✅




# Handling Multiple APIs in a React Application

### Requirements

- Page should load as quickly as possible.
- If one API fails, only that section should show an error.
- Other sections should continue working normally.

---

## Approach

Instead of calling APIs one after another, call all APIs in parallel using `Promise.allSettled()`.

### Why `Promise.allSettled()`?

- Executes all APIs simultaneously.
- Faster page load.
- Doesn't stop execution if one API fails.
- Returns success and failure status for each API separately.

---

## Example

```javascript
useEffect(() => {
  const fetchData = async () => {
    const results = await Promise.allSettled([
      getUserDetails(),
      getOrders(),
      getNotifications(),
    ]);

    if (results[0].status === "fulfilled") {
      setUser(results[0].value);
    } else {
      setUserError("Failed to load user details");
    }

    if (results[1].status === "fulfilled") {
      setOrders(results[1].value);
    } else {
      setOrdersError("Failed to load orders");
    }

    if (results[2].status === "fulfilled") {
      setNotifications(results[2].value);
    } else {
      setNotificationsError("Failed to load notifications");
    }
  };

  fetchData();
}, []);
```

---

## UI Handling

```jsx
<UserSection
  data={user}
  error={userError}
/>

<OrderSection
  data={orders}
  error={ordersError}
/>

<NotificationSection
  data={notifications}
  error={notificationsError}
/>
```

Each component handles its own loading/error state.

---

## Interview Answer

> To improve performance, I would call all APIs in parallel using `Promise.allSettled()`. This ensures the page loads faster because APIs don't wait for each other. If one API fails, only that section displays an error message while the remaining sections continue to work normally. Each section maintains its own loading, success, and error state, providing better user experience and fault tolerance.
