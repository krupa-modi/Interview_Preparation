# React State Management (Short Interview Notes)

## What is State?

State is data that changes in a React component.

When state changes, component re-renders automatically.

---

# useState

Used for simple local state.

```jsx
const [count, setCount] = useState(0);
````

Example:

* Counter
* Input field
* Toggle button

---

# useReducer

Used for complex state logic.

Best when:

* Multiple state updates
* Large forms
* Complex conditions

```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

---

# Prop Drilling

Passing data through many components unnecessarily.

```text
App → Parent → Child → GrandChild
```

Problem:
Data passes through all components even if they don't need it.

---

# Context API

Used to avoid prop drilling.

Provides global/shared state.

Example:

* Theme
* User data
* Language

---

# Redux / Redux Toolkit (RTK)

Used for large applications global state management.

Stores all app state in one central store.

Best for:

* Large scalable apps
* Complex data flow

RTK is modern Redux version with less code.

---

# Zustand

Lightweight alternative to Redux.

Simple and easy global state management.

---

# React Query / TanStack Query

Used for server/API state management.

Handles:

* API caching
* Loading
* Refetching
* Error handling

---

# When to Use What?

| Situation              | Use           |
| ---------------------- | ------------- |
| Simple local state     | useState      |
| Complex state logic    | useReducer    |
| Avoid prop drilling    | Context API   |
| Large app global state | Redux Toolkit |
| Simple global state    | Zustand       |
| API data               | React Query   |

---

# Important Interview Line

```text
useState is used for local state,
Context API for avoiding prop drilling,
Redux Toolkit for large global state,
and React Query for API/server state management.
```
