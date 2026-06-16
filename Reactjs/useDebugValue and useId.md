# useDebugValue() in React

## What is useDebugValue?

`useDebugValue` is a React Hook used to display custom labels or values for custom hooks in React DevTools.

It helps developers debug custom hooks more easily.

---

## Syntax

```jsx
useDebugValue(value);
```

---

## Why Do We Need It?

Without `useDebugValue`, React DevTools only shows:

```text
useOnlineStatus
```

With `useDebugValue`:

```text
useOnlineStatus
Status: Online
```

This makes debugging much easier.

---

## Simple Example

### Custom Hook

```jsx
import { useState, useEffect, useDebugValue } from "react";

function useOnlineStatus() {
  const [isOnline, setIsOnline] = useState(true);

  useDebugValue(
    isOnline ? "Online" : "Offline"
  );

  return isOnline;
}
```

### Component

```jsx
function App() {
  const isOnline = useOnlineStatus();

  return (
    <h1>
      {isOnline ? "Online" : "Offline"}
    </h1>
  );
}
```

---

## React DevTools Output

```text
useOnlineStatus
Online
```

---

## When to Use useDebugValue?

Use it only inside custom hooks.

Examples:

* Authentication Hook
* Theme Hook
* Online Status Hook
* API Hook
* Form Hook
* Cart Hook

---

## When NOT to Use?

❌ Normal Components

❌ Simple State Management

❌ Production Logic

❌ UI Rendering

It is only for debugging.

---

## Interview Definition

> `useDebugValue` is a React Hook used to display custom information about custom hooks in React DevTools. It improves debugging by showing meaningful labels and values while developing.

---

## Interview Example

```jsx
function useUser() {
  const [user, setUser] = useState(null);

  useDebugValue(
    user ? "Logged In" : "Guest"
  );

  return user;
}
```

React DevTools:

```text
useUser
Logged In
```

---

# useId() in React

## What is useId?

`useId` is a React Hook that generates a unique and stable ID.

It is mainly used to connect form elements such as labels and inputs.

---

## Why Do We Need It?

Without `useId`:

```jsx
<label htmlFor="name">
  Name
</label>

<input id="name" />
```

If multiple components are rendered, duplicate IDs can occur.

`useId` solves this problem by generating unique IDs automatically.

---

## Syntax

```jsx
const id = useId();
```

---

## Simple Example

```jsx
import { useId } from "react";

function LoginForm() {
  const id = useId();

  return (
    <>
      <label htmlFor={id}>
        Name
      </label>

      <input id={id} />
    </>
  );
}
```

---

## Generated ID

```text
:r0:
:r1:
:r2:
```

React automatically creates unique IDs.

---

## Multiple Fields Example

```jsx
import { useId } from "react";

function Form() {
  const nameId = useId();
  const emailId = useId();

  return (
    <>
      <label htmlFor={nameId}>
        Name
      </label>
      <input id={nameId} />

      <label htmlFor={emailId}>
        Email
      </label>
      <input id={emailId} />
    </>
  );
}
```

---

## Real-Life Usage

### Forms

```jsx
const id = useId();
```

### Accessibility

```jsx
<label htmlFor={id}>
  Username
</label>

<input id={id} />
```

### Reusable Components

```jsx
<TextInput />
<TextInput />
<TextInput />
```

Each component gets a unique ID.

---

## When to Use useId?

✅ Forms

✅ Accessibility (a11y)

✅ Reusable Components

✅ Labels and Inputs

✅ SSR Applications

---

## When NOT to Use?

❌ List Keys

```jsx
items.map(item => (
  <li key={item.id}>
    {item.name}
  </li>
))
```

Do not use `useId` for React keys.

❌ Random IDs for Database Records

❌ Authentication Tokens

---

## Interview Definition

> `useId` is a React Hook that generates unique and stable IDs for accessibility and form elements. It helps avoid duplicate IDs and works correctly with both client-side rendering and server-side rendering.

---

## useId vs UUID

| useId                 | UUID                 |
| --------------------- | -------------------- |
| React Hook            | External Library     |
| Stable across renders | Random value         |
| For UI elements       | For data identifiers |
| Accessibility focused | Database/API focused |

---

### useDebugValue

> `useDebugValue` is used inside custom hooks to display custom debugging information in React DevTools, making hooks easier to inspect and debug.

### useId

> `useId` generates unique and stable IDs for form elements and accessibility purposes. It helps connect labels and inputs without creating duplicate IDs and works well with SSR.
