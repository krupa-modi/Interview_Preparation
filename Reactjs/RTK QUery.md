# RTK Query in React (Redux Toolkit Query)

# What is RTK Query?

RTK Query Redux Toolkit ka powerful feature hai jo API calling aur server data fetching ko easy banata hai.

Simple words me:

> RTK Query React application me API fetch, caching, loading aur error handling automatically karta hai.

---

# Full Form

```text
RTK = Redux Toolkit
````

```text
RTK Query = Redux Toolkit Query
```

---

# Why RTK Query is Used?

Normally API call karne ke liye:

* useEffect
* useState
* axios/fetch
* loading state
* error state

sab manually likhna padta hai.

RTK Query ye sab easy aur automatic bana deta hai.

---

# Without RTK Query

```text
API Call
↓
Loading State
↓
Error Handling
↓
Store Data
↓
Caching
↓
Refetch
```

Sab manually.

---

# With RTK Query

```text
Sirf endpoint likho
```

बाकी:

* fetching
* caching
* loading
* error handling
* refetching

automatic.

---

# Main Features

| Feature        | Description                |
| -------------- | -------------------------- |
| API Fetching   | API data fetch karta hai   |
| Caching        | Data cache karta hai       |
| Auto Refetch   | Data automatically refresh |
| Loading State  | isLoading deta hai         |
| Error Handling | isError deta hai           |
| Mutation       | POST/PUT/DELETE handle     |
| Performance    | Better optimization        |

---

# Install RTK Query

```bash
npm install @reduxjs/toolkit react-redux
```

---

# Folder Structure

```text
src
 ├── app
 │    └── store.js
 │
 ├── services
 │    └── api.js
 │
 ├── components
 │    └── Users.js
 │
 └── main.jsx
```

---

# Step 1: Create API Slice

# api.js

```jsx id="x2q9mk"
import { createApi, fetchBaseQuery } from "@reduxjs/toolkit/query/react";

export const api = createApi({

  reducerPath: "api",

  baseQuery: fetchBaseQuery({
    baseUrl: "https://jsonplaceholder.typicode.com/",
  }),

  endpoints: (builder) => ({

    getUsers: builder.query({
      query: () => "users",
    }),

  }),
});

export const { useGetUsersQuery } = api;
```

---

# Explanation

## createApi()

API service create karta hai.

---

## reducerPath

Redux store me key name.

```jsx id="y5k8nd"
reducerPath: "api"
```

---

## baseQuery

Base URL define karta hai.

```jsx id="b7q3vw"
baseQuery: fetchBaseQuery({
  baseUrl: "https://jsonplaceholder.typicode.com/",
})
```

---

## endpoints

Saare API endpoints yaha define hote hai.

---

## builder.query()

GET API ke liye use hota hai.

---

# Step 2: Configure Store

# store.js

```jsx id="p6r2tz"
import { configureStore } from "@reduxjs/toolkit";
import { api } from "../services/api";

export const store = configureStore({

  reducer: {
    [api.reducerPath]: api.reducer,
  },

  middleware: (getDefaultMiddleware) =>
    getDefaultMiddleware().concat(api.middleware),
});
```

---

# Why middleware?

RTK Query internally:

* caching
* refetching
* API lifecycle

handle karta hai.

---

# Step 3: Wrap App with Provider

# main.jsx

```jsx id="w9v4mc"
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

import { Provider } from "react-redux";
import { store } from "./app/store";

ReactDOM.createRoot(document.getElementById("root")).render(

  <Provider store={store}>
    <App />
  </Provider>

);
```

---

# Step 4: Use API in Component

# Users.jsx

```jsx id="d4m7qk"
import React from "react";
import { useGetUsersQuery } from "../services/api";

function Users() {

  const {
    data,
    error,
    isLoading,
  } = useGetUsersQuery();

  if (isLoading) {
    return <h1>Loading...</h1>;
  }

  if (error) {
    return <h1>Error...</h1>;
  }

  return (
    <div>

      {data.map((user) => (
        <h3 key={user.id}>
          {user.name}
        </h3>
      ))}

    </div>
  );
}

export default Users;
```

---

# What is useGetUsersQuery()?

Ye auto-generated hook hai.

```jsx id="u2x5fd"
useGetUsersQuery()
```

Automatically:

* API call
* loading
* error
* data fetch

sab handle karta hai.

---

# RTK Query Flow

```text id="n8z1wr"
Component Render
      ↓
useGetUsersQuery()
      ↓
API Request
      ↓
Data Fetch
      ↓
Cache Store
      ↓
UI Update
```

---

# Query vs Mutation

| Query         | Mutation         |
| ------------- | ---------------- |
| GET data      | POST/PUT/DELETE  |
| Fetch data    | Update data      |
| builder.query | builder.mutation |

---

# Mutation Example

# Add User API

```jsx id="e1n4pv"
addUser: builder.mutation({

  query: (newUser) => ({
    url: "users",
    method: "POST",
    body: newUser,
  }),

}),
```

---

# Export Hook

```jsx id="m5q8zk"
export const {
  useGetUsersQuery,
  useAddUserMutation,
} = api;
```

---

# Using Mutation

```jsx id="j3w6rx"
const [addUser] = useAddUserMutation();

const handleAdd = async () => {

  await addUser({
    name: "Krupa",
  });

};
```

---

# Important Auto States

| State     | Meaning       |
| --------- | ------------- |
| isLoading | API loading   |
| isSuccess | API success   |
| isError   | API failed    |
| data      | Response data |
| error     | Error object  |

---

# Benefits of RTK Query

| Benefit                | Description      |
| ---------------------- | ---------------- |
| Less Code              | Boilerplate kam  |
| Auto Caching           | Automatic cache  |
| Better Performance     | Re-render kam    |
| Easy API Handling      | Simple syntax    |
| Built-in Loading/Error | Extra state nahi |

---

# RTK Query vs Traditional Redux

| Traditional Redux      | RTK Query    |
| ---------------------- | ------------ |
| Manual API handling    | Automatic    |
| Extra reducers/actions | Less code    |
| Manual loading/error   | Built-in     |
| More boilerplate       | Minimal code |

---

# RTK Query vs React Query

| RTK Query             | React Query      |
| --------------------- | ---------------- |
| Redux based           | Independent      |
| Redux Toolkit ka part | Separate library |
| Centralized store     | Local cache      |

---

# Real World Use Cases

| Use Case        | Example         |
| --------------- | --------------- |
| User Data       | Fetch users     |
| Products        | E-commerce      |
| Dashboard       | Analytics       |
| Authentication  | Login/Register  |
| CRUD Operations | Add/Edit/Delete |

---

# Most Important Keywords

| Keyword        | Meaning            |
| -------------- | ------------------ |
| createApi      | API service create |
| fetchBaseQuery | Base API config    |
| endpoints      | API list           |
| query          | GET request        |
| mutation       | POST/PUT/DELETE    |
| caching        | Store API data     |

---

# Interview Questions

# What is RTK Query?

RTK Query Redux Toolkit ka data fetching tool hai jo API calling, caching aur loading/error handling easy banata hai.

---

# Why use RTK Query?

Boilerplate code kam karne aur automatic caching/refetching ke liye.

---

# Difference between Query and Mutation?

| Query      | Mutation        |
| ---------- | --------------- |
| Fetch data | Change data     |
| GET        | POST/PUT/DELETE |

---

# What is createApi?

API service create karne ke liye use hota hai.

---

# What is fetchBaseQuery?

Base URL aur fetch configuration define karta hai.

---

# What is caching in RTK Query?

Fetched data ko store karna taaki baar baar API call na ho.

---

# Easy Interview Answer

RTK Query Redux Toolkit ka powerful feature hai jo API fetching, caching aur server state management ko easy aur optimized banata hai.

---

# One Line Definition

RTK Query React me APIs handle karne ka modern aur optimized way hai.

```
RTK Query sirf CRUD ke liye nahi hai.ye React applications me API fetching, caching, authentication, polling, pagination aur server state management ke liye use hota hai.
```