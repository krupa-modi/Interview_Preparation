# useReducer Hook in React (A to Z Interview Notes)

# What is useReducer?

`useReducer` is a React Hook used for managing complex state logic.
It works similar to Redux.

Best for:
- Complex state updates
- Multiple related states
- Large forms
- Conditional logic

---

# Syntax

```jsx
const [state, dispatch] = useReducer(reducer, initialState);
````

---

# Parameters

| Part         | Meaning                     |
| ------------ | --------------------------- |
| state        | Current state               |
| dispatch     | Sends action                |
| reducer      | Function that updates state |
| initialState | Default state               |

---

# Basic Flow

```text id="r9p2qx"
dispatch(action) → reducer() → new state → UI update
```

---

# Basic Example

```jsx id="z6x1mp"
import { useReducer } from "react";

const initialState = {
  count: 0
};

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return {
        count: state.count + 1
      };

    case "decrement":
      return {
        count: state.count - 1
      };

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

      <button
        onClick={() =>
          dispatch({ type: "decrement" })
        }
      >
        -
      </button>
    </>
  );
}
```

---

# Understanding Reducer Function

Reducer decides how state should update.

---

# Example

```jsx id="m5q8vn"
function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return {
        count: state.count + 1
      };

    default:
      return state;
  }
}
```

---

# What is Action?

Action is an object describing:
"What happened?"

---

# Example

```js id="t8x2pr"
{
  type: "increment"
}
```

---

# dispatch()

Used to trigger action.

---

# Example

```jsx id="w4n7qm"
dispatch({
  type: "increment"
});
```

---

# useState vs useReducer

| useState      | useReducer      |
| ------------- | --------------- |
| Simple state  | Complex state   |
| Easy syntax   | More scalable   |
| Small apps    | Large apps      |
| Direct update | Reducer pattern |

---

# When to Use useReducer?

Use when:

* Multiple state values exist
* State logic is complex
* Next state depends on previous state
* Large forms
* Multiple actions

---

# Example with Multiple States

```jsx id="k9m3zt"
const initialState = {
  count: 0,
  darkMode: false
};
```

---

# Form Handling Example

```jsx id="p6v1rx"
const initialState = {
  name: "",
  email: ""
};

function reducer(state, action) {
  return {
    ...state,
    [action.field]: action.value
  };
}
```

---

# Dispatch with Payload

Payload means extra data sent with action.

---

# Example

```jsx id="x2q8mn"
dispatch({
  type: "add",
  payload: 5
});
```

---

# Reducer Example with Payload

```jsx id="f7p4zx"
function reducer(state, action) {
  switch (action.type) {
    case "add":
      return {
        count: state.count + action.payload
      };

    default:
      return state;
  }
}
```

# form example

Handle multiple input fields using one reducer function.

---

# Full Example

```jsx
import { useReducer } from "react";

const initialState = {
  name: "",
  password: "",
  email: "",
  city: "",
  address: ""
};

function reducer(state, action) {
  return {
    ...state,
    [action.type]: action.val
  };
}

function App() {
  const [state, dispatch] = useReducer(
    reducer,
    initialState
  );

  return (
    <div>
      <h1>useReducer Form</h1>

      <input
        type="text"
        placeholder="Enter Name"
        onChange={(e) =>
          dispatch({
            type: "name",
            val: e.target.value
          })
        }
      />

      <br /><br />

      <input
        type="text"
        placeholder="Enter Password"
        onChange={(e) =>
          dispatch({
            type: "password",
            val: e.target.value
          })
        }
      />

      <br /><br />

      <input
        type="text"
        placeholder="Enter Email"
        onChange={(e) =>
          dispatch({
            type: "email",
            val: e.target.value
          })
        }
      />

      <br /><br />

      <input
        type="text"
        placeholder="Enter City"
        onChange={(e) =>
          dispatch({
            type: "city",
            val: e.target.value
          })
        }
      />

      <br /><br />

      <input
        type="text"
        placeholder="Enter Address"
        onChange={(e) =>
          dispatch({
            type: "address",
            val: e.target.value
          })
        }
      />

      <ul>
        <li>Name: {state.name}</li>
        <li>Password: {state.password}</li>
        <li>Email: {state.email}</li>
        <li>City: {state.city}</li>
        <li>Address: {state.address}</li>
      </ul>
    </div>
  );
}

export default App;
```

---

# Lazy Initialization

Used when initial state calculation is expensive.

---

# Syntax

```jsx id="c5n9vq"
useReducer(reducer, initialValue, initFunction);
```

---

# Important Rules

* Never mutate state directly
* Always return new state object
* Reducer should be pure function

---

# Wrong Way ❌

```js id="j3x7pt"
state.count++;
return state;
```

---

# Correct Way ✅

```js id="h8m2qr"
return {
  count: state.count + 1
};
```

---

# Common Interview Questions

---

# Q1: Why use useReducer instead of useState?

## Answer

```text id="v5p8mn"
useReducer is better for complex state logic where multiple related state updates and actions are involved.
```

---

# Q2: What is reducer function?

## Answer

```text id="q1x4zr"
Reducer is a function that receives current state and action, then returns updated state.
```

---

# Q3: What is dispatch?

## Answer

```text id="n7m2px"
dispatch is used to send actions to reducer for updating state.
```

---

# Q4: Is useReducer similar to Redux?

## Answer

```text id="r4q9vz"
Yes, useReducer follows Redux-like pattern with reducer, action and dispatch.
```

---

# Real Interview Answer

## "How have you used useReducer?"

```text id="m8p3qx"
I use useReducer for complex state management like forms, counters with multiple actions and components where state logic becomes difficult to manage using useState.
```

---

# Advantages

* Better for complex logic
* Predictable state updates
* Easier debugging
* Cleaner code
* Scalable

---

# Disadvantages

* More boilerplate than useState
* Not needed for simple state

---

# Short Revision

```text id="y2m7qx"
useReducer is used for complex state management.
It works using reducer, state and dispatch.
Reducer updates state based on actions.
```

