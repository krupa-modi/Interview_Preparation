# ✅ import vs require in JavaScript

# 🔥 What is `import`?

`import` is used in ES6 Modules.

```js
import add from "./math.js";
````

Modern JavaScript / React / Next.js me mostly use hota hai.
---

# 🔥 What is `require`?

`require` is used in CommonJS modules.

```js
const add = require("./math");
```

Mostly old Node.js projects me use hota hai.

---

# 🚀 Main Difference

| import                  | require                 |
| ----------------------- | ----------------------- |
| ES6 Module              | CommonJS                |
| Modern syntax           | Old syntax              |
| Top pe likhna padta hai | Kahin bhi use kar sakte |
| Async loading           | Sync loading            |
| React/Next.js me common | Old Node.js me common   |

---

# ✅ import Example

## math.js

```js id="c8r6lp"
export default function add(a, b) {
  return a + b;
}
```

## app.js

```js id="uv7u7d"
import add from "./math.js";

console.log(add(2, 3));
```

---

# ✅ require Example

## math.js

```js id="2ekm8y"
function add(a, b) {
  return a + b;
}

module.exports = add;
```

## app.js

```js id="q2t9df"
const add = require("./math");

console.log(add(2, 3));
```

---

# 🎯 Interview Definition

> `import` ES6 module system ka part hai,
> while `require` CommonJS module system ka part hai.

---

# 🔥 Named Export vs Default Export

# ✅ Default Export

File me sirf ek default export hota hai.

---

## math.js

```js id="x89i8o"
export default function add(a, b) {
  return a + b;
}
```

---

## app.js

```js id="98frht"
import add from "./math.js";
```

---

# ⚡ Important Point

Default export me:

```js id="d0q9y2"
name same hona zaruri nahi
```

```js id="zvjlwm"
import xyz from "./math.js";
```

Ye bhi chalega ✅

---

# ✅ Named Export

Multiple exports kar sakte ho.

---

## math.js

```js id="l8j1o2"
export const add = (a, b) => a + b;

export const sub = (a, b) => a - b;
```

---

## app.js

```js id="3b4l5u"
import { add, sub } from "./math.js";
```

---

# ⚡ Important Point

Named export me:

```js id="v2jjlwm"
same name use karna padta hai
```

---

# ✅ Rename bhi kar sakte ho

```js id="a6n7rp"
import { add as sum } from "./math.js";
```

---

# 🚀 Difference Table

| Default Export         | Named Export        |
| ---------------------- | ------------------- |
| Only one export        | Multiple exports    |
| No curly braces        | Curly braces needed |
| Any name use kar sakte | Same name required  |
| `export default`       | `export`            |

---

# 🔥 Combined Example

## math.js

```js id="5o8fda"
export default function multiply(a, b) {
  return a * b;
}

export const add = (a, b) => a + b;
```

---

## app.js

```js id="4u9tws"
import multiply, { add } from "./math.js";

console.log(multiply(2, 3));
console.log(add(2, 3));
```

---

# 🎯 Interview Questions

## Q1: Can we have multiple default exports?

## ❌ Answer:

No

---

## Q2: Can we have multiple named exports?

## ✅ Answer:

Yes

---

## Q3:Which export is mostly used in React components?

## ✅ Answer:

Default export

---

# 💡 Quick Revision

| Concept        | Meaning                  |
| -------------- | ------------------------ |
| import         | ES6 module syntax        |
| require        | CommonJS syntax          |
| default export | One export               |
| named export   | Multiple exports         |
| `{}`           | Named export me use hota |

---

# 🚀 One-Line Memory Trick

```js id="d7s9qa"
Default Export → ek file ka main export

Named Export → multiple exports
```

