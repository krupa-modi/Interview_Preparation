## 📌 What is Tree Shaking?

Tree Shaking ek optimization technique hai jisme **unused code remove** kiya jata hai final bundle se.

Simple words me:

👉 Jo code application me use nahi ho raha
👉 Usko build ke time automatically hata diya jata hai

Isse:

* Bundle size kam hota hai
* Website fast load hoti hai
* Performance improve hoti hai

---

# 🌲 Why name “Tree Shaking”?

Code ko ek **dependency tree** ki tarah treat kiya jata hai.

Bundler check karta hai:

* Kaunsa function use ho raha hai
* Kaunsa import unused hai

Unused branches ko “shake” karke remove kar diya jata hai.

---

# 📌 Example Without Tree Shaking

```js
// math.js

export function add(a, b) {
  return a + b;
}

export function sub(a, b) {
  return a - b;
}

export function multiply(a, b) {
  return a * b;
}
```

```js
// app.js

import { add } from "./math";

console.log(add(2, 3));
```

---

## 🔥 Problem

Humne sirf `add()` use kiya hai.

Lekin agar optimization na ho to:

```js
add()
sub()
multiply()
```

sab final bundle me aa jayega.

Bundle unnecessary bada ho jayega.

---

# ✅ Tree Shaking After Optimization

Bundler dekhega:

```js
Sirf add() use hua hai
```

To final bundle me:

```js
function add(a, b) {
  return a + b;
}
```

sirf ye hi rahega.

Unused:

```js
sub()
multiply()
```

remove ho jayenge.

---

# 📌 Tree Shaking Kab Hota Hai?

Tree shaking mostly:

* Production build me hota hai
* Bundlers perform karte hain

Jaise:

* Webpack
* Rollup
* Vite
* Parcel
* ESBuild

---

# 📌 Important Requirement

## ✅ ES Modules Required

Tree shaking properly sirf:

```js
import/export
```

ke sath kaam karta hai.

---

# ❌ CommonJS me Problem

```js
const math = require("./math");
```

Bundler ko exact dependency analysis difficult hota hai.

Isliye tree shaking proper nahi hoti.

---

# ✅ ES Module Example

```js
import { add } from "./math";
```

Ye static import hai.

Bundler easily analyze kar sakta hai.

---

# 📌 How Tree Shaking Works Internally

## Step 1 → Dependency Graph Banta Hai

Bundler sab imports ko analyze karta hai.

```js
A imports B
B imports C
```

Ek graph create hota hai.

---

## Step 2 → Used Exports Find Hote Hai

Bundler check karta hai:

```js
Kaunsa export actually use hua?
```

---

## Step 3 → Dead Code Elimination

Unused exports remove kar diye jate hain.

Isko:

# 🔥 Dead Code Elimination (DCE)

bhi bolte hain.

---

# 📌 JavaScript Example

## utils.js

```js
export const name = "Krupa";

export function greet() {
  console.log("Hello");
}

export function bye() {
  console.log("Bye");
}
```

---

## app.js

```js
import { greet } from "./utils";

greet();
```

---

# ✅ Final Bundle

```js
function greet() {
  console.log("Hello");
}

greet();
```

`bye()` remove ho jayega.

---

# 📌 Tree Shaking in React

React applications me tree shaking bahot important hota hai.

Kyuki React apps me:

* bahot libraries hoti hain
* components zyada hote hain
* bundle size bada ho sakta hai

---

# 📌 React Example

```js
import { useState } from "react";
```

Agar sirf `useState` use hua:

✅ Bundler sirf required code include karega.

Unused React utilities remove ho sakti hain.

---

# 📌 Component Example

## Button.js

```js
export function Button() {
  return <button>Click</button>;
}

export function Card() {
  return <div>Card</div>;
}
```

---

## App.js

```js
import { Button } from "./Button";

function App() {
  return <Button />;
}
```

---

# ✅ Final Bundle

Sirf:

```js
Button
```

component include hoga.

Unused:

```js
Card
```

remove ho jayega.

---

# 📌 Tree Shaking in React Libraries

Popular libraries tree shaking support karti hain:

* React
* Lodash-es
* Material UI
* RxJS

---

# ❌ Bad Import Example

```js
import _ from "lodash";
```

Ye pura lodash import kar sakta hai.

Bundle bada ho jayega.

---

# ✅ Good Import

```js
import debounce from "lodash/debounce";
```

ya

```js
import { debounce } from "lodash-es";
```

Sirf required code aayega.

---

# 📌 Side Effects Problem

Kabhi kabhi bundler code remove nahi karta because:

```js
import "./styles.css";
```

Ye side effect create karta hai.

Bundler cautious rehta hai.

---

# 📌 package.json me sideEffects

```json
{
  "sideEffects": false
}
```

Ye bundler ko batata hai:

✅ files safe hain remove karne ke liye.

---

# 📌 Webpack Tree Shaking

Webpack production mode me automatically tree shaking karta hai.

```js
mode: "production";
```

---

# 📌 Vite Tree Shaking

Vite internally:

* Rollup
* ESBuild

use karta hai.

Isliye tree shaking bahot fast aur efficient hoti hai.

---

# 📌 Benefits of Tree Shaking

## ✅ 1. Smaller Bundle

File size kam hoti hai.

---

## ✅ 2. Faster Loading

Website jaldi load hoti hai.

---

## ✅ 3. Better Performance

Browser ko kam JS parse karna padta hai.

---

## ✅ 4. Better SEO

Fast website → better SEO.

---

## ✅ 5. Improved User Experience

Page responsive feel hota hai.

---

# 📌 Real Interview Definition

> Tree Shaking is a JavaScript optimization technique used by bundlers like Webpack and Rollup to remove unused code from the final bundle, reducing bundle size and improving performance.

---

# 📌 Interview Important Points 🔥

| Topic        | Important             |
| ------------ | --------------------- |
| Works with   | ES Modules            |
| Removes      | Unused code           |
| Done by      | Bundlers              |
| Used in      | Production build      |
| Helps in     | Performance           |
| Another name | Dead Code Elimination |

---

# 📌 Difference: Tree Shaking vs Code Splitting

| Tree Shaking        | Code Splitting            |
| ------------------- | ------------------------- |
| Removes unused code | Splits bundle into chunks |
| Reduce size         | Lazy load files           |
| Optimization        | Loading strategy          |

---

# 📌 Short Interview Answer

> Tree Shaking is an optimization process in JavaScript where unused code is removed from the final bundle during build time. It works mainly with ES Modules and is commonly used in React applications through bundlers like Webpack, Rollup, and Vite to improve performance and reduce bundle size.
