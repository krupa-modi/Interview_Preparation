# 📘 React Router Scenario Based Interview Questions

# 📌 Agar User Login Nahi Hai To Route Access Kaise Rokoge?

## 🔹 Solution

Protected Routes use karte hain.

Authentication check karte hain before rendering route.

Agar user logged in nahi hai:

✅ Redirect to Login Page

---

# 📌 Example

```jsx id="jlwm1m"
import {
  Navigate
} from "react-router-dom";

function ProtectedRoute({
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

# 📌 Usage

```jsx id="jlwm7n"
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

If token exists:

✅ Route access allowed

Else:

❌ Redirect to login page

---

# 🎯 Interview Answer

## ❓ Agar user login nahi hai to route access kaise rokoge?

### ✅ Answer:

Protected routes create karke authentication check karenge. Agar user authenticated nahi hoga to `Navigate` component se login page par redirect karenge.

---

# 📘 Page Refresh Pe State Kaise Maintain Karoge?

---

# 📌 Problem

React state refresh hone par reset ho jati hai.

---

# 📌 Common Solutions

✅ localStorage
✅ sessionStorage
✅ Redux Persist
✅ Context + Storage

---

# 📌 Example

## Save State

```jsx id="jlwm4d"
localStorage.setItem(
  "token",
  token
);
```

---

## Get State After Refresh

```jsx id="jlwm9f"
const token =
  localStorage.getItem("token");
```

---

# 📌 Why localStorage?

Because browser refresh ke baad bhi data persist rehta hai.

---

# 📌 Real Example

Login token save karte hain taaki refresh ke baad user logout na ho.

---

# 🎯 Interview Answer

## ❓ Page refresh pe state kaise maintain karoge?

### ✅ Answer:

State ko localStorage, sessionStorage, ya Redux Persist me store karke refresh ke baad restore karte hain.

---

# 📘 URL Change Hone Pe API Call Kaise Trigger Karoge?

---

# 📌 Solution

`useLocation` ya `useParams` ke saath `useEffect` use karte hain.

---

# 📌 Example Using useParams

```jsx id="jlwm2s"
import {
  useParams
} from "react-router-dom";

import {
  useEffect
} from "react";

function Product() {
  const { id } = useParams();

  useEffect(() => {
    fetchProduct(id);
  }, [id]);

  return <h1>Product</h1>;
}
```

---

# 📌 How it Works?

Whenever URL param changes:

```txt id="jlwm6x"
id changes
```

then:

```txt id="’winijlwm"
API call triggers
```

---

# 📌 Example URL

```txt id="’winiijlwm5"
/product/1
/product/2
```

---

# 🎯 Interview Answer

## ❓ URL change hone pe API call kaise trigger karoge?

### ✅ Answer:

useEffect ke dependency array me route params ya location add karte hain. URL change hone par API call automatically trigger hoti hai.

---

# 📘 Breadcrumb Navigation Kaise Banaoge?

---

# 📌 What is Breadcrumb?

Breadcrumb current page path show karta hai.

---

# 📌 Example

```txt id="’winiijlwm8"
Home > Products > Mobile
```

---

# 📌 Solution

`useLocation` use karke pathname split karte hain.

---

# 📌 Example

```jsx id="’winiijlwm2"
import {
  useLocation
} from "react-router-dom";

function Breadcrumb() {
  const location = useLocation();

  const paths =
    location.pathname.split("/");

  return (
    <div>
      {paths.map((path, index) => (
        <span key={index}>
          {path} /
        </span>
      ))}
    </div>
  );
}
```

---

# 📌 How it Works?

For URL:

```txt id="’winiijlwm0"
/products/mobile
```

Output:

```txt id="’winiijlwm7"
products / mobile
```

---

# 🎯 Interview Answer

## ❓ Breadcrumb navigation kaise banaoge?

### ✅ Answer:

Breadcrumb navigation useLocation hook ke pathname ko split karke dynamic links generate karke banaya jata hai.

---

# 📘 Deep Linking Kaise Handle Karte Ho?

---

# 📌 What is Deep Linking?

Deep linking means directly opening a specific page using URL.

---

# 📌 Example

```txt id="’winiijlwm1"
/product/10
```

User directly product page open kar sakta hai.

---

# 📌 How React Router Handles It?

React Router automatically route match karta hai.

---

# 📌 Important Requirement

Server configuration required hota hai.

Otherwise refresh pe:

❌ 404 error aa sakta hai.

---

# 📌 BrowserRouter Fix

Server ko configure karte hain to always serve:

```txt id="’winiijlwm4"
index.html
```

---

# 📌 Example

```jsx id="’winiijlwm9"
<Route
  path="/product/:id"
  element={<Product />}
/>
```

---

# 📌 Benefits

✅ Shareable URLs
✅ Bookmark support
✅ Better user experience

---

# 🎯 Interview Answer

## ❓ Deep linking kaise handle karte ho?

### ✅ Answer:

Deep linking React Router routes ke through handle hota hai. BrowserRouter use karte waqt server configuration bhi required hoti hai taaki page refresh par 404 error na aaye.


# 📘 Redux Scenario Based Interview Questions

---

# 📘 API Calls Kaise Manage Karte Ho Redux Me?

---

# 📌 Common Ways

Redux me API calls mostly handle karte hain using:

✅ createAsyncThunk
✅ Redux Thunk
✅ RTK Query
✅ Redux Saga

---

# 📌 Most Common Approach

Redux Toolkit me:

# 👉 createAsyncThunk

most commonly use hota hai.

---

# 📌 Example

```js id="’winiijlwm"
export const fetchUsers =
  createAsyncThunk(
    "users/fetchUsers",

    async () => {
      const response =
        await fetch("/users");

      return response.json();
    }
  );
```

---

# 📌 Why Use createAsyncThunk?

✅ Async handling easy
✅ Loading/error states easy
✅ Less boilerplate

---

# 📌 API Flow

```txt id="’winiijlwm7"
Dispatch Async Action
        ↓
API Call
        ↓
pending / fulfilled / rejected
        ↓
Store Update
        ↓
UI Re-render
```

---

# 🎯 Interview Answer

## ❓ How do you manage API calls in Redux?

### ✅ Answer:

API calls in Redux are commonly managed using createAsyncThunk, Redux Thunk, RTK Query, or Redux Saga. In Redux Toolkit, createAsyncThunk is the most commonly used approach.

---

# 📘 Multiple API Calls Ko Kaise Sync Karoge?

---

# 📌 Problem

Kabhi multiple APIs ek saath call karni hoti hain.

---

# 📌 Solution 1 — Promise.all

```js id="’winiijlwm2"
const [users, posts] =
  await Promise.all([
    fetch("/users"),
    fetch("/posts")
  ]);
```

---

# 📌 Benefit

Both APIs parallel run karti hain.

---

# 📌 Solution 2 — Multiple Async Thunks

```js id="’winiijlwm5"
dispatch(fetchUsers());

dispatch(fetchPosts());
```

---

# 📌 Solution 3 — Redux Saga

Complex API synchronization me Saga use hota hai.

---

# 📌 Example Use Cases

✅ Dashboard APIs
✅ Multiple widgets
✅ Analytics data

---

# 🎯 Interview Answer

## ❓ How do you synchronize multiple API calls in Redux?

### ✅ Answer:

Multiple API calls can be synchronized using Promise.all, multiple async thunks, or Redux Saga for more complex workflows.

---

# 📘 Loading, Error State Kaise Manage Karte Ho?

---

# 📌 Best Practice

Redux state me:

✅ loading
✅ error
✅ data

store karte hain.

---

# 📌 Example State

```js id="’winiijlwm0"
initialState: {
  users: [],
  loading: false,
  error: null
}
```

---

# 📌 Handling States

```js id="’winiijlwm8"
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
```

---

# 📌 UI Example

```jsx id="’winiijlwm3"
{
  loading && <h1>Loading...</h1>
}
```

---

# 🎯 Interview Answer

## ❓ How do you manage loading and error states in Redux?

### ✅ Answer:

Loading and error states are usually managed inside Redux state using loading, error, and data properties handled through async actions like createAsyncThunk.

---

# 📘 Large Scale App Me State Structure Kaise Design Karte Ho?

---

# 📌 Best Practice

Feature-based structure use karte hain.

---

# 📌 Example

```txt id="’winiijlwm6"
src
 ├── app
 │    └── store.js
 │
 ├── features
 │    ├── auth
 │    ├── products
 │    ├── cart
 │    └── users
```

---

# 📌 Why Feature-Based Structure?

✅ Scalable
✅ Maintainable
✅ Easy debugging
✅ Better organization

---

# 📌 Important Point

Large apps me:

# 👉 Separate slices per feature

best practice hai.

---

# 📌 Example Store Structure

```js id="’winiijlwm1"
{
  auth: {},
  cart: {},
  products: {},
  users: {}
}
```

---

# 🎯 Interview Answer

## ❓ How do you design Redux state structure for large applications?

### ✅ Answer:

In large applications, Redux state is usually organized feature-wise using separate slices for better scalability and maintainability.

---

# 📘 Duplicate API Calls Kaise Avoid Karte Ho?

---

# 📌 Problem

Same API multiple times call ho sakti hai.

---

# 📌 Solutions

---

# 🔥 1️⃣ RTK Query Caching

Automatically duplicate requests avoid karta hai.

---

# 🔥 2️⃣ Existing State Check

```js id="’winiijlwm9"
if (state.users.length > 0) {
  return;
}
```

---

# 🔥 3️⃣ Memoized Selectors

Using:

# 👉 Reselect

---

# 🔥 4️⃣ useEffect Dependency Control

Proper dependency array use karna.

---

# 📌 RTK Query Benefit

Same request dubara API hit nahi karega if cache available hai.

---

# 🎯 Interview Answer

## ❓ How do you avoid duplicate API calls in Redux?

### ✅ Answer:

Duplicate API calls can be avoided using RTK Query caching, checking existing Redux state before fetching, and controlling component re-renders properly.

---

# 📘 Data Caching Kaise Implement Karte Ho?

---

# 📌 What is Data Caching?

Already fetched data ko store karna taaki repeated API calls avoid ho.

---

# 📌 Best Solution

# 👉 RTK Query

---

# 📌 Example

```js id="’winiijlwm4"
const {
  data,
  isLoading
} = useGetUsersQuery();
```

---

# 📌 RTK Query Features

✅ Automatic caching
✅ Auto refetching
✅ Cache invalidation
✅ Better performance

---

# 📌 Manual Caching Example

Redux store me API response save karte hain.

---

# 📌 Benefit

✅ Faster UI
✅ Less API calls
✅ Better performance

---

# 🎯 Interview Answer

## ❓ How do you implement data caching in Redux?

### ✅ Answer:

Data caching in Redux is commonly implemented using RTK Query, which automatically caches API responses and prevents unnecessary API calls.

# 📘 Redux + Routing Scenario Based Interview Questions

---

# 📘 Route Change Hone Pe Redux State Kaise Update Karte Ho?

---

# 📌 Solution

React Router hooks + Redux dispatch use karte hain.

Mostly:

# 👉 useLocation()

---

# 📌 Example

```jsx id="’winiijlwm"
import {
  useLocation
} from "react-router-dom";

import {
  useEffect
} from "react";

const location = useLocation();

useEffect(() => {
  dispatch(setRoute(location.pathname));
}, [location]);
```

---

# 📌 What Happens?

Jab route change hota hai:

✅ Redux state update ho jata hai.

---

# 🎯 Interview Answer

Route changes ko detect karne ke liye useLocation use karte hain aur Redux dispatch se state update karte hain.

---

# 📘 URL Params Ko Redux Store Me Kaise Sync Karte Ho?

---

# 📌 Solution

Using:

# 👉 useParams()

---

# 📌 Example

```jsx id="’winiijlwm7"
const { id } = useParams();

useEffect(() => {
  dispatch(setProductId(id));
}, [id]);
```

---

# 📌 Why Use?

URL params ko globally access karna easy ho jata hai.

---

# 🎯 Interview Answer

URL params ko useParams se read karke Redux store me dispatch karte hain.

---

# 📘 Navigation Ke Time API Call Kaise Trigger Karte Ho?

---

# 📌 Solution

Route/params change detect karke API call trigger karte hain.

---

# 📌 Example

```jsx id="’winiijlwm2"
const { id } = useParams();

useEffect(() => {
  dispatch(fetchProduct(id));
}, [id]);
```

---

# 📌 What Happens?

URL change:

```txt id="’winiijlwm5"
/product/1 → /product/2
```

then:

✅ New API call trigger hoti hai.

---

# 🎯 Interview Answer

Navigation ke time useEffect aur route params/location changes ke through API calls trigger karte hain.

---

# 📘 Redux State Reset On Logout Kaise Karte Ho?

---

# 📌 Solution

Logout action pe Redux state clear karte hain.

---

# 📌 Example

```js id="’winiijlwm0"
const rootReducer =
  (state, action) => {
    if (
      action.type ===
      "user/logout"
    ) {
      state = undefined;
    }

    return appReducer(
      state,
      action
    );
  };
```

---

# 📌 Why Use?

✅ Old user data remove
✅ Secure logout
✅ Fresh session

---

# 🎯 Interview Answer

Logout action dispatch hone par Redux state ko undefined set karke reset karte hain.

---

# 📘 Persisted State (redux-persist) Ka Use Kya Hai?

---

# 📌 Definition

Redux state ko browser storage me save karta hai.

---

# 📌 Why Needed?

Page refresh ke baad bhi:

✅ Login state
✅ Cart data
✅ User info

maintain rehta hai.

---

# 📌 Example

```js id="’winiijlwm8"
persistReducer(
  persistConfig,
  rootReducer
)
```

---

# 📌 Storage Used

Usually:

# 👉 localStorage

---

# 🎯 Interview Answer

redux-persist Redux state ko localStorage/sessionStorage me save karta hai taaki refresh ke baad state maintain rahe.

