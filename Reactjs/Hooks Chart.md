# React Hooks Complete Interview Revision Notes 🚀

## 📌 What are Hooks?
Hooks React ke special functions hote hain jo functional components me:

* state use karne
* lifecycle handle karne
* performance optimize karne
* reusable logic banane

me help karte hain.

👉 Hooks React 16.8 me aaye the.

---

# 🔥 Rules of Hooks (Very Important)

## ✅ Rule 1: Hooks sirf top level pe call karo

❌ Wrong

```js
if (show) {
  useEffect(() => {});
}
```

✅ Correct

```js
useEffect(() => {
  if (show) {
    console.log("hello");
  }
}, [show]);
```

---

## ✅ Rule 2: Hooks sirf React component ya custom hook me use karo

❌ Wrong

```js
function test() {
  useState();
}
```

✅ Correct

```js
function App() {
  useState();
}
```

---

# 📊 Complete React Hooks Chart

---

# 🟢 1. State Management Hooks

| Hook                 | Use                 | Re-render | Best Use Case        |
| -------------------- | ------------------- | --------- | -------------------- |
| useState             | Simple local state  | ✅         | Form, toggle         |
| useReducer           | Complex state logic | ✅         | Multiple actions     |
| useSyncExternalStore | External store sync | ✅         | Redux/Zustand custom |

---

# 🔹 useState

## ✅ Use

Simple state manage karne ke liye.

## ✅ Syntax

```js
const [count, setCount] = useState(0);
```

## ✅ Example

```js
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <h1>{count}</h1>

      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </>
  );
}
```

---

## 🔥 Important Interview Points

### ✅ State async hota hai

```js
setCount(count + 1);
console.log(count);
```

Old value print ho sakti hai.

---

### ✅ Functional Update

```js
setCount((prev) => prev + 1);
```

---

### ✅ Re-render trigger karta hai

State update → component re-render.

---

# 🔹 useReducer

## ✅ Use

Complex state logic ke liye.

Redux jaisa pattern.

---

## ✅ Syntax

```js
const [state, dispatch] = useReducer(reducer, initialState);
```

---

## ✅ Example

```js
import { useReducer } from "react";

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };

    case "decrement":
      return { count: state.count - 1 };

    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(
    reducer,
    initialState
  );

  return (
    <>
      <h1>{state.count}</h1>

      <button
        onClick={() =>
          dispatch({ type: "increment" })
        }
      >
        +
      </button>
    </>
  );
}
```

---

## 🔥 Interview Points

| useState         | useReducer             |
| ---------------- | ---------------------- |
| Simple state     | Complex logic          |
| Easy syntax      | Reducer pattern        |
| Small components | Large state management |

---

# 🔹 useSyncExternalStore

## ✅ Use

External store ko React ke sath sync karne ke liye.

Mostly library creators use karte hain.

---

## ✅ Example

```js
const value = useSyncExternalStore(
  subscribe,
  getSnapshot
);
```

---

# 🔵 2. Ref Hooks

| Hook                | Use               | Re-render |
| ------------------- | ----------------- | --------- |
| useRef              | DOM/value store   | ❌         |
| useImperativeHandle | Custom ref expose | ❌         |

---

# 🔹 useRef

## ✅ Use

* DOM access
* Mutable value store
* Previous value store

---

## ✅ Example

```js
import { useRef } from "react";

function App() {
  const inputRef = useRef();

  function focusInput() {
    inputRef.current.focus();
  }

  return (
    <>
      <input ref={inputRef} />

      <button onClick={focusInput}>
        Focus
      </button>
    </>
  );
}
```

---

## 🔥 Important Points

### ✅ Re-render nahi karta

```js
ref.current = 10;
```

UI update nahi hota.

---

### ✅ Previous value store kar sakte hain

```js
const prev = useRef();
```

---

# 🔹 useImperativeHandle

## ✅ Use

Parent ko limited methods expose karne ke liye.

forwardRef ke sath use hota hai.

---

## ✅ Example

```js
useImperativeHandle(ref, () => ({
  focus() {
    inputRef.current.focus();
  },
}));
```

---

# 🟣 3. Effect Hooks (Most Important)

| Hook               | Timing        | Use           |
| ------------------ | ------------- | ------------- |
| useEffect          | After paint   | API           |
| useLayoutEffect    | Before paint  | DOM measure   |
| useInsertionEffect | Before layout | CSS injection |

---

# 🔥 Hook Timing Order

Render →
DOM Update →
useInsertionEffect →
useLayoutEffect →
Paint →
useEffect

---

# 🔹 useEffect

## ✅ Use

* API calls
* Event listener
* Timer
* Subscription

---

## ✅ Example

```js
useEffect(() => {
  console.log("Component Mounted");
}, []);
```

---

## 🔥 Dependency Array Cases

### ✅ Run once

```js
useEffect(() => {}, []);
```

---

### ✅ Run every render

```js
useEffect(() => {});
```

---

### ✅ Run on dependency change

```js
useEffect(() => {}, [count]);
```

---

## 🔥 Cleanup Function

```js
useEffect(() => {
  const timer = setInterval(() => {}, 1000);

  return () => clearInterval(timer);
}, []);
```

---

## 🔥 Interview Questions

### ✅ Why cleanup important?

Memory leak avoid karta hai.

---

### ✅ Infinite loop kab hota hai?

```js
useEffect(() => {
  setCount(count + 1);
}, [count]);
```

---

# 🔹 useLayoutEffect

## ✅ Use

DOM measure/layout calculations.

---

## ✅ Example

```js
useLayoutEffect(() => {
  console.log(divRef.current.offsetHeight);
}, []);
```

---

## 🔥 Difference

| useEffect   | useLayoutEffect |
| ----------- | --------------- |
| After paint | Before paint    |
| Async       | Sync            |
| Faster UI   | Layout measure  |

---

# 🔹 useInsertionEffect

## ✅ Use

CSS-in-JS libraries.

Rarely used.

---

# 🟡 4. Context Hook

# 🔹 useContext

## ✅ Use

Prop drilling avoid karne ke liye.

---

## ✅ Example

```js
const ThemeContext = createContext();

function Child() {
  const theme = useContext(ThemeContext);

  return <h1>{theme}</h1>;
}
```

---

## 🔥 Interview Point

### ❌ Context Redux ka replacement nahi hai

Global state sharing ke liye useful hai.

---

# 🔴 5. Transition Hooks (React 18)

| Hook             | Use                  |
| ---------------- | -------------------- |
| useTransition    | Low priority updates |
| useDeferredValue | Delayed rendering    |

---

# 🔹 useTransition

## ✅ Use

Heavy UI updates ko smooth banana.

---

## ✅ Example

```js
const [isPending, startTransition] =
  useTransition();

startTransition(() => {
  setList(data);
});
```

---

## 🔥 Interview Point

Urgent updates block nahi hote.

---

# 🔹 useDeferredValue

## ✅ Use

Search optimization.

---

## ✅ Example

```js
const deferredValue =
  useDeferredValue(search);
```

---

## 🔥 Use Case

Search input lag avoid.

---

# 🟤 6. Performance Hooks

| Hook        | Use               |
| ----------- | ----------------- |
| useMemo     | Memoized value    |
| useCallback | Memoized function |

---

# 🔹 useMemo

## ✅ Use

Expensive calculation cache.

---

## ✅ Example

```js
const result = useMemo(() => {
  return heavyCalculation(data);
}, [data]);
```

---

## 🔥 Interview Point

### ❌ Har jagah use mat karo

Over optimization bhi problem hai.

---

# 🔹 useCallback

## ✅ Use

Function memoization.

---

## ✅ Example

```js
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

---

## 🔥 Difference

| useMemo      | useCallback     |
| ------------ | --------------- |
| Value return | Function return |

---

# 🟠 7. Debug / Utility Hooks

| Hook          | Use               |
| ------------- | ----------------- |
| useDebugValue | Debug custom hook |
| useId         | Unique ID         |

---

# 🔹 useDebugValue

## ✅ Use

Custom hook debugging.

---

## ✅ Example

```js
useDebugValue("Online");
```

---

# 🔹 useId

## ✅ Use

Unique accessible IDs.

---

## ✅ Example

```js
const id = useId();
```

---

# 🟢 8. React 19 Hooks

| Hook          | Use              |
| ------------- | ---------------- |
| useFormStatus | Form pending     |
| useFormState  | Form state       |
| useOptimistic | Optimistic UI    |
| use           | Promise handling |

---

# 🔹 useOptimistic

## ✅ Use

Instant UI update before API success.

---

## ✅ Example

```js
const [optimisticTodos, addTodo] =
  useOptimistic(todos);
```

---

# 🔹 use()

## ✅ Use

Promise directly component me resolve.

---

## ✅ Example

```js
const data = use(fetchData());
```

---

# 🔥 Custom Hooks (VERY IMPORTANT)

## ✅ Why use?

Reusable logic create karne ke liye.

---

## ✅ Example

```js
function useCounter() {
  const [count, setCount] = useState(0);

  function increment() {
    setCount(count + 1);
  }

  return { count, increment };
}
```

---

# 🔥 Most Asked Interview Questions

---

## ✅ Difference: useState vs useRef

| useState  | useRef          |
| --------- | --------------- |
| Re-render | No re-render    |
| UI update | Mutable storage |

---

## ✅ Difference: useEffect vs useLayoutEffect

| useEffect   | useLayoutEffect |
| ----------- | --------------- |
| After paint | Before paint    |
| Async       | Sync            |

---

## ✅ Difference: useMemo vs useCallback

| useMemo        | useCallback       |
| -------------- | ----------------- |
| Memoized value | Memoized function |

---

# 🔥 Hooks Execution Order

```js
function App() {
  console.log("Render");

  useLayoutEffect(() => {
    console.log("Layout");
  });

  useEffect(() => {
    console.log("Effect");
  });

  return <h1>Hello</h1>;
}
```

## ✅ Output

```js
Render
Layout
Effect
```

---

# 🚨 Common Mistakes

| Mistake                 | Problem           |
| ----------------------- | ----------------- |
| Missing dependency      | Stale data        |
| Over useMemo            | Performance issue |
| useEffect infinite loop | Continuous render |
| Mutating state directly | UI not update     |

---

# 🎯 Easy Revision Trick

| Situation      | Hook                |
| -------------- | ------------------- |
| State chahiye  | useState            |
| Complex state  | useReducer          |
| DOM access     | useRef              |
| API call       | useEffect           |
| DOM measure    | useLayoutEffect     |
| Performance    | useMemo/useCallback |
| Global data    | useContext          |
| Smooth UI      | useTransition       |
| Reusable logic | Custom Hook         |

---

# 🔥 Final Interview Line

> “Hooks functional components me state, lifecycle aur reusable logic provide karte hain. React internally hooks ko call order ke basis par track karta hai, isliye hooks ko hamesha top level par call karna chahiye.”
