Maine saare common topics ko combine karke ek clean aur easy-to-revise single markdown notes file bana diya hai — jisme duplicate topics remove karke proper interview-oriented explanations rakhe gaye hain.
File source: 

# 📘 Redux Toolkit Complete Interview Notes (Combined & Clean Version)

---

## 📌 Redux

### 🔹 What is Redux?

Redux is a state management library used to manage global state in React applications.

### 🔹 Why Redux?

Without Redux:

❌ Props drilling
❌ Difficult state sharing

With Redux:

✅ Centralized state
✅ Easy data sharing
✅ Better scalability

### 🎯 Interview Answer

Redux is used to manage and share global state across React applications.

---

# 📘 Redux Toolkit (RTK)

## 🔹 What is Redux Toolkit?

Redux Toolkit is the official modern way to write Redux.

### 🔹 Benefits

✅ Less boilerplate
✅ Easier setup
✅ Built-in middleware
✅ Better developer experience

### 🎯 Interview Answer

Redux Toolkit simplifies Redux development and reduces boilerplate code.

---

# 📘 Global State

## 🔹 What is Global State?

Data shared across multiple components.

### 🔹 Examples

* User data
* Theme
* Cart items
* Authentication

### 🎯 Interview Answer

Global state is shared application data accessible from multiple components.

---

# 📘 State Management

## 🔹 What is State Management?

Managing and updating application data/state.

### 🎯 Interview Answer

State management is the process of storing, updating, and sharing application state.

---

# 📘 Store

## 🔹 What is Store?

Central place where Redux state is stored.

### 🔹 Example

```js
const store = configureStore({
  reducer: reducer,
});
```

### 🎯 Interview Answer

Store is the central container that holds the complete Redux state.

---

# 📘 configureStore

## 🔹 What is configureStore?

Redux Toolkit function used to create Redux store.

### 🔹 Benefits

✅ Easy setup
✅ DevTools support
✅ Middleware included
✅ Cleaner configuration

### 🔹 Example

```js
const store = configureStore({
  reducer: reducer,
});
```

### 🎯 Interview Answer

configureStore creates and configures Redux store with simplified setup.

---

# 📘 Reducer

## 🔹 What is Reducer?

Reducer is a function that updates state based on actions.

### 🔹 Example

```js
(state, action) => newState
```

### 🎯 Interview Answer

Reducer is a function that takes current state and action and returns updated state.

---

# 📘 Root Reducer

## 🔹 What is Root Reducer?

Main reducer that combines all reducers.

### 🔹 Example

```js
const rootReducer = combineReducers({
  user: userReducer,
  cart: cartReducer,
});
```

### 🎯 Interview Answer

Root reducer combines multiple reducers into one main reducer.

---

# 📘 combineReducers

## 🔹 What is combineReducers?

Used to combine multiple reducers into a single reducer.

### 🔹 Example

```js
combineReducers({
  auth: authReducer,
  cart: cartReducer,
});
```

### 🔹 Why Use?

✅ Better code organization
✅ Scalable architecture
✅ Separate feature reducers

### 🎯 Interview Answer

combineReducers combines multiple reducers into one reducer function.

---

# 📘 Action

## 🔹 What is Action?

Action is an object describing what happened.

### 🔹 Example

```js
{
  type: "increment";
}
```

### 🎯 Interview Answer

Action is an object that describes an event in the application.

---

# 📘 Dispatch

## 🔹 What is Dispatch?

Dispatch sends actions to reducers.

### 🔹 Example

```js
dispatch(increment());
```

### 🎯 Interview Answer

Dispatch is used to send actions to reducers for updating state.

---

# 📘 createSlice

## 🔹 What is createSlice?

Redux Toolkit function that creates:

✅ Reducer
✅ Actions
✅ Action types

### 🔹 Example

```js
const counterSlice = createSlice({
  name: "counter",

  initialState: {
    value: 0,
  },

  reducers: {
    increment: (state) => {
      state.value += 1;
    },
  },
});
```

### 🎯 Interview Answer

createSlice automatically creates reducers and actions in one place.

---

# 📘 useSelector

## 🔹 What is useSelector?

Used to read Redux store state.

### 🔹 Example

```js
const count = useSelector(
  (state) => state.counter.value
);
```

### 🎯 Interview Answer

useSelector is used to access Redux state from components.

---

# 📘 useDispatch

## 🔹 What is useDispatch?

Used to dispatch Redux actions.

### 🔹 Example

```js
dispatch(increment());
```

### 🎯 Interview Answer

useDispatch is used to dispatch Redux actions.

---

# 📘 Middleware

## 🔹 What is Middleware?

Middleware is a processing layer between dispatch and reducer.

### 🔹 Uses

✅ API calls
✅ Logging
✅ Async operations

### 🎯 Interview Answer

Middleware processes actions before they reach reducers.

---

# 📘 Redux Thunk

## 🔹 What is Redux Thunk?

Middleware used for asynchronous operations.

### 🔹 Examples

* API calls
* Delayed actions
* Async requests

### 🔹 Important Point

Redux Toolkit already includes thunk by default.

### 🎯 Interview Answer

Redux Thunk handles asynchronous logic like API calls in Redux.

---

# 📘 createAsyncThunk

## 🔹 What is createAsyncThunk?

Redux Toolkit helper for async API handling.

### 🔹 Example

```js
createAsyncThunk();
```

### 🎯 Interview Answer

createAsyncThunk simplifies asynchronous API calls in Redux Toolkit.

---

# 📘 Redux Persist

## 🔹 What is Redux Persist?

Used to save Redux state in browser storage.

### 🔹 Why Use?

Without Persist:

❌ State resets on refresh

With Persist:

✅ Data remains after refresh

### 🎯 Interview Answer

Redux Persist stores Redux state in browser storage so data remains after refresh.

---

# 📘 persistReducer

## 🔹 What is persistReducer?

Wraps reducer to enable persistence.

### 🔹 Example

```js
persistReducer(
  persistConfig,
  rootReducer
);
```

### 🎯 Interview Answer

persistReducer wraps reducers and enables automatic state persistence.

---

# 📘 persistStore

## 🔹 What is persistStore?

Creates persisted Redux store.

### 🔹 Example

```js
const persistor = persistStore(store);
```

### 🎯 Interview Answer

persistStore creates persisted Redux store and manages rehydration.

---

# 📘 PersistGate

## 🔹 What is PersistGate?

Prevents app rendering until persisted data loads.

### 🔹 Example

```jsx
<PersistGate
  loading={null}
  persistor={persistor}
>
  <App />
</PersistGate>
```

### 🎯 Interview Answer

PersistGate delays app rendering until persisted Redux state is restored.

---

# 📘 localStorage

## 🔹 What is localStorage?

Browser storage used to permanently store data.

### 🔹 Example

```js
localStorage.setItem("token", token);
```

### 🎯 Interview Answer

localStorage stores data in browser even after refresh.

---

# 📘 State Persistence

## 🔹 What is State Persistence?

Maintaining state after page refresh.

### 🎯 Interview Answer

State persistence means keeping application state even after refresh.

---

# 📘 Logout Reset

## 🔹 What is Logout Reset?

Clearing Redux state during logout.

### 🔹 Example

```js
state = undefined;
```

### 🔹 Why Use?

✅ Clear user data
✅ Secure logout
✅ Remove old session

### 🎯 Interview Answer

Logout reset clears Redux state when user logs out.

---

# 📘 Immer

## 🔹 What is Immer?

Redux Toolkit internally uses Immer.

### 🔹 Benefit

Allows writing mutation-style code safely.

### 🔹 Example

```js
state.count += 1;
```

### 🎯 Interview Answer

Immer allows mutable-style updates while maintaining immutability internally.

---

# 📘 Full Redux Flow

```txt
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

# 📘 Most Asked Redux Interview Questions

| Question               | Short Answer              |
| ---------------------- | ------------------------- |
| Why Redux?             | Global state management   |
| Why RTK?               | Less boilerplate          |
| What is Store?         | Central state container   |
| What is Reducer?       | Updates state             |
| What is Action?        | Describes event           |
| What is Dispatch?      | Sends action              |
| What is Middleware?    | Extra processing          |
| What is Redux Persist? | Saves state after refresh |
| What is createSlice?   | Creates reducer + actions |
| What is useSelector?   | Reads Redux state         |
| What is useDispatch?   | Dispatches actions        |
| What is Redux Thunk?   | Handles async logic       |
| What is PersistGate?   | Waits for persisted state |
| What is Logout Reset?  | Clears state on logout    |

# 📘 Redux Data Flow Explained

# 📌 What is Redux Data Flow?

Redux follows:

# 👉 Unidirectional Data Flow

Meaning:

Data flows in one direction only.

---

# 📌 Redux Flow Diagram

```txt id="’winiijlwm"
Component
   ↓
Dispatch(Action)
   ↓
Reducer
   ↓
Store Updated
   ↓
UI Re-render
```

---

# 📘 Step-by-Step Redux Data Flow

---

# 📌 1️⃣ Component Triggers Action

User button click karta hai.

---

# 📌 Example

```jsx id="’winiijlwm7"
<button
  onClick={() =>
    dispatch(increment())
  }
>
  Increment
</button>
```

---

# 📌 What Happens?

```txt id="’winiijlwm2"
dispatch(increment())
```

Action dispatch hota hai.

---

# 📘 2️⃣ Action Dispatch Hota Hai

---

# 📌 What is Action?

Action object hota hai jo batata hai:

# 👉 Kya hua?

---

# 📌 Example

```js id="’winiijlwm5"
{
  type: "counter/increment"
}
```

---

# 📌 Purpose

Reducer ko information dena.

---

# 📘 3️⃣ Reducer Action Receive Karta Hai

---

# 📌 What is Reducer?

Reducer current state aur action lekar:

# 👉 New state

return karta hai.

---

# 📌 Example

```js id="’winiijlwm0"
increment: (state) => {
  state.value += 1;
}
```

---

# 📌 What Happens?

Old state update hoti hai.

---

# 📘 4️⃣ Store Update Hota Hai

---

# 📌 What is Store?

Redux ka central storage.

---

# 📌 Example

```js id="’winiijlwm8"
{
  counter: {
    value: 1
  }
}
```

---

# 📌 Store Me New State Save Hoti Hai

---

# 📘 5️⃣ UI Automatically Re-render Hota Hai

---

# 📌 useSelector Detects Changes

```jsx id="’winiijlwm3"
const count =
  useSelector(
    (state) => state.counter.value
  );
```

---

# 📌 Result

UI automatically update ho jata hai.

---

# 📘 Complete Easy Example

---

# 📌 Slice

```js id="’winiijlwm6"
import {
  createSlice
} from "@reduxjs/toolkit";

const counterSlice =
  createSlice({
    name: "counter",

    initialState: {
      value: 0
    },

    reducers: {
      increment: (state) => {
        state.value += 1;
      }
    }
  });

export const { increment } =
  counterSlice.actions;

export default
  counterSlice.reducer;
```

---

# 📌 Component

```jsx id="’winiijlwm1"
import {
  useSelector,
  useDispatch
} from "react-redux";

import {
  increment
} from "./counterSlice";

function Counter() {
  const count = useSelector(
    (state) => state.counter.value
  );

  const dispatch = useDispatch();

  return (
    <div>
      <h1>{count}</h1>

      <button
        onClick={() =>
          dispatch(increment())
        }
      >
        Increment
      </button>
    </div>
  );
}
```

---

# 📘 How This Example Works?

---

# 🔥 Step 1

User clicks button.

---

# 🔥 Step 2

```js id="’winiijlwm9"
dispatch(increment())
```

action dispatch hota hai.

---

# 🔥 Step 3

Reducer receives action.

---

# 🔥 Step 4

State update hoti hai.

```js id="’winiijlwm4"
value: 0 → value: 1
```

---

# 🔥 Step 5

Store updated.

---

# 🔥 Step 6

`useSelector()` updated value detect karta hai.

---

# 🔥 Step 7

UI automatically re-render hota hai.

---

# 📘 Important Redux Data Flow Point

Redux data flow:

# 👉 Always One Direction

```txt id="’winiijlwmq"
Component
→ Action
→ Reducer
→ Store
→ UI
```

---

# 📘 Why Redux Uses One-Way Data Flow?

✅ Predictable state
✅ Easy debugging
✅ Better scalability
✅ Easier testing

---

# 📘 Real Interview Questions

---

# ❓ What is Redux Data Flow?

### ✅ Answer:

Redux follows a unidirectional data flow where actions are dispatched from components, reducers update the state, the store gets updated, and the UI re-renders automatically.

---

# ❓ Explain Redux Flow Step-by-Step.

### ✅ Answer:

1. Component dispatches action
2. Action reaches reducer
3. Reducer updates state
4. Store gets updated
5. UI re-renders using updated state

---

# ❓ Why Redux Uses Unidirectional Data Flow?

### ✅ Answer:

Redux uses unidirectional data flow for predictable state management, easier debugging, and better scalability.

---

# 📘 Normal Redux vs Redux Toolkit

---

# 📌 What is Normal Redux?

Traditional Redux approach where:

❌ Actions manually create karne padte the
❌ Reducers alag likhne padte the
❌ Store setup complex hota tha

---

# 📌 Example — Normal Redux

## Action

```js id="’winiijlwm2"
const increment = () => {
  return {
    type: "INCREMENT"
  };
};
```

---

## Reducer

```js id="’winiijlwm5"
function counterReducer(
  state = 0,
  action
) {
  switch (action.type) {
    case "INCREMENT":
      return state + 1;

    default:
      return state;
  }
}
```

---

# 📌 Problems in Normal Redux

❌ Too much boilerplate
❌ Multiple files
❌ Hard setup
❌ Manual immutable updates

---

# 📘 What is Redux Toolkit?

Redux Toolkit is the official modern way to write Redux.

---

# 📌 Example — Redux Toolkit

```js id="’winiijlwm0"
import {
  createSlice
} from "@reduxjs/toolkit";

const counterSlice =
  createSlice({
    name: "counter",

    initialState: {
      value: 0
    },

    reducers: {
      increment: (state) => {
        state.value += 1;
      }
    }
  });

export const { increment } =
  counterSlice.actions;

export default
  counterSlice.reducer;
```

---

# 📌 RTK Advantages

✅ Less boilerplate
✅ Easier setup
✅ Cleaner code
✅ Built-in Immer
✅ Built-in Thunk

---

# 📘 Normal Redux vs Redux Toolkit Table

| Normal Redux             | Redux Toolkit          |
| ------------------------ | ---------------------- |
| More boilerplate         | Less boilerplate       |
| Manual actions           | Auto-generated actions |
| Complex setup            | Easy setup             |
| Manual immutable updates | Immer included         |
| Multiple files           | Cleaner structure      |
| Thunk setup manually     | Thunk included         |

---

# 📌 Important Point

Today:

# 👉 Redux Toolkit is officially recommended by Redux team.

---

# 🎯 Interview Answers

---

# ❓ Difference Between Redux and Redux Toolkit?

### ✅ Answer:

Redux Toolkit is the modern official approach for Redux that simplifies Redux development by reducing boilerplate and providing built-in utilities like createSlice and configureStore.

---

# ❓ Why Redux Toolkit is Better?

### ✅ Answer:

Redux Toolkit provides easier setup, less boilerplate code, built-in async support, and cleaner state management compared to traditional Redux.

---

# ❓ Why Redux Toolkit was introduced?

### ✅ Answer:

Redux Toolkit was introduced to solve Redux complexity and reduce excessive boilerplate code.


# 📘 createAsyncThunk in Redux Toolkit

---

# 📌 What is createAsyncThunk?

`createAsyncThunk` Redux Toolkit ka function hai jo:

# 👉 Async operations

handle karne ke liye use hota hai.

Mostly used for:

✅ API calls
✅ Async requests
✅ Server data fetching

---

# 📌 Why createAsyncThunk is Needed?

Without `createAsyncThunk`:

❌ Loading state manually handle karna padta hai
❌ Success/error actions manually create karne padte hain
❌ Boilerplate code jyada hota hai

---

# 📌 Solution

`createAsyncThunk` automatically create karta hai:

✅ pending
✅ fulfilled
✅ rejected

actions.

---

# 📘 Syntax

```js id="’winiijlwm"
createAsyncThunk(
  "actionName",
  async () => {}
)
```

---

# 📘 Example

---

# 🔥 Step 1 — Create Async Thunk

```js id="’winiijlwm7"
import {
  createAsyncThunk
} from "@reduxjs/toolkit";

export const fetchUsers =
  createAsyncThunk(
    "users/fetchUsers",

    async () => {
      const response =
        await fetch(
          "https://jsonplaceholder.typicode.com/users"
        );

      return response.json();
    }
  );
```

---

# 📌 What Happens Here?

```js id="’winiijlwm2"
fetchUsers
```

API call karega aur data return karega.

---

# 📘 Step 2 — Handle States in extraReducers

```js id="’winiijlwm5"
import {
  createSlice
} from "@reduxjs/toolkit";

import { fetchUsers }
from "./userThunk";

const userSlice =
  createSlice({
    name: "users",

    initialState: {
      users: [],
      loading: false,
      error: null
    },

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

            state.users =
              action.payload;
          }
        )

        .addCase(
          fetchUsers.rejected,
          (state, action) => {
            state.loading = false;

            state.error =
              action.error.message;
          }
        );
    }
  });

export default
  userSlice.reducer;
```

---

# 📘 Step 3 — Dispatch Async Thunk

```jsx id="’winiijlwm0"
import {
  useDispatch
} from "react-redux";

import {
  fetchUsers
} from "./userThunk";

function App() {
  const dispatch = useDispatch();

  return (
    <button
      onClick={() =>
        dispatch(fetchUsers())
      }
    >
      Fetch Users
    </button>
  );
}
```

---

# 📘 How createAsyncThunk Works?

---

# 🔥 Step 1

Thunk dispatch hota hai.

```js id="’winiijlwm8"
dispatch(fetchUsers())
```

---

# 🔥 Step 2

Automatically:

```txt id="’winiijlwm3"
pending
```

action dispatch hota hai.

---

# 🔥 Step 3

API call hoti hai.

---

# 🔥 Step 4

If success:

```txt id="’winiijlwm6"
fulfilled
```

action dispatch hota hai.

---

# 🔥 Step 5

If error:

```txt id="’winiijlwm1"
rejected
```

action dispatch hota hai.

---

# 📘 Three Important States

| State     | Meaning |
| --------- | ------- |
| pending   | Loading |
| fulfilled | Success |
| rejected  | Error   |

---

# 📌 Why extraReducers Used?

Async actions slice ke reducers me directly nahi hote.

Isliye:

# 👉 extraReducers

use karte hain.

---

# 📘 Benefits of createAsyncThunk

✅ Less boilerplate
✅ Easy async handling
✅ Automatic action types
✅ Cleaner code
✅ Better error handling

---

# 📘 Real Use Cases

✅ Fetch users
✅ Login API
✅ Product API
✅ Dashboard data

---

# 📘 Difference Between reducers and extraReducers

| reducers             | extraReducers       |
| -------------------- | ------------------- |
| Normal sync actions  | Async thunk actions |
| Slice ke actions     | External actions    |
| increment, decrement | pending, fulfilled  |

---

# 🎯 Interview Answers

---

# ❓ What is createAsyncThunk?

### ✅ Answer:

`createAsyncThunk` is a Redux Toolkit function used for handling asynchronous operations like API calls.

---

# ❓ Why use createAsyncThunk?

### ✅ Answer:

createAsyncThunk reduces boilerplate code by automatically generating pending, fulfilled, and rejected action types for async operations.

---

# ❓ What are pending, fulfilled, and rejected in createAsyncThunk?

### ✅ Answer:

* pending → API request started
* fulfilled → API success
* rejected → API failed

---

# ❓ Why use extraReducers with createAsyncThunk?

### ✅ Answer:

extraReducers are used to handle actions generated by createAsyncThunk because those actions are created outside the slice reducers.

# 📘 Advanced Redux Interview Notes

---

# 📘 Redux Me Performance Optimization Kaise Karte Ho?

---

# 📌 Why Performance Optimization Needed?

Large Redux apps me:

❌ Unnecessary re-renders
❌ Slow UI
❌ Large state updates

problem create kar sakte hain.

---

# 📌 Common Redux Performance Optimization Techniques

---

# 🔥 1️⃣ State Ko Properly Split Karna

Large single state avoid karo.

---

# ✅ Good Example

```js id="’winiijlwm"
{
  auth: {},
  cart: {},
  products: {}
}
```

---

# 📌 Benefit

Sirf required component re-render hoga.

---

# 🔥 2️⃣ Memoized Selectors Use Karna

Using:

# 👉 Reselect

---

# 🔥 3️⃣ Normalized State

Nested state avoid karte hain.

---

# 🔥 4️⃣ Avoid Unnecessary Re-renders

Using:

✅ React.memo
✅ useMemo
✅ useCallback

---

# 🔥 5️⃣ RTK Query Caching

API response cache hota hai.

---

# 📌 Important Point

Redux me har state update pe subscribed components re-render hote hain.

Optimization unnecessary renders reduce karta hai.

---

# 🎯 Interview Answer

## ❓ How do you optimize performance in Redux?

### ✅ Answer:

Redux performance can be optimized using normalized state, memoized selectors, proper store structure, React.memo, and caching techniques like RTK Query.

---

# 📘 Normalization of State Kya Hota Hai?

---

# 📌 Definition

Normalization means storing data in flat structure instead of deeply nested objects.

---

# ❌ Bad Example (Nested State)

```js id="’winiijlwm7"
{
  users: [
    {
      id: 1,
      posts: [
        {
          id: 101
        }
      ]
    }
  ]
}
```

---

# ✅ Good Example (Normalized)

```js id="’winiijlwm2"
{
  users: {
    1: {
      id: 1,
      name: "Krupa"
    }
  },

  posts: {
    101: {
      id: 101,
      userId: 1
    }
  }
}
```

---

# 📌 Benefits

✅ Faster updates
✅ Easier state management
✅ Less duplication
✅ Better performance

---

# 📌 Why Needed?

Nested state update difficult aur expensive hota hai.

---

# 🎯 Interview Answer

## ❓ What is normalization of state?

### ✅ Answer:

Normalization is the process of storing Redux state in a flat structured format to improve performance and simplify updates.

---

# 📘 Memoization Kya Hai? (Reselect)

---

# 📌 What is Memoization?

Memoization means:

# 👉 Reusing previously calculated result

instead of recalculating again.

---

# 📌 Why Needed?

Without memoization:

❌ Selectors har render pe recalculate honge.

---

# 📌 Solution

Using:

# 👉 Reselect

---

# 📌 Example

```js id="’winiijlwm5"
import { createSelector }
from "reselect";

const selectUsers =
  (state) => state.users;

const activeUsers =
  createSelector(
    [selectUsers],

    (users) => {
      return users.filter(
        (user) => user.active
      );
    }
  );
```

---

# 📌 How it Works?

Agar users state change nahi hua:

✅ Old result reuse hoga.

---

# 📌 Benefits

✅ Better performance
✅ Fewer recalculations
✅ Optimized rendering

---

# 🎯 Interview Answer

## ❓ What is memoization in Redux?

### ✅ Answer:

Memoization stores previously calculated selector results and prevents unnecessary recalculations using libraries like Reselect.

---

# 📘 Store Structure Kaise Design Karte Ho Large Apps Me?

---

# 📌 Best Practice

Feature-based structure use karte hain.

---

# 📌 Example Structure

```txt id="’winiijlwm0"
src
 ├── app
 │    └── store.js
 │
 ├── features
 │    ├── auth
 │    │    ├── authSlice.js
 │    │
 │    ├── cart
 │    │    ├── cartSlice.js
 │    │
 │    └── products
 │         ├── productSlice.js
```

---

# 📌 Why This Structure?

✅ Scalable
✅ Easy maintenance
✅ Better organization

---

# 📌 Important Point

Store ko:

# 👉 Feature-wise split

karna best practice hai.

---

# 🎯 Interview Answer

## ❓ How do you design Redux store structure for large apps?

### ✅ Answer:

In large applications, Redux store is usually organized feature-wise where each feature has its own slice, actions, and reducers for better scalability and maintainability.

---

# 📘 RTK Query Kya Hai?

---

# 📌 Definition

RTK Query Redux Toolkit ka powerful data fetching tool hai.

---

# 📌 Why RTK Query?

API handling simplify karta hai.

---

# 📌 Features

✅ Data fetching
✅ Caching
✅ Auto refetching
✅ Loading states
✅ Error handling

---

# 📌 Example

```js id="’winiijlwm8"
import {
  createApi,
  fetchBaseQuery
} from "@reduxjs/toolkit/query/react";

export const api =
  createApi({
    reducerPath: "api",

    baseQuery:
      fetchBaseQuery({
        baseUrl: "/api"
      }),

    endpoints: (builder) => ({
      getUsers:
        builder.query({
          query: () => "/users"
        })
    })
  });
```

---

# 📌 Usage

```js id="’winiijlwm3"
const {
  data,
  isLoading
} = useGetUsersQuery();
```

---

# 📌 Benefits

✅ Less boilerplate
✅ Built-in caching
✅ Better API handling

---

# 🎯 Interview Answer

## ❓ What is RTK Query?

### ✅ Answer:

RTK Query is a Redux Toolkit feature used for efficient API data fetching, caching, and server state management.

---

# 📘 Redux DevTools Ka Use Kya Hai?

---

# 📌 What is Redux DevTools?

Redux state debugging tool.

---

# 📌 What Can We See?

✅ Actions
✅ State changes
✅ Previous state
✅ Next state

---

# 📌 Benefits

✅ Easy debugging
✅ Time travel debugging
✅ Track dispatched actions

---

# 📌 Example

```txt id="’winiijlwm6"
Action Dispatched →
State Updated →
View Changes in DevTools
```

---

# 📌 Important Point

Redux Toolkit automatically enables Redux DevTools.

---

# 🎯 Interview Answer

## ❓ What is Redux DevTools used for?

### ✅ Answer:

Redux DevTools is used for debugging Redux applications by inspecting actions, state changes, and dispatched events.



