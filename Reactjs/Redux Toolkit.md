# 📘 Redux Toolkit (RTK) — Complete Interview Notes

---
# 📌 What is Redux?

Redux is a state management library used to manage Global State in React applications.

---

# 📌 What is Global State?

Data shared between multiple components.

---

# 📌 Example

* User data
* Theme
* Cart items
* Authentication
* Products

---

# 📌 Problem Without Redux

Suppose:

```txt id="’winiijlwm"
App
 ├── Navbar
 ├── Product
 ├── Cart
 └── Checkout
```

If cart data needed everywhere:

❌ Props drilling problem

---

# 📌 Solution

Redux stores data in one central store. Any component can access it.

---

# 📘 What is Redux Toolkit (RTK)?

Redux Toolkit is the official recommended way to write Redux.

It simplifies Redux development.

---

# 📌 Why Redux Toolkit Introduced?

Traditional Redux had:

❌ Too much boilerplate
❌ Complex setup
❌ Many files
❌ Hard async handling

RTK solves all these issues.

---

# 📌 Redux Toolkit Main Features

| Feature          | Purpose                  |
| ---------------- | ------------------------ |
| configureStore   | Create Redux store       |
| createSlice      | Create reducer + actions |
| createAsyncThunk | API handling             |
| useSelector      | Read state               |
| useDispatch      | Update state             |

---

# 📘 Redux Flow

```txt id="’winiijlwm7"
Component
   ↓
Dispatch Action
   ↓
Reducer Updates State
   ↓
Store Updated
   ↓
UI Re-render
```

---

# 📘 Step-by-Step Redux Toolkit Setup

---

# 📌 Step 1 — Install Packages

```bash id="’winiijlwm2"
npm install @reduxjs/toolkit react-redux
```

# 📘 Step 2 — Create Store

# 📌 store.js

```js id="’winiijlwm5"
import { configureStore } from "@reduxjs/toolkit";

import counterReducer from "./counterSlice";

export const store =
  configureStore({
    reducer: {
      counter: counterReducer
    }
  });
```

---

# 📌 What is configureStore?

It creates Redux store easily.

---

# 📌 Benefits

✅ Easy setup
✅ Redux DevTools support
✅ Middleware included

---

# 🎯 Interview Answer

## ❓ What is configureStore?

### ✅ Answer:

`configureStore` is a Redux Toolkit function used to create and configure Redux store with simplified setup.

---

# 📘 Step 3 — Create Slice

---

# 📌 What is Slice?

Slice contains:

✅ State
✅ Reducers
✅ Actions

---

# 📌 counterSlice.js

```js id="’winiijlwm0"
import {createSlice} from "@reduxjs/toolkit";

const counterSlice =
  createSlice({
    name: "counter",
    initialState: {
      value: 0
    },

    reducers: {
      increment: (state) => {
        state.value += 1;
      },

      decrement: (state) => {
        state.value -= 1;
      }
    }
  });

export const {increment, decrement} = counterSlice.actions;

export default counterSlice.reducer;
```

---

# 📌 What is createSlice?

`createSlice()` automatically creates:

✅ Reducer
✅ Actions
✅ Action types

---

# 📌 Important Point

RTK internally uses:

# 👉 Immer

So direct state mutation syntax works safely.

---

# 🎯 Interview Answer

## ❓ What is createSlice?

### ✅ Answer:

`createSlice` is a Redux Toolkit function that automatically creates reducers, actions, and action types in a single place.

---

# 📘 Step 4 — Provide Store

---

# 📌 main.jsx

```jsx id="’winiijlwm8"
import ReactDOM from "react-dom/client";
import { Provider } from "react-redux";
import { store } from "./store";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root")).render(
  <Provider store={store}>
    <App />
  </Provider>
);
```

---

# 📌 What is Provider?

Makes Redux store available to entire app.

---

# 🎯 Interview Answer

## ❓ What is Provider in Redux?

### ✅ Answer:

Provider is a React Redux component that makes the Redux store accessible to all components.

---

# 📘 Step 5 — useSelector

---

# 📌 What is useSelector?

Used to read data from Redux store.

---

# 📌 Example

```jsx id="’winiijlwm3"
import {useSelector} from "react-redux";

function Counter() {
  const count = useSelector((state) => state.counter.value);

  return <h1>{count}</h1>;
}
```

---

# 🎯 Interview Answer

## ❓ What is useSelector?

### ✅ Answer:

`useSelector` is a React Redux hook used to access state data from the Redux store.

---

# 📘 Step 6 — useDispatch

---

# 📌 What is useDispatch?

Used to dispatch actions.

---

# 📌 Example

```jsx id="’winiijlwm6"
import {useDispatch} from "react-redux";
import {increment} from "./counterSlice";

function Counter() {
  const dispatch = useDispatch();

  return (
    <button
      onClick={() =>
        dispatch(increment())
      }
    >
      Increment
    </button>
  );
}
```

---

# 🎯 Interview Answer

## ❓ What is useDispatch?

### ✅ Answer:

`useDispatch` is a React Redux hook used to dispatch actions to update Redux state.

---

# 📘 Async API Calls in RTK

---

# 📌 Problem

Redux me async API handling difficult thi.

---

# 📌 Solution

Redux Toolkit provides:

# 👉 createAsyncThunk()

---

# 📌 Example

```js id="’winiijlwm1"
import { createAsyncThunk} from "@reduxjs/toolkit";

export const fetchUsers = createAsyncThunk("users/fetchUsers",async () => {
      const response = await fetch("https://jsonplaceholder.typicode.com/users" );
      return response.json();
    }
  );
```

---

# 📌 extraReducers

```js id="’winiijlwm9"
extraReducers: (builder) => {
  builder
    .addCase(
      fetchUsers.pending,
      (state) => {
        state.loading = true;
      }
    )

    .addCase(
      fetchUsers.fulfilled,
      (state, action) => {
        state.loading = false;
        state.users = action.payload;
      }
    )

    .addCase(
      fetchUsers.rejected,
      (state) => {
        state.loading = false;
      }
    );
}
```

---

# 📌 Async States

| State     | Meaning |
| --------- | ------- |
| pending   | Loading |
| fulfilled | Success |
| rejected  | Error   |

---

# 🎯 Interview Answer

## ❓ What is createAsyncThunk?

### ✅ Answer:

`createAsyncThunk` is a Redux Toolkit function used for handling asynchronous operations like API calls.

---

# 📘 Redux Toolkit Folder Structure

---

# 📌 Recommended Structure

```txt id="’winiijlwm4"
src
 ├── app
 │    └── store.js
 │
 ├── features
 │    └── counter
 │          ├── counterSlice.js
 │
 ├── components
 │
 └── App.js
```

---

# 📘 Important Redux Toolkit Concepts

---

# 📌 Store

Central place where state stored hota hai.

---

# 📌 Reducer

State update logic.

---

# 📌 Action

Describes what happened.

---

# 📌 Dispatch

Action send karta hai reducer ko.

---

# 📌 Slice

State + reducers + actions ka combination.

---

# 📘 Redux Toolkit Advantages

| Advantage             | Benefit              |
| --------------------- | -------------------- |
| Less Boilerplate      | Cleaner code         |
| Easy Setup            | Faster development   |
| Immer Support         | Safe mutation syntax |
| Better Async Handling | createAsyncThunk     |
| DevTools Support      | Easy debugging       |

---

# 📘 Redux Toolkit vs Context API

| Redux Toolkit             | Context API         |
| ------------------------- | ------------------- |
| Large apps                | Small apps          |
| Better performance        | Simpler setup       |
| Advanced state management | Basic state sharing |
| Middleware support        | No middleware       |

---

# 📘 Common Interview Questions

---

# ❓ Why Redux Toolkit over Redux?

### ✅ Answer:

Redux Toolkit reduces boilerplate code, simplifies setup, and provides better developer experience compared to traditional Redux.

---

# ❓ Why use Redux Toolkit?

### ✅ Answer:

Redux Toolkit is used for centralized state management, easier async handling, and scalable React applications.

---

# ❓ What is Slice?

### ✅ Answer:

A Slice is a Redux Toolkit feature that combines state, reducers, and actions into one unit.

---

# ❓ What is the role of useSelector?

### ✅ Answer:

useSelector reads data from Redux store.

---

# ❓ What is the role of useDispatch?

### ✅ Answer:

useDispatch sends actions to update Redux state.

---

# ❓ What is Redux Store?

### ✅ Answer:

Redux store is the central container that holds the application state.
