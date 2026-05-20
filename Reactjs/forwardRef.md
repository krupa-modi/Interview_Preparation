## What is forwardRef?

`forwardRef` React ka function hai jo parent component ki `ref` ko child component ke andar forward karta hai.

Simple words me:

> Parent component child component ke DOM element ko access kar sakta hai using `forwardRef`.

---

# Why We Need forwardRef?

Normally ref direct HTML elements par lagti hai.

Example:

```jsx
<input ref={inputRef} />
````

Lekin:

```jsx
<MyComponent ref={inputRef} />
```

Ye directly work nahi karta.

Kyuki functional components refs accept nahi karte by default.

Is problem ko solve karne ke liye `forwardRef` use hota hai.

---

# Syntax

```jsx
const Component = forwardRef((props, ref) => {
  return <input ref={ref} />;
});
```

---

# Basic Example

# Child Component

```jsx id="u5z2mw"
import React, { forwardRef } from "react";

const Child = forwardRef((props, ref) => {

  return (
    <input
      type="text"
      ref={ref}
      placeholder="Enter text"
    />
  );
});

export default Child;
```

---

# Parent Component

```jsx id="p1x8cr"
import React, { useRef } from "react";
import Child from "./Child";

function App() {

  const inputRef = useRef();

  const handleFocus = () => {
    inputRef.current.focus();
  };

  return (
    <div>

      <Child ref={inputRef} />

      <button onClick={handleFocus}>
        Focus Input
      </button>

    </div>
  );
}

export default App;
```

---

# How It Works

## Step 1

Parent creates ref.

```jsx id="t9n3vz"
const inputRef = useRef();
```

---

## Step 2

Ref child component ko pass hoti hai.

```jsx id="m7q4xl"
<Child ref={inputRef} />
```

---

## Step 3

Child component ref ko receive karta hai.

```jsx id="f4y8pk"
forwardRef((props, ref) => {})
```

---

## Step 4

Ref input element ko attach hoti hai.

```jsx id="r2w6jb"
<input ref={ref} />
```

---

## Step 5

Parent DOM access karta hai.

```jsx id="y8k1vz"
inputRef.current.focus();
```

---

# Flow Diagram

```text id="j5p9xr"
Parent Component
      ↓
Passes ref
      ↓
forwardRef receives ref
      ↓
Ref attached to DOM
      ↓
Parent accesses DOM element
```

---

# Real Use Cases

| Use Case       | Example           |
| -------------- | ----------------- |
| Focus input    | Auto focus        |
| Scroll control | Scroll section    |
| Modal control  | Open/close modal  |
| Animation      | Trigger animation |
| Form handling  | Input access      |

---

# Difference Between Normal Component and forwardRef

| Normal Component                 | forwardRef Component        |
| -------------------------------- | --------------------------- |
| Ref access nahi hota             | Ref forward hoti hai        |
| Parent DOM access nahi kar sakta | Parent DOM access kar sakta |
| Simple component                 | Ref-enabled component       |

---

# Important Notes

## forwardRef mostly used with:

```jsx id="e6v2nd"
useRef
```

and

```jsx id="w3k9tb"
useImperativeHandle
```

---

# Interview Questions

## What is forwardRef?

forwardRef ek React function hai jo parent component ki ref ko child component ke andar forward karta hai.

---

## Why use forwardRef?

Child component ke DOM elements ko parent se access karne ke liye.

---

## Can functional components accept refs directly?

No.

Functional components refs directly accept nahi karte.

---

## Which hook is commonly used with forwardRef?

```jsx id="x7m1rc"
useImperativeHandle
```

---

# Interview Short Answer

`forwardRef` parent component ki ref ko child component ke DOM element tak forward karta hai.

---

# One Line Easy Definition

`forwardRef` parent ko child ke DOM elements access karne deta hai.

---

# Summary

| Concept             | Meaning                         |
| ------------------- | ------------------------------- |
| useRef              | Ref create karta hai            |
| forwardRef          | Ref child ko forward karta hai  |
| useImperativeHandle | Custom methods expose karta hai |


