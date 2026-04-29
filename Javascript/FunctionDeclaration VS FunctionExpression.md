
# Function Declaration vs Function Expression

## Function Declaration

```js
greet();

function greet() {
  console.log("Hello");
}
```

👉 Fully hoisted → can call before definition

---

## Function Expression

```js
sayHi(); // Error

const sayHi = function() {
  console.log("Hi");
};
```

👉 Not fully hoisted → behaves like variable

---

## Key Differences

| Feature            | Declaration   | Expression  |
| ------------------ | ------------- | ----------- |
| Hoisting           | Fully hoisted | Not hoisted |
| Call before define | ✅ Yes         | ❌ No        |
| Naming             | Required      | Optional    |

---

## Arrow Function (Expression)

```js
const add = (a, b) => a + b;
```

---

## Key Points

* Declaration → safer for reuse
* Expression → more flexible

---
