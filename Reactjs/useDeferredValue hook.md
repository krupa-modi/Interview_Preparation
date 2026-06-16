# useDeferredValue() in React

## What is useDeferredValue?

useDeferredValue is a React Hook that makes a value update at a lower priority.

In simple words:

👉 Whatever the user is typing updates immediately.

👉 Heavy UI updates (large lists, search results, filtering) happen a little later.

This keeps the UI responsive and typing smooth.

---

## Real Life Example

Imagine you are searching on Google.

```text
Typing:
R
Re
Rea
Reac
React
```

If every key press triggers filtering of 10,000 records, the UI can become slow.

useDeferredValue says:

```text
Show the user's typing first.
Do the heavy filtering later.
```

---

## Syntax

```jsx
const deferredValue = useDeferredValue(value);
```

---

## Simple Example

### Without useDeferredValue

```jsx
import { useState } from "react";

function App() {
  const [search, setSearch] = useState("");

  return (
    <>
      <input
        value={search}
        onChange={(e) => setSearch(e.target.value)}
      />

      <SearchResults query={search} />
    </>
  );
}
```

### Problem

```text
SearchResults re-renders on every key press.
```

---

### With useDeferredValue

```jsx
import { useState, useDeferredValue } from "react";

function App() {
  const [search, setSearch] = useState("");

  const deferredSearch = useDeferredValue(search);

  return (
    <>
      <input
        value={search}
        onChange={(e) => setSearch(e.target.value)}
      />

      <SearchResults query={deferredSearch} />
    </>
  );
}
```

### Flow

```text
User types:
React

search = React (updates immediately)

deferredSearch
= R
= Re
= Rea
= React (updates later)

SearchResults uses deferredSearch.
```

### Result

✅ Smooth typing

✅ Faster UI

✅ Expensive rendering is delayed

---

## Interview Definition

useDeferredValue is a React Hook that lets us defer updating a non-critical part of the UI. It keeps urgent updates like typing responsive while delaying expensive rendering work such as filtering large lists or search results.

---

## Practical Interview Example

### Search Box + Large List

```jsx
import React, {
  useState,
  useDeferredValue
} from "react";

function App() {
  const [search, setSearch] = useState("");

  const deferredSearch =
    useDeferredValue(search);

  const users = [
    "React",
    "Angular",
    "Vue",
    "Node"
  ];

  const filteredUsers = users.filter((item) =>
    item.toLowerCase().includes(
      deferredSearch.toLowerCase()
    )
  );

  return (
    <>
      <input
        value={search}
        onChange={(e) =>
          setSearch(e.target.value)
        }
      />

      {filteredUsers.map((user) => (
        <p key={user}>{user}</p>
      ))}
    </>
  );
}
```

---

## Difference Between useMemo and useDeferredValue

| useMemo                  | useDeferredValue               |
| ------------------------ | ------------------------------ |
| Caches calculations      | Delays updates                 |
| Performance optimization | UI responsiveness optimization |
| Avoids re-computation    | Postpones rendering            |
| Reduces CPU work         | Improves user experience       |

---

## Difference Between useTransition and useDeferredValue

| useTransition            | useDeferredValue              |
| ------------------------ | ----------------------------- |
| Defers state updates     | Defers a value                |
| Uses startTransition()   | Uses a hook directly          |
| Manual control           | Automatic                     |
| Best for complex updates | Best for search/filter inputs |

### Example

```jsx
const [isPending, startTransition] =
  useTransition();

startTransition(() => {
  setUsers(newUsers);
});
```

```jsx
const deferredSearch =
  useDeferredValue(search);
```

---

## When Should We Use It?

### 1. Search Functionality

```text
Searching through 10,000 records
```

### 2. Large Table Filtering

```text
Employee table filtering
```

### 3. Charts

```text
Expensive chart updates
```

### 4. Dashboards

```text
Heavy widgets rendering
```

### 5. API Search UI

```text
Search text updates instantly
Results render later
```

---

## When Should We NOT Use It?

❌ Simple forms

❌ Small lists

❌ Login pages

❌ CRUD forms

❌ Small components

If rendering is not expensive, there is no need to use useDeferredValue.

---

## 30-Second Interview Answer

useDeferredValue is a React performance Hook that defers non-urgent UI updates. When a user performs an urgent action like typing and there is expensive rendering or filtering happening at the same time, useDeferredValue keeps the UI responsive by delaying the non-critical updates. It is commonly used in search boxes, large tables, and expensive filtering scenarios.
