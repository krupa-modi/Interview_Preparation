## What is React.memo?

`React.memo` is a Higher Order Component (HOC) in React.

It is used to optimize performance by preventing unnecessary re-rendering of components.

If the component props do not change, React will reuse the previous rendered result instead of rendering the component again.

---

# Syntax

```jsx
const MemoizedComponent = React.memo(Component)
````

OR

```jsx
export default React.memo(Component)
```

---

# Why React.memo is Used?

Normally in React:

* When parent component re-renders
* All child components also re-render

Even if child props are same.

This can reduce performance in large applications.

`React.memo` solves this problem.

---

# Example Without React.memo

## Child Component

```jsx
function Child() {
  console.log("Child Rendered")

  return <h1>Child Component</h1>
}

export default Child
```

## Parent Component

```jsx
import { useState } from "react"
import Child from "./Child"

function App() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <h1>{count}</h1>

      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>

      <Child />
    </div>
  )
}

export default App
```

---

# Output

Whenever button clicked:

```bash
Child Rendered
```

Why?

Because parent re-render hua toh child bhi re-render ho gaya.

---

# Example With React.memo

## Child Component

```jsx
import React from "react"

function Child() {
  console.log("Child Rendered")

  return <h1>Child Component</h1>
}

export default React.memo(Child)
```

## Parent Component

```jsx
import { useState } from "react"
import Child from "./Child"

function App() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <h1>{count}</h1>

      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>

      <Child />
    </div>
  )
}

export default App
```

---

# Output

Now button click karne par:

```bash
Child Rendered
```

Sirf first time render hoga.

Baad me render nahi hoga because props change nahi hue.

---

# React.memo with Props

```jsx
import React from "react"

function Child({ name }) {
  console.log("Child Rendered")

  return <h1>{name}</h1>
}

export default React.memo(Child)
```

## Parent

```jsx
import { useState } from "react"
import Child from "./Child"

function App() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>

      <Child name="Krupa" />
    </div>
  )
}

export default App
```

---

# What Happens?

* Parent re-render hoga
* But Child re-render nahi hoga
* Because `name` prop same hai

# Problem with Object Props

```jsx
<Child user={{ name: "Krupa" }} />
```

Every render new object create hota hai.

So React.memo fail ho jayega.

Because reference different hai.

---

# Solution

Use `useMemo`

```jsx
const user = useMemo(() => {
  return { name: "Krupa" }
}, [])
```

---

# Custom Comparison Function

React.memo second argument bhi accept karta hai.

```jsx
React.memo(Component, areEqual)
```

---

# Example

```jsx
function Child({ data }) {
  console.log("Rendered")

  return <h1>{data.name}</h1>
}

function areEqual(prevProps, nextProps) {
  return prevProps.data.name === nextProps.data.name
}

export default React.memo(Child, areEqual)
```

---

# When to Use React.memo?

Use React.memo when:

* Component frequently re-renders
* Same props pass ho rahe ho
* Large list rendering ho
* Expensive UI ho
* Performance optimize karna ho

---

# When NOT to Use React.memo?

Avoid when:

* Small/simple component ho
* Props always change hote ho
* Component lightweight ho

Because memoization bhi extra memory use karta hai.

---

# Real World Example

Examples:

* Product cards
* Table rows
* Dashboard widgets
* Chat message items
* Large lists

---

# Advantages

* Better performance
* Avoid unnecessary re-render
* Faster UI

---

# Disadvantages

* Extra memory usage
* Overuse can reduce performance
* Shallow comparison limitations

---

# Interview Questions

## 1. What is React.memo?

React.memo is a Higher Order Component used to prevent unnecessary re-rendering of functional components.

---

## 2. Does React.memo work for class components?

No.

For class components use:

```jsx
PureComponent
```

## 4. Difference between React.memo and useMemo?

* React.memo memoizes component
* useMemo memoizes value

---

## 5. Can React.memo improve performance?

Yes, when unnecessary renders are happening.

---

# Easy Definition for Interview

"React.memo is used to prevent unnecessary re-rendering of functional components when props have not changed."


# Difference Between useMemo and React.memo

Both are performance optimization techniques in React.

But dono ka purpose different hai.

---

# React.memo

## Purpose

Component ko memoize karta hai.

Means:
Agar props same hai toh component re-render nahi hoga.

---

# Syntax

```jsx
export default React.memo(Component)
````

---

# useMemo

## Purpose

Computed value ko memoize karta hai.

Means:
Expensive calculation ko baar baar run hone se bachata hai.

---

# Syntax

```jsx
const value = useMemo(() => {
  return expensiveFunction()
}, [dependency])
```

---

# Main Difference

| Feature  | React.memo                | useMemo                 |
| -------- | ------------------------- | ----------------------- |
| Used For | Component memoization     | Value memoization       |
| Prevents | Component re-render       | Expensive recalculation |
| Works On | Functional component      | Value/function result   |
| Returns  | Memoized component        | Memoized value          |
| Used In  | Export/component wrapping | Inside component        |

---

# React.memo Example

## Child Component

```jsx
function Child({ name }) {
  console.log("Child Rendered")

  return <h1>{name}</h1>
}

export default React.memo(Child)
```

## Parent Component

```jsx
function App() {
  const [count, setCount] = useState(0)

  return (
    <>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>

      <Child name="Krupa" />
    </>
  )
}
```

---

# What Happens?

* Parent re-render hoga
* Child re-render nahi hoga
* Because prop same hai

---

# useMemo Example

```jsx
import { useMemo, useState } from "react"

function App() {
  const [count, setCount] = useState(0)

  const expensiveValue = useMemo(() => {
    console.log("Calculating...")

    return count * 1000
  }, [count])

  return (
    <>
      <h1>{expensiveValue}</h1>

      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </>
  )
}
```

---

# What Happens?

Calculation tabhi chalega jab `count` change hoga.

---

# When to Use React.memo?

Use when:

* Child component unnecessary re-render ho raha ho
* Same props pass ho rahe ho
* Large UI rendering ho

Examples:

* Product cards
* Table rows
* List items

---

# When to Use useMemo?

Use when:

* Heavy calculation ho
* Expensive computation ho
* Derived data calculate karna ho

Examples:

* Filtering large arrays
* Sorting data
* Complex calculations

---

# Important Relation

Many times:

```jsx
React.memo + useMemo
```

Together use hote hai.

---

# Example

```jsx
const user = useMemo(() => {
  return { name: "Krupa" }
}, [])

<Child user={user} />
```

Why?

Because object reference stable rahega.

Otherwise React.memo fail ho jayega.

---

# Simple Memory Trick

## React.memo

"Memoize Component"

## useMemo

"Memoize Value"

---

## React.memo

Used to prevent unnecessary re-rendering of components.

## useMemo

Used to cache expensive computed values.


