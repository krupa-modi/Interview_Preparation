# 📘 Redux Thunk vs Redux Saga — Complete Interview Notes
# 📌 What is Redux Middleware?

Redux middleware actions aur reducers ke beech me kaam karta hai.

Ye mainly:

✅ API calls
✅ Async logic
✅ Delay
✅ Retry
✅ Logging

handle karta hai.

---

# 📌 Important Point

Both:
* Redux Thunk
* Redux Saga
are Redux middleware.

---

# 📘 What is Redux Thunk?

Redux Thunk ek simple middleware hai jo async operations handle karta hai.

Thunk hume: Function ko action ki tarah dispatch karne deta hai.

---

# 📌 Normal Redux Action

```js id="’winiijlwm"
{
  type: "FETCH_USERS"
}
```

---

# 📌 Thunk Action

```js id="’winiijlwm7"
(dispatch) => {}
```

Function dispatch hota hai.

---

# 📘 Redux Thunk Example

```js id="’winiijlwm2"
const fetchUsers = () => {
  return async (dispatch) => {
    dispatch({
      type: "LOADING"
    });

    try {
      const response =
        await fetch("/users");

      const data =
        await response.json();

      dispatch({
        type: "SUCCESS",
        payload: data
      });
    } catch (error) {
      dispatch({
        type: "ERROR",
        payload: error
      });
    }
  };
};
```

---

# 📌 How Thunk Works?

---

# 🔥 Step 1

Action dispatch hota hai.

---

# 🔥 Step 2

Thunk async API call karta hai.

---

# 🔥 Step 3

Success/Error action dispatch karta hai.

---

# 📌 Features of Thunk

✅ Easy to learn
✅ Less boilerplate
✅ Simple async handling
✅ Async/await support

---

# 📌 Limitations of Thunk

❌ Complex async flows messy ho jate hain
❌ Retry/cancel difficult
❌ Large apps me hard to maintain

---

# 📌 Best Use Cases

✅ Small-medium apps
✅ Simple API calls
✅ Beginner-friendly projects

---

# 📘 What is Redux Saga?

Redux Saga advanced middleware hai jo: Complex async side effects handle karta hai using:

# 📌 Generator Function

```js id="’winiijlwm5"
function* mySaga() {}
```

---

# 📘 Redux Saga Example

```js id="’winiijlwm0"
import {
  call,
  put,
  takeEvery
} from "redux-saga/effects";

function* fetchUsersSaga() {
  try {
    const response = yield call(
      fetch,
      "/users"
    );

    const data =
      yield response.json();

    yield put({
      type: "SUCCESS",
      payload: data
    });
  } catch (error) {
    yield put({
      type: "ERROR",
      payload: error
    });
  }
}

function* watchUsers() {
  yield takeEvery(
    "FETCH_USERS",
    fetchUsersSaga
  );
}
```

---

# 📌 How Saga Works?

---

# 🔥 Step 1

Action dispatch hota hai.

---

# 🔥 Step 2

Saga action ko listen karta hai.

---

# 🔥 Step 3

Async task run karta hai.

---

# 🔥 Step 4

Success/Error action dispatch karta hai.

---

# 📌 Features of Saga

✅ Complex async flow handling
✅ Retry support
✅ Cancellation support
✅ Better testing
✅ Better scalability

---

# 📌 Limitations of Saga

❌ Learning curve high
❌ Boilerplate ज्यादा
❌ Generators samajhna padta hai

---

# 📌 Best Use Cases

✅ Large enterprise apps
✅ Complex workflows
✅ Retry/cancel operations
✅ Background tasks

---

# 📘 Thunk vs Saga Difference Table

| Feature        | Redux Thunk | Redux Saga          |
| -------------- | ----------- | ------------------- |
| Type           | Middleware  | Middleware          |
| Async Handling | Functions   | Generator functions |
| Complexity     | Simple      | Advanced            |
| Boilerplate    | Less        | More                |
| Learning Curve | Easy        | Hard                |
| Testing        | Difficult   | Easier              |
| Retry/Cancel   | Difficult   | Easy                |
| Best For       | Small apps  | Large apps          |
| Async Logic    | Direct      | Separate layer      |

---

# 📌 Important Point

Redux Toolkit already includes: Redux Thunk by default No separate installation needed.

---

# 📘 When to Use Thunk?

✅ Simple API calls
✅ Small-medium apps
✅ Basic async handling
✅ Fast development

---

# 📘 When to Use Saga?

✅ Complex async logic
✅ Background tasks
✅ Retry/cancel/debounce
✅ Large scalable apps

---

# 📘 Easy Understanding

---

# 🔥 Redux Thunk
* Simple & Quick

---

# 🔥 Redux Saga
* Powerful & Scalable

---

# 🎯 Interview Answers

---

# ❓ What is Redux Thunk?

### ✅ Answer:

Redux Thunk is middleware used for handling asynchronous logic like API calls using functions.

---

# ❓ What is Redux Saga?

### ✅ Answer:

Redux Saga is middleware used for handling complex asynchronous operations using generator functions.

---

# ❓ Difference Between Redux Thunk and Redux Saga?

### ✅ Answer:

Redux Thunk is simpler and suitable for basic async operations, while Redux Saga is more powerful and better for complex asynchronous workflows like retry, cancellation, and background tasks.

---

# ❓ Which is Better: Thunk or Saga?

### ✅ Answer:

Thunk is better for simple and medium-sized applications, while Saga is better for large applications with complex async workflows.

---

# 📌 One-Line Summary

> Redux Thunk is simple and beginner-friendly for async logic, while Redux Saga is powerful and scalable for handling complex asynchronous workflows.

