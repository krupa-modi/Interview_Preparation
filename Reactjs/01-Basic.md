
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


# 1. Compound Components Pattern in React

## Definition
Compound Components pattern means multiple components work together to manage one functionality.

It gives users flexible and clean component structure.

Example:
```jsx
<Modal>
  <Modal.Header />
  <Modal.Body />
  <Modal.Footer />
</Modal>
````

Here all child components are connected with the parent component.

---

## Why Use Compound Components?

* Better code readability
* Flexible UI structure
* Reusable components
* Avoid prop drilling

---

## Simple Example

```jsx
function Card({ children }) {
  return <div>{children}</div>;
}

Card.Title = function ({ children }) {
  return <h2>{children}</h2>;
};

Card.Body = function ({ children }) {
  return <p>{children}</p>;
};

export default function App() {
  return (
    <Card>
      <Card.Title>React</Card.Title>
      <Card.Body>Compound Components Example</Card.Body>
    </Card>
  );
}
```

---

## Interview Short Answer

Compound Components pattern allows multiple related components to work together under one parent component. It improves flexibility, readability, and reusability in React applications.

---

# 2. What are Children Props in React?

## Definition

`children` is a special prop in React used to pass components, text, or JSX between opening and closing tags of a component.

---

## Example

```jsx
function Wrapper({ children }) {
  return <div>{children}</div>;
}

export default function App() {
  return (
    <Wrapper>
      <h1>Hello React</h1>
    </Wrapper>
  );
}
```

Here:

```jsx
<h1>Hello React</h1>
```

is passed as `children`.

---

## Uses of Children Props

* Wrapper components
* Layout components
* Reusable UI components
* Compound Components pattern

---

## Interview Short Answer

Children props allow passing dynamic content inside components. It helps create reusable and flexible components in React.

---

# 3. Different Approaches for API Handling in React

## 1. Using Fetch API

```jsx
useEffect(() => {
  fetch("https://api.example.com/users")
    .then(res => res.json())
    .then(data => console.log(data));
}, []);
```

### Advantages

* Built into browser
* Simple to use

---

## 2. Using Axios

```jsx
import axios from "axios";

useEffect(() => {
  axios.get("https://api.example.com/users")
    .then(res => console.log(res.data));
}, []);
```

### Advantages

* Cleaner syntax
* Better error handling
* Request interceptors

---

## 3. Using Async/Await

```jsx
const fetchData = async () => {
  try {
    const res = await fetch("https://api.example.com/users");
    const data = await res.json();
    console.log(data);
  } catch (error) {
    console.log(error);
  }
};
```

---

## 4. Using React Query / TanStack Query

Used for:

* Caching
* Auto refetching
* API state management

---

## 5. Using Redux Thunk / Redux Toolkit

Used in large applications for centralized API handling.

---

## Interview Short Answer

In React, APIs can be handled using Fetch API, Axios, Async/Await, React Query, and Redux Toolkit depending on project size and requirements.

---

# 4. Explain JWT Authentication Flow

## Definition

JWT (JSON Web Token) is used for secure authentication between frontend and backend.

---

# JWT Authentication Flow

## Step 1: User Login

User enters:

* Email
* Password

Frontend sends request to backend.

```js
POST /login
```

---

## Step 2: Backend Verifies User

Backend checks credentials from database.

If valid:

* JWT token is generated

---

## Step 3: Token Sent to Frontend

Backend sends token:

```js
{
  token: "jwt_token_here"
}
```

---

## Step 4: Frontend Stores Token

Usually stored in:

* LocalStorage
* SessionStorage
* Cookies

---

## Step 5: Token Sent with API Requests

Frontend sends token in headers:

```js
Authorization: Bearer token
```

---

## Step 6: Backend Verifies Token

Backend checks:

* Token validity
* Expiry
* Signature

If valid:

* API response is returned

---

## Step 7: User Logout

Token removed from storage.

---

## Advantages of JWT

* Stateless authentication
* Secure communication
* Works well with React apps
* Easy API authorization

---

## Interview Short Answer

JWT authentication works by generating a token after login. The frontend stores the token and sends it with every API request. Backend verifies the token before giving access to protected resources.

---

# Why We Write `{ children }` Instead of `(children)` in React?

## Correct Way

```jsx
function Wrapper({ children }) {
  return <div>{children}</div>;
}
````

---

# Reason

React component always receives a single object called `props`.

Example:

```jsx
<Wrapper>
  <h1>Hello</h1>
</Wrapper>
```

Internally React sends:

```js
{
  children: <h1>Hello</h1>
}
```

So component receives:

```js
props
```

not directly `children`.

---

# If We Write Round Brackets

```jsx
function Wrapper(children) {
  return <div>{children}</div>;
}
```

Then `children` becomes full props object.

Meaning:

```js
children = {
  children: <h1>Hello</h1>
}
```

So output will not work properly.

---

# Correct Alternative

You can also write:

```jsx
function Wrapper(props) {
  return <div>{props.children}</div>;
}
```

Here:

* `props` = full object
* `props.children` = actual child content

---

# Why `{ children }` is Preferred?

This is called **object destructuring**.

```jsx
function Wrapper({ children })
```

means:

```js
const children = props.children;
```

Advantages:

* Cleaner code
* Short syntax
* Easy to read

---

# Interview Short Answer

React components receive a `props` object.
`{ children }` is object destructuring used to directly access `props.children`.
If we use `(children)`, it receives the entire props object instead of only children.

---
# Why Do We Use `{{ }}` in React?

In React, double curly braces `{{ }}` are mostly used for:

- Inline CSS styling
- Passing JavaScript objects

---

# 1. Inline CSS Styling

## Example

```jsx
<h1 style={{ color: "red", fontSize: "30px" }}>
  Hello React
</h1>
````

---

# Why Double Curly Braces?

## First `{ }`

Outer curly braces mean:
➡ "Write JavaScript inside JSX"

```jsx
style={ ... }
```

---

## Second `{ }`

Inner curly braces mean:
➡ JavaScript Object

```js
{
  color: "red",
  fontSize: "30px"
}
```

---

# Combined Meaning

```jsx
style={{ color: "red" }}
```

means:

```jsx
style={JavaScript Object}
```

---

# 2. Passing Object as Props

## Example

```jsx
const user = {
  name: "Krupa",
  age: 22
};

<Component data={user} />
```

Sometimes directly:

```jsx
<Component data={{ name: "Krupa", age: 22 }} />
```

Here also:

* Outer `{}` = JavaScript
* Inner `{}` = Object

---

# Important Difference

## Single Curly Braces `{}`

Used for:

* Variables
* Expressions
* Functions

Example:

```jsx
<h1>{name}</h1>
```

---

## Double Curly Braces `{{}}`

Used for:

* Objects
* Inline styles

Example:

```jsx
style={{ color: "blue" }}
```

---

# Interview Short Answer

In React, `{{}}` is used when we need to pass a JavaScript object inside JSX.
Outer `{}` represents JavaScript expression, and inner `{}` represents an object.

---

# 1. What is React and why is it efficient?

## What is React?

React is a JavaScript library used to build fast and interactive user interfaces, especially Single Page Applications (SPA).

It was developed by Meta Platforms.

React uses a component-based architecture, where UI is divided into reusable components.

Example:

* Navbar
* Sidebar
* Button
* Card

Each can be created as a separate component and reused anywhere.

---

## Why is React Efficient?

### 1. Virtual DOM

React uses a Virtual DOM instead of directly updating the Real DOM.

Process:

1. React creates a virtual copy of the UI.
2. When state changes, React compares old and new Virtual DOM.
3. Only changed elements are updated in the Real DOM.

Because updating the Real DOM is slow, React becomes faster and more efficient.

---

### 2. Reusable Components

Components can be reused multiple times.

Benefits:

* Less code
* Easy maintenance
* Faster development

---

### 3. One-Way Data Flow

Data moves from Parent → Child.

This makes:

* Debugging easier
* Application predictable
* State management simpler

---

### 4. Fast Rendering

React updates only necessary parts of the UI instead of reloading the full page.

This improves:

* Performance
* User experience

---

### Interview Short Answer

“React is a JavaScript library used for building user interfaces using reusable components. It is efficient because it uses Virtual DOM, which updates only changed parts of the UI instead of re-rendering the entire page.”

---

# 2. How does React work internally?

## Internal Working of React

### Step 1: Component Creation

Developer creates components using JSX.

Example:

```jsx
function App() {
  return <h1>Hello</h1>;
}
```

---

### Step 2: JSX Conversion

React converts JSX into normal JavaScript using Babel.

```jsx
<h1>Hello</h1>
```

becomes:

```js
React.createElement("h1", null, "Hello")
```

---

### Step 3: Virtual DOM Creation

React creates a Virtual DOM object from components.

Virtual DOM is a lightweight JavaScript representation of the Real DOM.

---

### Step 4: Diffing Algorithm

When state or props change:

* React creates a new Virtual DOM
* Compares it with the old Virtual DOM

This comparison process is called Diffing.

---

### Step 5: Reconciliation

React finds the exact changed elements and updates only those parts in the Real DOM.

This process is called Reconciliation.

---

### Step 6: UI Update

Finally, React updates the browser UI efficiently.

---

# Important Internal Concepts

## 1. Virtual DOM

A lightweight copy of the Real DOM.

Purpose:

* Faster updates
* Better performance

---

## 2. Diffing

Comparison between old and new Virtual DOM.

---

## 3. Reconciliation

Process of updating changed elements in Real DOM.

---

## 4. Fiber Architecture

React Fiber is React’s internal rendering engine.

Benefits:

* Better rendering
* Priority-based updates
* Smooth UI rendering

---

## Interview Short Answer

“React works by creating a Virtual DOM. When data changes, React compares old and new Virtual DOM using the Diffing algorithm and updates only changed parts in the Real DOM through Reconciliation, making the application fast and efficient.”


# Manipulating API Response Data in React

## What is API Response Manipulation?

API response manipulation means modifying or transforming the data received from an API before displaying it in the UI.

Common operations:

* Filtering data
* Mapping data
* Sorting data
* Combining multiple API responses
* Adding custom fields

---

# Example API Response

```js
[
  {
    id: 1,
    name: "John",
    age: 24
  },
  {
    id: 2,
    name: "Peter",
    age: 30
  }
]
```

---

# Manipulating Data in React

## Example

```jsx
import React, { useEffect, useState } from "react";

const Users = () => {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((res) => res.json())
      .then((data) => {

        // Manipulating API response
        const updatedUsers = data.map((user) => ({
          id: user.id,
          name: user.name.toUpperCase(),
          email: user.email,
        }));

        setUsers(updatedUsers);
      });
  }, []);

  return (
    <div>
      <h2>User List</h2>

      {users.map((user) => (
        <div key={user.id}>
          <p>{user.name}</p>
          <p>{user.email}</p>
        </div>
      ))}
    </div>
  );
};

export default Users;
```

---

# Important Interview Points

## Why manipulate API data?

* UI-friendly structure
* Remove unnecessary fields
* Improve performance
* Better readability

---

# Implementing Concurrent API Calls Based on IDs

## Scenario

First API gives user IDs.

```js
[1, 2, 3]
```

Then we call multiple APIs together using those IDs.

---

# Why Concurrent Calls?

Instead of calling APIs one by one:

* Faster performance
* Better user experience
* Reduced waiting time

---

# Example Using Promise.all

```jsx
import React, { useEffect, useState } from "react";

const UsersPosts = () => {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((res) => res.json())
      .then(async (users) => {

        // Extract user IDs
        const ids = users.map((user) => user.id);

        // Concurrent API calls
        const apiCalls = ids.map((id) =>
          fetch(`https://jsonplaceholder.typicode.com/posts/${id}`)
            .then((res) => res.json())
        );

        // Wait for all APIs
        const postsData = await Promise.all(apiCalls);

        setPosts(postsData);
      });
  }, []);

  return (
    <div>
      <h2>Posts Data</h2>

      {posts.map((post) => (
        <div key={post.id}>
          <p>{post.title}</p>
        </div>
      ))}
    </div>
  );
};

export default UsersPosts;
```

---

# Flow Explanation

```text
First API Call
      ↓
Get IDs
      ↓
Create Multiple API Calls
      ↓
Promise.all()
      ↓
Get All Responses Together
      ↓
Update UI
```

---

# Important Interview Points

## Promise.all

* Runs APIs in parallel
* Improves performance
* Returns result in same order

---

## Concurrent API Calls

* Better than sequential calls
* Reduces loading time

---

## Common Real-Time Use Cases

* Dashboard data
* User profile + posts + comments
* Product details + reviews
* Multiple analytics APIs

---

# Difference Between Sequential and Concurrent Calls

## Sequential

```js
await api1();
await api2();
await api3();
```

* Slow
* Waits one by one

---

## Concurrent

```js
await Promise.all([api1(), api2(), api3()]);
```

* Faster
* Runs together


# What is JSON?

## Definition

JSON stands for:

```text id="tr06a4"
JavaScript Object Notation
```

It is a lightweight format used to store and exchange data between:

* Frontend ↔ Backend
* Client ↔ Server
* APIs

---

# Example of JSON

```json id="d3cb0y"
{
  "name": "Krupa",
  "age": 22,
  "city": "Pune"
}
```

---

# Important Rules

* Data is written in `key : value` pairs
* Keys must be in double quotes `" "`
* JSON supports:

  * string
  * number
  * boolean
  * array
  * object
  * null

---

# Why JSON is Used?

* Easy to read
* Easy to transfer data
* Lightweight
* Mostly used in APIs

---

# API Example

```js id="0s38mk"
fetch("api/users")
```

Response usually comes in JSON format.

---

# Convert JavaScript Object → JSON

```js id="n4g8jl"
JSON.stringify(obj)
```

---

# Convert JSON → JavaScript Object

```js id="vqgxxf"
JSON.parse(data)
```

---

# Interview Answer

JSON is a lightweight data format used for storing and exchanging data between client and server. It is written in key-value pairs and commonly used in APIs.

---

# Important Interview Point

JSON is:

```text id="u2tx8r"
Data Format
NOT JavaScript Object
```
