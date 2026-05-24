
# ⚛️ React Interview Notes

## 1. What is React?

React is a **JavaScript library** used to build **user interfaces (UI)**, especially for **single-page applications (SPA)**.

- Developed by Facebook
- Component-based architecture
- Reusable UI pieces

👉 In short: React helps you build fast, interactive web apps using components.

---

## 2. Why React over JavaScript?

React is preferred over plain JavaScript because:

- **Component-Based** → Reusable code, better structure
- **Virtual DOM** → Faster updates
- **Declarative UI** → Easy to understand and debug
- **State Management** → Dynamic UI updates easily
- **Large Ecosystem** → Strong community support

👉 JS can do everything, but React makes it **faster, cleaner, and scalable**.

---

## 3. What is SPA (Single Page Application)?

SPA is a web app that loads **only one HTML page** and updates content dynamically **without reloading the page**.

### Features:
- Fast navigation
- No full page reload
- Better user experience

### Example:
- Gmail
- Instagram
- React apps

👉 React is mainly used to build SPAs.

---

## 4. What is Virtual DOM? 🔥

Virtual DOM is a **lightweight copy of the real DOM**.

### How it works:
1. React creates a Virtual DOM
2. When state changes → new Virtual DOM is created
3. React compares old vs new (Diffing)
4. Updates only changed parts in real DOM

👉 This makes React **very fast**.

### Example:
If only one list item changes → React updates only that item, not the whole page.

---

## 5. How React works internally?

### Step-by-step flow:

1. **Component Render**
   - React converts JSX → Virtual DOM

2. **State/Props Change**
   - Triggers re-render

3. **Diffing Algorithm**
   - Compares old vs new Virtual DOM

4. **Reconciliation**
   - Finds minimal changes

5. **DOM Update**
   - Updates only required parts in real DOM

👉 Key concept: React follows **"Update only what changed"**


````md
# Key in React List

## What is Key in React?
A `key` is a special prop used in React lists to uniquely identify each element.

React uses keys to:
- Identify which item changed
- Re-render efficiently
- Improve performance

---

## Example

```jsx
const users = ["Krupa", "Rahul", "Aman"];

function App() {
  return (
    <ul>
      {users.map((user, index) => (
        <li key={index}>{user}</li>
      ))}
    </ul>
  );
}
````

---

## Best Practice

Use unique IDs instead of index.

```jsx
<li key={user.id}>{user.name}</li>
```

---

## Why Key is Important?

* Helps React track elements
* Avoids unnecessary re-render
* Improves UI performance
* Required when rendering lists using `map()`

---

## Wrong Practice

```jsx
key={Math.random()}
```

Because key changes every render.

---

## Interview One-Line Answer

> Key is a special React prop used to uniquely identify list elements so React can efficiently update and re-render components.

# Why Not Use Index as Key in React?

## Problem with Index as Key

When list items are:
- Added
- Removed
- Reordered

React gets confused because index changes.

This can cause:
- Wrong UI updates
- Performance issues
- State mismatch

---

## Bad Example

```jsx
{users.map((user, index) => (
  <li key={index}>{user.name}</li>
))}
````

If one item is deleted, all indexes shift.

React may re-render wrong items.

---

## Why Use user.id?

`user.id` is unique and stable.

```jsx
{users.map((user) => (
  <li key={user.id}>{user.name}</li>
))}
```

Benefits:

* Correct re-rendering
* Better performance
* Stable identity for each item

---

## Interview One-Line Answer

> We avoid using index as key because indexes can change when list items are added or removed. Using unique IDs gives stable rendering and better performance.



# How to Avoid Re-render in React

## 1. Use React.memo

Prevents component re-render if props do not change.

```jsx
const Child = React.memo(({ name }) => {
  return <h1>{name}</h1>;
});
````

---

## 2. Use useCallback

Prevents function recreation on every render.

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

---

## 3. Use useMemo

Memoizes expensive calculations.

```jsx
const result = useMemo(() => {
  return heavyCalculation(data);
}, [data]);
```

---

## 4. Avoid Updating Unnecessary State

Only update state when needed.

```jsx
setCount(count + 1);
```

Avoid multiple unnecessary state updates.

---

## 5. Split Components

Create smaller components so only required parts re-render.

---

## 6. Use Proper Key in Lists

Use unique IDs instead of index.

```jsx
key={user.id}
```

---

## 7. Avoid Inline Functions & Objects

Bad:

```jsx
<Button onClick={() => handleClick()} />
```

Better:

```jsx id="95c3o7"
<Button onClick={handleClick} />
```

---

## Interview One-Line Answer

> We can avoid unnecessary re-renders in React using React.memo, useCallback, useMemo, proper state management, and stable keys.


# Difference Between

## Bad

```jsx
<Button onClick={() => handleClick()} />
````

## Better

```jsx
<Button onClick={handleClick} />
```

---

# Main Difference

## 1. First One Creates New Function Every Render

```jsx
() => handleClick()
```

This arrow function is recreated on every render.

So React thinks:

* New function came
* Props changed
* Component may re-render

This can reduce performance.

---

## 2. Second One Uses Same Function Reference

```jsx
onClick={handleClick}
```

Here React gets the same function reference.

Benefits:

* Better performance
* Avoid unnecessary re-render
* Cleaner code

---

# When Arrow Function is Needed?

Use arrow function only when passing arguments.

```jsx
<Button onClick={() => handleClick(id)} />
```

Because directly writing:

```jsx
onClick={handleClick(id)}
```

will execute immediately.

---

# Interview One-Line Answer

> `onClick={() => handleClick()}` creates a new function on every render, while `onClick={handleClick}` passes the same function reference and gives better performance.


# Why We Use `{}` in Props and Parameters in React

In React, `{}` is used for two different purposes.

---

## 1. While Sending Props

```jsx
<Component data={data} />
````

Here `{}` is used to write JavaScript inside JSX.

Example:

```jsx id="2ab8oc"
const name = "Krupa";

<Component username={name} />
```

React sends it like:

```js id="78y2fb"
{
  username: "Krupa"
}
```

---

## 2. While Receiving Props

```jsx id="wxg9wq"
const Child = ({ username }) => {
  return <h1>{username}</h1>;
};
```

Here `{}` is used for object destructuring.

Instead of writing:

```jsx id="m6pjlwm"
props.username
```

we directly extract the value.

---

## Without Destructuring

```jsx id="k3hr0s"
const Child = (props) => {
  return <h1>{props.username}</h1>;
};
```

---

## Simple Difference

* `{}` in JSX → JavaScript expression
* `{}` in function parameter → Object destructuring

---

## Interview One-Line Answer

> In React, `{}` inside JSX is used to write JavaScript expressions, and `{}` in component parameters is used for object destructuring of props.


# Performance Optimization Techniques in React JS

## 1. React.memo

Prevents unnecessary component re-render.

```jsx
const Child = React.memo(({ name }) => {
  return <h1>{name}</h1>;
});
````

---

## 2. useMemo

Memoizes expensive calculations.

```jsx id="y4x7ka"
const filteredData = useMemo(() => {
  return data.filter(item => item.active);
}, [data]);
```

---

## 3. useCallback

Memoizes functions to avoid recreation.

```jsx id="e2rm7q"
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

---

## 4. Code Splitting

Load components only when needed.

```jsx id="t4l8np"
const Home = React.lazy(() => import("./Home"));
```

---

## 5. Lazy Loading

Improves initial loading performance.

```jsx id="w9dk1f"
<Suspense fallback={<h1>Loading...</h1>}>
  <Home />
</Suspense>
```

---

## 6. Proper Key Usage

Use unique IDs instead of index.

```jsx id="g7pq2s"
key={user.id}
```

---

## 7. Avoid Inline Functions

Bad:

```jsx id="m0zt8x"
<button onClick={() => handleClick()} />
```

Better:

```jsx id="f5cl9v"
<button onClick={handleClick} />
```

---

## 8. Debouncing & Throttling

Used for search input and scroll events.

Example:

* Search API call after user stops typing

---

## 9. Virtualization

Render only visible list items.

Libraries:

* react-window
* react-virtualized

---

## 10. Optimize State Management

* Keep state minimal
* Avoid unnecessary state updates
* Split large components

---

## Interview One-Line Answer

> React performance can be optimized using React.memo, useMemo, useCallback, lazy loading, code splitting, proper keys, virtualization, and avoiding unnecessary re-renders.


# Large Scale App Structure

## Answer

In large-scale React apps, I prefer feature-based folder structure instead of type-based structure.

Example:

```text
src/
 ├── features/
 │    ├── auth/
 │    ├── dashboard/
 │    ├── users/
 │
 ├── components/
 ├── hooks/
 ├── services/
 ├── redux/
 ├── routes/
 ├── utils/
 └── layouts/
````

Benefits:

* Easy maintenance
* Better scalability
* Cleaner code organization
* Team collaboration becomes easier

---

# When Not to Use Redux?

## Answer

Redux should not be used when:

* State is small
* Data sharing is limited
* App is simple
* Only local component state is needed

In such cases:

* useState
* useContext

are enough.

Redux adds extra boilerplate and complexity for small apps.

---

# Code Splitting Strategy

## Answer

Code splitting is used to load components only when needed.

I use:

* React.lazy()
* Suspense
* Dynamic imports

Example:

```jsx
const Dashboard = React.lazy(() => import("./Dashboard"));
```

Benefits:

* Faster initial load
* Smaller bundle size
* Better performance

---

# SSR vs CSR

## SSR (Server Side Rendering)

* HTML generated on server
* Faster first load
* Better SEO

Used in:

* Next.js

---

## CSR (Client Side Rendering)

* Rendering happens in browser
* Slower first load
* Better for highly interactive apps

Used in:

* React CRA / Vite apps

---

## Interview One-Line

> SSR improves SEO and initial load performance, while CSR gives better client-side interactivity.

---

# React with Next.js

## Answer

Next.js is a React framework that provides:

* SSR
* SSG
* API routes
* File-based routing
* Better SEO
* Performance optimization

I use Next.js for:

* SEO-based projects
* Fast-loading applications
* Production-ready scalable apps

---

# Testing Strategy

## Answer

I follow multiple levels of testing:

### 1. Unit Testing

Tests individual components/functions.

Tools:

* Jest
* React Testing Library

---

### 2. Integration Testing

Tests component interaction.

Example:

* Form submission
* API integration

---

### 3. End-to-End Testing

Tests complete user flow.

Tools:

* Cypress
* Playwright

---

## Main Focus

* Critical business logic
* API handling
* User interactions
* Edge cases

---

# How You Mentor Juniors?

## Answer

I mentor juniors by:

* Explaining concepts with practical examples
* Encouraging clean code practices
* Helping in debugging
* Reviewing code properly
* Teaching React best practices
* Guiding them on project structure and optimization

I also encourage them to:

* Ask questions freely
* Write reusable components
* Follow coding standards

---

# Final Interview One-Line Answer

> I focus on scalable architecture, clean code, performance optimization, proper testing, and collaborative mentoring to build maintainable React applications.


# One-Way Data Binding in React

## What is One-Way Data Binding?

One-way data binding means data flows only in one direction:

```text
Parent Component → Child Component
````

In React, data is passed using props from parent to child.

---

## Example

### Parent Component

```jsx
function Parent() {
  const name = "Krupa";

  return <Child name={name} />;
}
```

---

## Child Component

```jsx id="f9x2lw"
function Child(props) {
  return <h1>{props.name}</h1>;
}
```

---

## How It Works

* Parent sends data using props
* Child receives and displays data
* Child cannot directly modify parent data

---

## Benefits

* Better control over data
* Easier debugging
* Predictable application flow
* Improved maintainability

---

## Real Life Example

```text id="s7kp3m"
Parent controls data
Child only uses data
```

---

## Interview One-Line Answer

> One-way data binding means data flows only from parent to child components using props, making the application more predictable and easier to manage.


# What is JSX?

JSX stands for JavaScript XML.

It allows us to write HTML-like code inside JavaScript.

React uses JSX to create UI components easily.

---

## Example

```jsx
const element = <h1>Hello React</h1>;
````

---

# How JSX Works

JSX is converted into JavaScript using Babel.

Example:

```jsx id="gwm3ls"
const element = <h1>Hello</h1>;
```

Converted into:

```js id="y1a0pv"
React.createElement("h1", null, "Hello");
```

React then creates virtual DOM elements.

---

# JSX vs HTML

| JSX                              | HTML                      |
| -------------------------------- | ------------------------- |
| Uses `className`                 | Uses `class`              |
| Uses camelCase                   | Uses lowercase attributes |
| Can write JavaScript inside `{}` | Cannot write JS directly  |
| Used in React                    | Used in normal webpages   |

---

## Example

### JSX

```jsx id="igp6cs"
<h1 className="title">Hello</h1>
```

### HTML

```html id="ojhcmg"
<h1 class="title">Hello</h1>
```

---

# Expressions in JSX

JavaScript expressions are written inside `{}`.

## Example

```jsx id="qwjh7x"
const name = "Krupa";

<h1>Hello {name}</h1>
```

---

# Fragments (`<> </>`)

Fragments are used to group multiple elements without adding extra DOM nodes.

---

## Example

```jsx id="t8zl2x"
<>
  <h1>Title</h1>
  <p>Description</p>
</>
```

Equivalent to:

```jsx id="5gk1mb"
<React.Fragment>
  <h1>Title</h1>
  <p>Description</p>
</React.Fragment>
```

---

# Interview One-Line Answer

> JSX allows us to write HTML-like syntax inside JavaScript, which React converts into JavaScript objects using Babel.



# Why State is Asynchronous in React?

## What Does Asynchronous Mean?

State updates do not happen immediately.

React schedules state updates and updates the UI later for better performance.

---

## Example

```jsx
const [count, setCount] = useState(0);

setCount(count + 1);

console.log(count);
````

Output:

```text
0
```

Because state update is pending.

---

## Why React Uses Async State Updates?

React batches multiple updates together to:

* Improve performance
* Reduce unnecessary re-rendering
* Make UI updates efficient

---

## Correct Way

Use `useEffect` or updated state callback logic.

```jsx id="m7v3kd"
useEffect(() => {
  console.log(count);
}, [
  count]);
```

# Callback State Update in React

Callback state update is used when new state depends on previous state.

Because React state updates are asynchronous, callback gives the latest updated value.

---

## Example

```jsx
const [count, setCount] = useState(0);

const increment = () => {
  setCount((prevCount) => prevCount + 1);
};
````

Here:

* `prevCount` = previous state value
* React always uses latest state safely

---

## Why Use It?

Bad:

```jsx id="c4t9zl"
setCount(count + 1);
setCount(count + 1);
```

Result may be:

```text id="rjlwm2"
1
```

---

Good:

```jsx id="pxk3fw"
setCount((prev) => prev + 1);
setCount((prev) => prev + 1);
```

Result:

```text id="yrp8nm"
2
```

---

## Interview One-Line Answer

> Callback state update is used when the next state depends on the previous state because React state updates are asynchronous.


---

# Why We Don’t Modify State Directly?

React state should be updated using setter functions like:

* setState()
* useState setter

---

## Wrong Way

```jsx id="k9x2pd"
count = count + 1;
```

or

```jsx id="fvq1nm"
state.name = "Krupa";
```

---

## Correct Way

```jsx id="q3d8lw"
setCount(count + 1);
```

---

# Why Direct Modification is Bad?

Because React:

* Cannot detect changes properly
* Will not re-render component correctly
* Can create unexpected bugs

React tracks state changes using setter functions.

---

# Interview One-Line Answer

> React state is asynchronous because React batches updates for better performance, and we should never modify state directly because React may not detect changes and re-render properly.


# Rendering Concepts in React

Rendering means displaying UI on the screen.

Whenever state or props change, React updates the UI by re-rendering components.

---

# Conditional Rendering

Conditional rendering means showing UI based on conditions.

## Example

```jsx
function App() {
  const isLogin = true;

  return (
    <>
      {isLogin ? <h1>Welcome</h1> : <h1>Please Login</h1>}
    </>
  );
}
````

---

# List Rendering

List rendering means displaying multiple items using `map()`.

## Example

```jsx id="z9m2wr"
const users = ["Krupa", "Rahul", "Aman"];

function App() {
  return (
    <ul>
      {users.map((user, index) => (
        <li key={index}>{user}</li>
      ))}
    </ul>
  );
}
```

---

# What is Key Prop & Why It’s Important?

`key` is a special prop used to uniquely identify list items.

React uses keys to:

* Track items
* Update UI efficiently
* Avoid unnecessary re-render

---

## Best Practice

```jsx id="v3p7lx"
<li key={user.id}>{user.name}</li>
```

Avoid using index as key when list changes dynamically.

---

# When Re-render Happens?

React component re-renders when:

* State changes
* Props change
* Parent component re-renders
* Context value changes

---

## Example

```jsx id="i7w2qb"
setCount(count + 1);
```

State update triggers re-render.

---

# Interview One-Line Answer

> React re-renders components whenever state, props, or context values change to update the UI efficiently.

# Events & Styling in React

# Handling Events

React events are used to handle user actions like:
- Click
- Change
- Submit
- Mouse events

---

## Example

```jsx
function App() {

  const handleClick = () => {
    alert("Button Clicked");
  };

  return (
    <button onClick={handleClick}>
      Click Me
    </button>
  );
}
````

# Synthetic Events in React

## What are Synthetic Events?

Synthetic Events are React’s wrapper around native browser events.

React creates its own event system to make events work the same across all browsers.

---

## Why React Uses Synthetic Events?

Because different browsers handle events differently.

* Synthetic Event means React ka own event system.
* React browser ke original events ko wrap karke ek common event object banata hai.
* Isse har browser me events same tarike se work karte hain.


Synthetic Events provide:
- Cross-browser compatibility
- Better performance
- Same behavior in all browsers

Why React Uses It?

* Different browsers events ko differently handle karte hain
* React sabko same behavior deta hai
* Performance bhi improve hoti hai
---

## Example

```jsx
function App() {

  const handleClick = (e) => {
    console.log(e);
  };

  return <button onClick={handleClick}>Click</button>;
}
````

Here `e` is a Synthetic Event object.

---

## Common Synthetic Events

* onClick
* onChange
* onSubmit
* onMouseOver
* onKeyDown

---

## Interview One-Line Answer

> Synthetic Events are React’s cross-browser wrapper around native browser events that provide consistent event handling and better performance.


# Inline Styling

Inline styling in React is written using JavaScript objects.

---

## Example

```jsx id="q3v9zl"
function App() {
  return (
    <h1 style={{ color: "blue", fontSize: "30px" }}>
      Hello React
    </h1>
  );
}
```

---

# Dynamic Styling

Dynamic styling means changing styles based on conditions or state.

---

## Example

```jsx id="k5x2mp"
function App() {

  const isActive = true;

  return (
    <h1 style={{
      color: isActive ? "green" : "red"
    }}>
      Status
    </h1>
  );
}
```

---

# Interview One-Line Answer

> React handles events using Synthetic Events and supports inline and dynamic styling using JavaScript objects and conditional logic.



# Why Hooks Are Used Only at Top Level?

Hooks should always be used at the top level of a component.

We should not use hooks inside:
- loops
- conditions
- nested functions

---

## Wrong Example

```jsx
if (show) {
  useEffect(() => {
    console.log("Hello");
  }, []);
}
````

---

## Correct Example

```jsx id="v8m3kp"
useEffect(() => {
  if (show) {
    console.log("Hello");
  }
}, [show]);
```

---

# Why?

React tracks hooks by their order.

If hooks are used inside conditions or loops:

* Hook order may change
* React gets confused
* State may break

---

## Example

First render:

```text id="d3x9qw"
useState
useEffect
```

Second render:

```text id="c7p2zl"
useState
```

Now React cannot match hooks correctly.

---

# Rule

Hooks must always run:

* In same order
* On every render

---

# Interview One-Line Answer

> Hooks are used only at the top level because React depends on the hook call order to manage state and lifecycle correctly.


# What are Hooks?

Hooks are special React functions that allow functional components to use:
- State
- Lifecycle features
- Other React features

without using class components.

---

## Example

```jsx
const [count, setCount] = useState(0);
````

---

# Why Hooks?

Before hooks:

* State and lifecycle methods were used only in class components

Hooks make code:

* Simpler
* Reusable
* Cleaner
* Easier to maintain

---

## Benefits

* No need for class components
* Better code reusability
* Easier state management
* Cleaner component logic

---

# Rules of Hooks

## 1. Use Hooks Only at Top Level

Do not use hooks inside:

* loops
* conditions
* nested functions

Correct:

```jsx id="y8m2qw"
useEffect(() => {
  console.log("Hello");
}, []);
```

---

## 2. Use Hooks Only Inside React Functions

Hooks can be used only:

* Inside React functional components
* Inside custom hooks

---

## Wrong Example

```jsx id="g3x9pl"
function test() {
  useState();
}
```

---

# Common Hooks

* useState
* useEffect
* useContext
* useRef
* useMemo
* useCallback

---

# Interview One-Line Answer

> Hooks are React functions that allow functional components to use state and lifecycle features while following specific rules for consistent behavior.

# What is onChange in React?
onChange event input value change hone par trigger hota hai.

# What is onSubmit?
Form submit hone par onSubmit event call hota hai.

* React components ka naming convention mostly PascalCase hota hai.
Example: UserCard.jsx, Navbar.jsx.
* Component folders bhi generally PascalCase me rakhte hain, while utility folders lowercase/camelCase me hote hain like utils, hooks, services,components.



# Lighthouse / DevTools Ka Use Kaise Karte Ho? (Interview Purpose)

---

# 1. What is Chrome DevTools?

Chrome DevTools browser ka built-in debugging tool hai.

Use hota hai:
- Debugging
- Performance checking
- API testing
- CSS inspection
- Memory analysis
- Network monitoring

---

# Common DevTools Tabs

| Tab | Purpose |
|---|---|
| Elements | HTML/CSS inspect |
| Console | Errors & logs |
| Network | API requests |
| Application | LocalStorage/Cookies |
| Performance | Performance analysis |
| Sources | Debug JS code |

---

# 2. DevTools Kaise Use Karte Ho?

## Interview Answer

“I use Chrome DevTools for:
- Debugging UI issues
- Checking API calls
- Monitoring network requests
- Analyzing performance
- Inspecting elements
- Finding console errors”

---

# 3. API Debugging Kaise Karte Ho?

## Network Tab

Check:
- API URL
- Request payload
- Response data
- Status code
- Headers
- Failed requests

---

# Example

```text id="p2b3f4"
Network Tab
   ↓
Click API
   ↓
Check:
- Response
- Headers
- Payload
- Timing
````

---

# 4. Console Tab Use

Use for:

* Error debugging
* Logs checking
* Runtime issue detection

---

# Example

```jsx id="l7g8h9"
console.log(data)
console.error(error)
```

---

# 5. Lighthouse Kya Hai?

Lighthouse ek auditing tool hai jo:

* Performance
* Accessibility
* SEO
* Best Practices

analyze karta hai.

---

# Lighthouse Metrics

| Metric         | Meaning                 |
| -------------- | ----------------------- |
| Performance    | App speed               |
| Accessibility  | Accessibility support   |
| Best Practices | Secure coding practices |
| SEO            | Search optimization     |

---

# 6. Lighthouse Kaise Run Karte Ho?

## Steps

```text id="x1y2z3"
Open Website
   ↓
Right Click → Inspect
   ↓
Lighthouse Tab
   ↓
Generate Report
```

---

# 7. Lighthouse Se Kya Check Karte Ho?

## Performance Issues

* Large bundle size
* Slow loading
* Unused JS
* Heavy images
* Blocking resources

---

# Optimization Techniques

✅ Lazy loading
✅ Code splitting
✅ Image optimization
✅ Memoization
✅ API optimization

---

# 8. Performance Optimization Example

## Before

Large component loading at once ❌

---

## After

```jsx id="a4s5d6"
const Home = lazy(() => import("./Home"))
```

Using:

* Lazy loading
* Suspense

---

# 9. Common DevTools Features

---

# Element Inspection

```text id="e4r5t6"
Inspect Element
   ↓
Edit CSS Live
```

---

# Device Testing

Responsive mode for:

* Mobile
* Tablet
* Desktop

---

# Local Storage Check

```text id="u7i8o9"
Application Tab
   ↓
LocalStorage
```

---

# 10. Production Bug Debugging

## Interview Answer

“If production issue comes:

* First check console errors
* Then verify API calls in Network tab
* Analyze failed requests
* Check recent deployment changes
* Reproduce issue locally
* Fix and test in staging”

---

# Short Interview Answer

“I use Chrome DevTools for debugging UI, checking API requests, monitoring performance, and inspecting errors.
I use Lighthouse for performance auditing and identifying optimization opportunities.”

---

# Professional One-Liners

## DevTools

“DevTools helps me debug UI, API, and performance-related issues efficiently.”

---

## Lighthouse

“I use Lighthouse reports to improve performance, accessibility, and best practices.”

---


# Q1. Which DevTools tab do you use most?

## Answer

“Mostly Network, Console, and Elements tabs.”

---

# Q2. How do you debug API issues?

## Answer

“I use the Network tab to inspect request payload, response data, headers, and status codes.”

