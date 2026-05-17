# 📘 Difference Between Redux and Redux Toolkit (RTK)

# 📌 What is Redux?

Redux is a state management library used to manage global state in React applications.

It follows:

# 👉 Single Store + Actions + Reducers

---

# 📌 Problem with Traditional Redux

Traditional Redux me:

❌ Bahot boilerplate code hota tha
❌ Setup complex tha
❌ Multiple files banana padta tha
❌ Immutable update manually karne padte the

---

# 📘 What is Redux Toolkit (RTK)?

Redux Toolkit is the official recommended way to write Redux logic.

It simplifies Redux development.

---

# 📌 Why Redux Toolkit Introduced?

Redux Toolkit introduced because traditional Redux was:

❌ Verbose
❌ Complex
❌ Hard to maintain

RTK ne Redux ko:

✅ Simple
✅ Cleaner
✅ Faster to write

banaya.

---

# 📌 Traditional Redux Example

---

# 🔥 Action

```js id="jlwm1g"
const increment = () => {
  return {
    type: "INCREMENT"
  };
};
```

---

# 🔥 Reducer

```js id="’winiijlwm"
function counterReducer(
  state = 0,
  action
) {
  switch (action.type) {
    case "INCREMENT":
      return state + 1;

    default:
      return state;
  }
}
```

---

# 📌 Redux Toolkit Example

```js id="’winiijlwm7"
import {
  createSlice
} from "@reduxjs/toolkit";

const counterSlice =
  createSlice({
    name: "counter",

    initialState: {
      value: 0
    },

    reducers: {
      increment: (state) => {
        state.value += 1;
      }
    }
  });

export const { increment } =
  counterSlice.actions;

export default
  counterSlice.reducer;
```

---

# 📌 Main Difference

Redux Toolkit me:

✅ Action creator automatically banta hai
✅ Reducer simpler hota hai
✅ Boilerplate kam hota hai

---

# 📌 Redux vs Redux Toolkit

| Redux                     | Redux Toolkit            |
| ------------------------- | ------------------------ |
| More boilerplate          | Less boilerplate         |
| Manual setup              | Simplified setup         |
| Separate actions/reducers | createSlice handles both |
| Complex configuration     | Easy configuration       |
| Manual immutable updates  | Uses Immer internally    |
| More code                 | Cleaner code             |

---

# 📌 What is createSlice?

`createSlice()`:

✅ Reducer create karta hai
✅ Actions create karta hai
✅ Action types create karta hai

Automatically.

---

# 📌 What is configureStore?

Redux Toolkit provides:

```js id="’winiijlwm2"
configureStore()
```

for easy store setup.

---

# 📌 Example

```js id="’winiijlwm5"
import {
  configureStore
} from "@reduxjs/toolkit";

const store =
  configureStore({
    reducer: {
      counter: counterReducer
    }
  });
```

---

# 📌 Important RTK Features

| Feature          | Purpose           |
| ---------------- | ----------------- |
| createSlice      | Reducer + actions |
| configureStore   | Store setup       |
| createAsyncThunk | API handling      |
| Immer            | Immutable updates |

---

# 📌 Why RTK is Better?

✅ Less code
✅ Easy to understand
✅ Better performance
✅ Official Redux recommendation
✅ Easier async handling

---

# 📌 Interview Important Point

Today:

# 👉 Redux Toolkit is the recommended way to use Redux.

---

# 🎯 Interview Answers

---

# ❓ Difference Between Redux and Redux Toolkit?

### ✅ Answer:

Redux Toolkit is the modern official way to use Redux that reduces boilerplate code and simplifies Redux setup, while traditional Redux requires manual setup of actions, reducers, and store configuration.

---

# ❓ Why Redux Toolkit was introduced?

### ✅ Answer:

Redux Toolkit was introduced to simplify Redux development, reduce boilerplate code, and provide better developer experience.

---

# ❓ What problem does Redux Toolkit solve?

### ✅ Answer:

Redux Toolkit solves Redux complexity issues such as excessive boilerplate, manual immutable updates, and difficult store configuration.

---

# ❓ Is Redux Toolkit replacing Redux?

### ✅ Answer:

Redux Toolkit is built on top of Redux and is now the officially recommended approach for Redux development.

