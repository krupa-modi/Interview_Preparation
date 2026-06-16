# React Query / TanStack Query Complete A to Z Guide

## What is React Query / TanStack Query?
Earlier its name was **React Query**.
Now officially it is called:

TanStack Query

But mostly companies/interviewers still say **React Query**.

---

# Why React Query Came?

Before React Query, developers used:

* `useEffect`
* `useState`
* axios/fetch manually

Example:

```js
useEffect(() => {
  fetchUsers();
}, []);
```

Problems:

* Loading manage manually
* Error manage manually
* Refetch manually
* Cache nahi hota
* Same API baar baar hit hoti
* Background update nahi hota
* Performance issue
* Boilerplate code bahot zyada

Isliye React Query bana.

---

# What React Query Does?

React Query handles:

* API calling
* Caching
* Loading state
* Error state
* Refetching
* Pagination
* Infinite scrolling
* Background sync
* Optimistic updates
* Mutation
* Retry
* Performance optimization

Automatically.

---

# Main Purpose

React Query ka main kaam hai:

> Server State Management

---

# What is Server State?

Data jo backend/database/API se aata hai.

Example:

* Users
* Products
* Todos
* Orders
* Posts

---

# What is Client State?

Frontend ke andar ka state.

Example:

* Modal open/close
* Theme
* Sidebar toggle
* Input field value

Ye React state handle karta hai.

---

# Difference Between Client State & Server State

| Client State         | Server State          |
| -------------------- | --------------------- |
| Local hota hai       | API se aata hai       |
| Fast change hota hai | Async hota hai        |
| useState se handle   | React Query se handle |
| Example: modal       | Example: users list   |

---

# Why Companies Use React Query?

Because:

* Performance fast
* API optimization
* Better UX
* Automatic caching
* Less code
* Cleaner architecture
* Better scalability

---

# Installation

## React Query Install

```bash
npm install @tanstack/react-query
```

---

# Devtools Install

```bash
npm install @tanstack/react-query-devtools
```

---

# Setup Step by Step

# Step 1: Create QueryClient

```js
import { QueryClient } from "@tanstack/react-query";

const queryClient = new QueryClient();
```

---

# Step 2: Wrap Application

```js
import { QueryClientProvider } from "@tanstack/react-query";

<QueryClientProvider client={queryClient}>
  <App />
</QueryClientProvider>
```

---

# Full Setup

```js
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

import {
  QueryClient,
  QueryClientProvider,
} from "@tanstack/react-query";

const queryClient = new QueryClient();

ReactDOM.createRoot(document.getElementById("root")).render(
  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>
);
```

---

# Add Devtools

```js
import { ReactQueryDevtools } from "@tanstack/react-query-devtools";

<QueryClientProvider client={queryClient}>
  <App />
  <ReactQueryDevtools initialIsOpen={false} />
</QueryClientProvider>
```

---

# Most Important Hooks

| Hook             | Use             |
| ---------------- | --------------- |
| useQuery         | GET API         |
| useMutation      | POST PUT DELETE |
| useInfiniteQuery | Infinite scroll |
| useQueries       | Multiple APIs   |
| useQueryClient   | Cache access    |

---

# useQuery

Most important hook.

Used for:

* GET API
* Fetching data

---

# Basic Syntax

```js
const result = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});
```

---

# queryKey

Unique key.

```js
queryKey: ["users"]
```

React Query cache isi key se maintain karta hai.

---

# queryFn

API call function.

```js
queryFn: fetchUsers
```

---

# Full Example

```js
import { useQuery } from "@tanstack/react-query";
import axios from "axios";

function Users() {

  const fetchUsers = async () => {
    const res = await axios.get(
      "https://jsonplaceholder.typicode.com/users"
    );

    return res.data;
  };

  const {data,isLoading,isError, error,} = useQuery({
    queryKey: ["users"],
    queryFn: fetchUsers,
  });

  if (isLoading) {
    return <h1>Loading...</h1>;
  }

  if (isError) {
    return <h1>{error.message}</h1>;
  }

  return (
    <div>
      {data.map((user) => (
        <h2 key={user.id}>{user.name}</h2>
      ))}
    </div>
  );
}

export default Users;
```

---

# Important Returned Values

| Value      | Meaning             |
| ---------- | ------------------- |
| data       | API data            |
| isLoading  | First loading       |
| isError    | Error check         |
| error      | Error object        |
| isFetching | Background fetching |
| refetch    | Manual refetch      |

---

# isLoading vs isFetching

## isLoading

First time API call.

## isFetching

Every fetching including background.

---

# Example

```js
if(isLoading){
  return <h1>Loading...</h1>
}
```

---

# Manual Refetch

```js
const { refetch } = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});
```

```js
<button onClick={refetch}>
  Refetch
</button>
```

---

# Cache in React Query

Biggest feature.

---

# What is Cache?

API data memory me store hota hai.

Example:

```js
queryKey: ["users"]
```

Users data cache me save ho jayega.

---

# Benefit of Cache

* Fast UI
* Less API calls
* Better performance
* Better UX

---

# staleTime

Defines:

> Data kitni der tak fresh rahega

---

# Example

```js
useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
  staleTime: 5000,
});
```

5 seconds tak API dubara call nahi hogi.

---

# cacheTime / gcTime

Unused cache kitni der tak memory me rahega.

---

# Example

```js
gcTime: 1000 * 60 * 5
```

5 minute.

---

# Retry

API fail ho to automatic retry.

```js
retry: 3
```

---

# Disable Retry

```js
retry: false
```

---

# Refetch on Window Focus

Tab change karke aaye to API auto call.

```js
refetchOnWindowFocus: true
```

Disable:

```js
refetchOnWindowFocus: false
```

---

# Polling

Continuous API calling.

```js
refetchInterval: 2000
```

2 second me API call.

Used in:

* Live chat
* Stock market
* Notifications

---

# Dynamic Query Key

```js
queryKey: ["user", id]
```

Different id ka different cache.

---

# Example

```js
useQuery({
  queryKey: ["user", id],
  queryFn: () => fetchUser(id),
});
```

---

# Enabled

Conditional API call.

---

# Example

```js
enabled: !!id
```

Agar id hogi tabhi API call hogi.

---

# Select

Data transform karne ke liye.

```js
select: (data) => {
  return data.users;
}
```

---

# Placeholder Data

Temporary data.

```js
placeholderData: []
```

---

# Initial Data

Starting data.

```js
initialData: []
```

---

# Pagination

Very important interview topic.

---

# Traditional Pagination Problem

Page change pe flickering/loading hota hai.

React Query solve karta hai.

---

# Pagination Example

```js
const { data } = useQuery({
  queryKey: ["users", page],
  queryFn: () => fetchUsers(page),
});
```

---

# keepPreviousData

Old data show karta hai until new data comes.

```js
placeholderData: keepPreviousData
```

---

# Infinite Query

Used for:

* Infinite scrolling
* Load more

---

# Example

```js
useInfiniteQuery({
  queryKey: ["posts"],
  queryFn: fetchPosts,
  getNextPageParam: (lastPage) => {
    return lastPage.nextPage;
  },
});
```

---

# useMutation

Used for:

* POST
* PUT
* PATCH
* DELETE

---

# Syntax

```js
const mutation = useMutation({
  mutationFn: addUser,
});
```

---

# POST Example

```js
import { useMutation } from "@tanstack/react-query";
import axios from "axios";

function AddUser() {

  const addUser = async (user) => {
    return await axios.post(
      "https://jsonplaceholder.typicode.com/users",
      user
    );
  };

  const mutation = useMutation({
    mutationFn: addUser,
  });

  const handleAdd = () => {
    mutation.mutate({
      name: "Jarvis",
    });
  };

  return (
    <button onClick={handleAdd}>
      Add User
    </button>
  );
}
```

---

# mutate

API trigger karta hai.

```js
mutation.mutate(data)
```

---

# Mutation States

| State     | Meaning |
| --------- | ------- |
| isPending | Loading |
| isSuccess | Success |
| isError   | Error   |

---

# onSuccess

Success ke bad.

```js
onSuccess: () => {
  console.log("Success");
}
```

---

# onError

```js
onError: (error) => {
  console.log(error);
}
```

---

# onSettled

Success/error dono ke bad.

```js
onSettled: () => {}
```

---

# Important Concept

# Query Invalidation

Most asked interview topic.

---

# Why Needed?

POST ke bad latest data lana hota hai.

---

# Example

```js
const queryClient = useQueryClient();

const mutation = useMutation({
  mutationFn: addUser,

  onSuccess: () => {
    queryClient.invalidateQueries({
      queryKey: ["users"],
    });
  },
});
```

---

# invalidateQueries

Cache stale mark karta hai.

Then API refetch hoti hai.

---

# Optimistic Update

Advanced topic.

---

# Meaning

Backend response se pehle UI update.

Used for:

* Like button
* Todo add
* Chat apps

---

# Example Flow

1. UI instantly update
2. API call
3. Success → keep data
4. Error → rollback

---

# Example

```js
const mutation = useMutation({
  mutationFn: addTodo,

  onMutate: async (newTodo) => {

    await queryClient.cancelQueries({
      queryKey: ["todos"],
    });

    const previousTodos =
      queryClient.getQueryData(["todos"]);

    queryClient.setQueryData(
      ["todos"],
      (old) => [...old, newTodo]
    );

    return { previousTodos };
  },

  onError: (err, newTodo, context) => {
    queryClient.setQueryData(
      ["todos"],
      context.previousTodos
    );
  },

  onSettled: () => {
    queryClient.invalidateQueries({
      queryKey: ["todos"],
    });
  },
});
```

---

# Prefetching

Data pehle se fetch.

```js
queryClient.prefetchQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});
```

---

# Dependent Queries

Ek query dusri pe depend.

```js
const user = useQuery({
  queryKey: ["user"],
  queryFn: fetchUser,
});

const projects = useQuery({
  queryKey: ["projects"],
  queryFn: fetchProjects,
  enabled: !!user.data,
});
```

---

# Parallel Queries

Multiple APIs together.

```js
useQueries({
  queries: [
    {
      queryKey: ["users"],
      queryFn: fetchUsers,
    },
    {
      queryKey: ["posts"],
      queryFn: fetchPosts,
    },
  ],
});
```

---

# Axios Setup Best Practice

```js
import axios from "axios";

const api = axios.create({
  baseURL: "https://api.com",
});

export default api;
```

---

# API Folder Structure

```bash
src
 ├── api
 ├── hooks
 ├── services
 ├── components
 ├── pages
```

---

# Best Practice Custom Hook

```js
export const useUsers = () => {
  return useQuery({
    queryKey: ["users"],
    queryFn: fetchUsers,
  });
};
```

Usage:

```js
const { data } = useUsers();
```

---

# React Query Lifecycle

1. Query starts
2. Fetch API
3. Save cache
4. Return data
5. Background refetch
6. Cache cleanup

---

# Important Status

| Status  | Meaning |
| ------- | ------- |
| pending | Loading |
| success | Success |
| error   | Error   |

---

# Difference Between useEffect and React Query

| useEffect          | React Query |
| ------------------ | ----------- |
| Manual loading     | Automatic   |
| Manual caching     | Automatic   |
| Boilerplate ज्यादा | Less code   |
| Difficult retry    | Built-in    |
| No background sync | Available   |
| Hard optimization  | Easy        |

---

# Where React Query Used?

* Ecommerce
* Dashboard
* CRM
* Admin panel
* Social media
* Chat apps
* Banking apps

Almost every modern React project.

---

# React Query Interview Flow

Interviewer mostly asks:

1. Why React Query?
2. Difference useEffect vs React Query
3. Cache kya hota?
4. staleTime?
5. invalidateQueries?
6. Mutation?
7. Optimistic update?
8. Infinite query?
9. Retry?
10. Query key?

---

# VERY IMPORTANT INTERVIEW QUESTIONS

# Beginner Questions

## 1. What is React Query?

Server state management library.

---

## 2. Why use React Query?

For:

* Caching
* Data fetching
* Better performance
* Less boilerplate

---

## 3. Difference between useQuery and useMutation?

| useQuery   | useMutation     |
| ---------- | --------------- |
| GET API    | POST/PUT/DELETE |
| Fetch data | Modify data     |

---

## 4. What is queryKey?

Unique cache identifier.

---

## 5. What is staleTime?

Time until data remains fresh.

---

# Intermediate Questions

## 6. Difference between staleTime and gcTime?

| staleTime      | gcTime                 |
| -------------- | ---------------------- |
| Fresh duration | Cache removal duration |

---

## 7. What is invalidateQueries?

Marks query stale and refetches.

---

## 8. What is optimistic update?

UI updates before server response.

---

## 9. What is prefetching?

Data load before user needs it.

---

## 10. What is dependent query?

One query depends on another.

---

# Advanced Questions

## 11. How React Query improves performance?

* Cache
* Deduplication
* Background fetch
* Less API calls

---

## 12. What is background refetching?

API refresh without blocking UI.

---

## 13. What happens when query becomes stale?

React Query may refetch data.

---

## 14. Difference between isLoading and isFetching?

| isLoading  | isFetching |
| ---------- | ---------- |
| First load | Any fetch  |

---

## 15. How to handle pagination?

Dynamic query keys.

---

# Real Interview Practical Questions

* Create user list with React Query

* Implement pagination

* Implement infinite scrolling

* Create optimistic update

* Create CRUD using mutation

* Cache API response

* Refetch after POST

---

# Most Important Practical Flow

# GET API

```js
useQuery()
```

# POST API

```js
useMutation()
```

# Refresh Data

```js
invalidateQueries()
```

---

# Common Mistakes

## Wrong query keys

Bad:

```js
queryKey: ["data"]
```

Good:

```js
queryKey: ["users", id]
```

---

## API call inside component directly

Bad practice.

---

## Not invalidating query after mutation

UI old data show karegi.

---

# React Query Devtools

Very important.

Shows:

* Cache
* Queries
* Status
* Refetch
* Query keys

---

# Best Practices

* Always use query keys properly

* Use custom hooks

* Separate API logic

* Use staleTime wisely

* Invalidate after mutation

* Avoid unnecessary refetch

---

# Real World Example

# Ecommerce App

## Products GET

```js
useQuery()
```

## Add to cart

```js
useMutation()
```

## Refresh cart

```js
invalidateQueries()
```

---

# CRUD Full Flow

| Operation | Hook        |
| --------- | ----------- |
| GET       | useQuery    |
| POST      | useMutation |
| PUT       | useMutation |
| DELETE    | useMutation |

---

# TanStack Query v5 Important Changes

| Old       | New       |
| --------- | --------- |
| cacheTime | gcTime    |
| isLoading | isPending |

---

# Final Revision Notes

* React Query = Server State Management

* useQuery = GET

* useMutation = POST PUT DELETE

* queryKey = Cache identity

* staleTime = Fresh time

* gcTime = Cache cleanup

* invalidateQueries = Refetch query

* Optimistic update = Instant UI update

* Infinite query = Infinite scroll

---

# One Line Definitions

* useQuery

Fetch data from server.

---

## useMutation

Modify server data.

---

## Cache

Stored API data.

---

## staleTime

Fresh duration.

---

## invalidateQueries

Refresh query data.

---

# Interview Ready Summary

If interviewer asks:

> Why React Query?

Answer:

```txt
React Query is used for server state management.
It provides caching, background refetching,
pagination, retry, optimistic updates,
and reduces boilerplate code compared to
useEffect-based data fetching.
```

---

# Most Important Revision Order

1. useQuery
2. queryKey
3. Cache
4. staleTime
5. useMutation
6. invalidateQueries
7. Optimistic update
8. Pagination
9. Infinite query
10. Devtools

---

# Last Important Thing

## React Query does NOT replace:

* Redux fully
* Context API fully

Because:

Redux mainly handles client state.

React Query handles server state.

Sometimes both used together.

---

# Final Interview Tip

If interviewer gives practical task:

Always think:

```txt
GET → useQuery
POST/PUT/DELETE → useMutation
Refresh → invalidateQueries
```

# QueryClientProvider and queryClient Explained Easy Way

React Query use karne ke liye sabse important 2 cheeze hai:

1. `queryClient`
2. `QueryClientProvider`

Agar ye dono nahi honge to React Query kaam hi nahi karega.

---

# 1. What is queryClient?

```js id="ekyl4r"
const queryClient = new QueryClient();
```

Ye React Query ka **main manager/controller** hai.

Iska kaam:

* Cache manage karna
* API data store karna
* Refetch manage karna
* Retry manage karna
* Query track karna
* Mutation manage karna

Simple words:

> queryClient React Query ka brain hai.

---

# Real Life Example

Socho:

## React App = Shopping Mall

## queryClient = Mall Manager

Manager kya karta hai?

* Data maintain
* Store manage
* Updates manage
* Problems handle

Same kaam queryClient karta hai.

---

# Example

```js id="dtxzux"
import { QueryClient } from "@tanstack/react-query";

const queryClient = new QueryClient();
```

---

# What Happens Internally?

Jab API call hoti hai:

```js id="dghm4y"
useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});
```

to React Query:

1. queryClient me data save karta hai
2. Cache create karta hai
3. Data track karta hai
4. Refetch manage karta hai

---

# 2. What is QueryClientProvider?

```js id="7l7b1k"
<QueryClientProvider client={queryClient}>
  <App />
</QueryClientProvider>
```

Ye provider pura React app ko React Query access deta hai.

---

# Why Needed?

React Query hooks:

* useQuery
* useMutation
* useInfiniteQuery

sabko queryClient chahiye hota hai.

Provider ke through pura app queryClient access karta hai.

---

# Real Life Example

## queryClient = WiFi Router

## QueryClientProvider = WiFi Connection

Aur:

## useQuery = Mobile Devices

Agar WiFi connect nahi hua:

❌ Internet nahi chalega

Same:

Agar QueryClientProvider nahi diya:

❌ useQuery kaam nahi karega

---

# Full Flow

```txt id="h3omvq"
QueryClient
     ↓
QueryClientProvider
     ↓
Entire App
     ↓
useQuery / useMutation
```

---

# Full Setup Example

```js id="fd0j54"
import React from "react";
import ReactDOM from "react-dom/client";

import App from "./App";

import {
  QueryClient,
  QueryClientProvider,
} from "@tanstack/react-query";

const queryClient = new QueryClient();

ReactDOM.createRoot(document.getElementById("root")).render(

  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>

);
```

---

# Step by Step Understanding

---

# Step 1

```js id="1zdr9k"
const queryClient = new QueryClient();
```

React Query manager create hua.

---

# Step 2

```js id="0h70wa"
<QueryClientProvider client={queryClient}>
```

App ko manager diya.

---

# Step 3

```js id="vmr7jd"
useQuery()
```

Ab app React Query use kar sakta hai.

---

# What If QueryClientProvider Not Used?

Error ayega:

```txt id="nwmadq"
No QueryClient set, use QueryClientProvider to set one
```

Because hooks ko queryClient nahi mila.

---

# What is Stored Inside queryClient?

## Cache

```js id="o5ubm2"
["users"]
["posts"]
["todos"]
```

* Query data

* Mutation data

* Query states

* Retry info

* Fetch status

Sab kuch.

---

# queryClient Important Methods

| Method            | Use          |
| ----------------- | ------------ |
| invalidateQueries | Refetch      |
| setQueryData      | Update cache |
| getQueryData      | Get cache    |
| removeQueries     | Remove cache |
| prefetchQuery     | Prefetch     |

---

# Example of invalidateQueries

```js id="4p8w8m"
queryClient.invalidateQueries({
  queryKey: ["users"],
});
```

Users API dubara chalegi.

---

# useQueryClient Hook

Agar component ke andar queryClient use karna ho:

```js id="ah6jrw"
import { useQueryClient } from "@tanstack/react-query";

const queryClient = useQueryClient();
```

---

# Example

```js id="5g7f6h"
const queryClient = useQueryClient();

queryClient.invalidateQueries({
  queryKey: ["users"],
});
```

---

# Interview Definition

# QueryClient

```txt id="b18pqj"
QueryClient is the core manager in React Query
that handles caching, fetching, refetching,
and query state management.
```

---

# QueryClientProvider

```txt id="pt8vw4"
QueryClientProvider provides the QueryClient
instance to the entire React application
so that React Query hooks can access it.
```

---

# Simple One Line

## queryClient

> Data manager

## QueryClientProvider

> Data manager ko app me provide karta hai

---

# Most Important Thing

```js id="kwynwb"
const queryClient = new QueryClient();
```

Usually sirf ek baar banta hai.

---

# Why Single queryClient?

Because:

Agar multiple queryClient bana diye:

* Cache alag ho jayega
* Data sync issue ayega
* Performance issue ayega

---

# Real Interview Question

## Question:

Why QueryClientProvider is required?

## Answer:

```txt id="jzlvcs"
QueryClientProvider is required to provide
the QueryClient instance to the React component tree.
Without it, React Query hooks like useQuery
and useMutation cannot access the query client.
```

---

# Visual Understanding

```txt id="9fhq7c"
queryClient
   ↓
stores cache and query data

QueryClientProvider
   ↓
provides queryClient to app

useQuery/useMutation
   ↓
uses queryClient internally
```
