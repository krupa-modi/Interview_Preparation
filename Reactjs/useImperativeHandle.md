# useImperativeHandle Hook in React

## What is useImperativeHandle?

`useImperativeHandle` React hook hai jo parent component ko child component ke functions ya values access karne deta hai using `ref`.

Ye mostly `forwardRef` ke sath use hota hai.
---

# Simple Definition

Parent component child component ke custom methods access kar sake uske liye `useImperativeHandle` use hota hai.

---

# Syntax

```jsx
useImperativeHandle(ref, () => {
  return {
    customMethod,
  };
});
````

---

# Important Points

| Point           | Description                          |
| --------------- | ------------------------------------ |
| Used with       | forwardRef                           |
| Purpose         | Parent ko child methods expose karna |
| Mostly Used For | Focus input, reset form, open modal  |
| Works With      | refs                                 |

---

# Why use useImperativeHandle?

Normally parent component directly child ke internal functions access nahi kar sakta.

Lekin:

* focus input
* clear input
* open modal
* reset form

jaise kaam karne ke liye parent ko child ke methods access karne padte hai.

Tab `useImperativeHandle` use hota hai.

---

# Basic Example

## Child Component

```jsx id="ff8ajm"
import React, {
  useRef,
  forwardRef,
  useImperativeHandle,
} from "react";

const Child = forwardRef((props, ref) => {

  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focusInput() {
      inputRef.current.focus();
    },
  }));

  return (
    <input
      type="text"
      ref={inputRef}
      placeholder="Enter text"
    />
  );
});

export default Child;
```

---

## Parent Component

```jsx id="x3v6tq"
import React, { useRef } from "react";
import Child from "./Child";

function App() {

  const childRef = useRef();

  const handleClick = () => {
    childRef.current.focusInput();
  };

  return (
    <div>

      <Child ref={childRef} />

      <button onClick={handleClick}>
        Focus Input
      </button>

    </div>
  );
}

export default App;
```

---

# Flow Explanation

```text
Parent Component
      ↓
Calls child method using ref
      ↓
useImperativeHandle exposes method
      ↓
Child method executes
```

---

# Step By Step Understanding

## Step 1

Parent creates ref.

```jsx id="a9h3vr"
const childRef = useRef();
```

---

## Step 2

Ref child component ko pass hoti hai.

```jsx id="m5k8dn"
<Child ref={childRef} />
```

---

## Step 3

Child component methods expose karta hai.

```jsx id="f2n7qc"
useImperativeHandle(ref, () => ({
  focusInput() {
    inputRef.current.focus();
  },
}));
```

---

## Step 4

Parent method call karta hai.

```jsx id="u8r4wb"
childRef.current.focusInput();
```

---

# Real Use Cases

| Use Case          | Example           |
| ----------------- | ----------------- |
| Focus Input       | Input auto focus  |
| Open Modal        | Modal open/close  |
| Reset Form        | Form clear        |
| Trigger Animation | Animation start   |
| Scroll Control    | Scroll to section |

---

# Difference Between useRef and useImperativeHandle

| useRef               | useImperativeHandle             |
| -------------------- | ------------------------------- |
| Ref create karta hai | Custom methods expose karta hai |
| DOM access           | Parent-child communication      |
| Simple reference     | Controlled access               |

---

# Important Notes

## useImperativeHandle always used with:

```jsx id="w6s1xt"
forwardRef
```

Without `forwardRef`, ye properly work nahi karta.

---

# Interview Questions

## What is useImperativeHandle?

It is a React hook used to customize the instance value exposed to parent components using refs.

---

## Why use useImperativeHandle?

To expose custom methods or values from child component to parent component.

---

## Which hook is commonly used with useImperativeHandle?

```jsx id="n3v8qy"
forwardRef
```

---

# Interview Short Answer

`useImperativeHandle` parent component ko child component ke custom functions access karne deta hai using refs.

---

# Summary

| Hook                | Purpose               |
| ------------------- | --------------------- |
| useRef              | Reference create      |
| forwardRef          | Ref forward           |
| useImperativeHandle | Custom methods expose |

---

# One Line Easy Definition

`useImperativeHandle` parent ko child ke functions control karne deta hai using ref.

