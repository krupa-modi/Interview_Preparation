# Dynamic Imports in Next.js

# What is Dynamic Import?

Dynamic import means:

> Component ya library ko tab load karna jab uski need ho.

Instead of loading everything initially.

---

# Why Use Dynamic Import?

* Improve performance
* Reduce bundle size
* Faster page load
* Lazy loading possible

---

# Normal Import

```jsx id="7nkhwm"
import HeavyComponent from "./HeavyComponent";
```

Problem:

Component starting me hi load ho jata hai.

---

# Dynamic Import

```jsx id="dfd9ef"
import dynamic from "next/dynamic";
```

Component only when needed load hoga.

---

# Syntax

```jsx id="q6yk9y"
const Component = dynamic(() =>
  import("./Component")
);
```

---

# Basic Example

## Heavy Component

```jsx id="xw3z1h"
export default function HeavyComponent() {
  return <h1>Heavy Component</h1>;
}
```

---

## Page.js

```jsx id="9qxv80"
"use client";

import dynamic from "next/dynamic";

const HeavyComponent = dynamic(() =>
  import("./HeavyComponent")
);

export default function Home() {
  return (
    <div>
      <h1>Home Page</h1>

      <HeavyComponent />
    </div>
  );
}
```

---

# What Happens?

Initially:

```text id="oj1ueu"
Home Page loads fast
```

Then:

```text id="gkww4k"
HeavyComponent loads separately
```

---

# Loading Component Example

```jsx id="g9clow"
const HeavyComponent = dynamic(
  () => import("./HeavyComponent"),
  {
    loading: () => <p>Loading...</p>,
  }
);
```

---

# Output

While component loads:

```text id="7x4oz8"
Loading...
```

Then actual component show hoga.

---

# Disable SSR Example

# What is SSR?

Server Side Rendering

---

# Sometimes Browser APIs Error Deti Hain

Like:

* window
* localStorage
* document

---

# Solution

```jsx id="dz2qkr"
const Component = dynamic(
  () => import("./Component"),
  {
    ssr: false,
  }
);
```

---

# Why `ssr: false`?

Component sirf browser me render hoga.

Server pe nahi.

---

# Real Interview Example

## Chart Library

```jsx id="tkj1l6"
const Chart = dynamic(
  () => import("chart.js"),
  {
    ssr: false,
  }
);
```

Because chart libraries often use:

```js id="m4zvwe"
window
document
```

---

# Dynamic Import for Libraries

```jsx id="zby6zz"
const loadLodash = async () => {
  const _ = await import("lodash");

  console.log(_.default.chunk([1,2,3,4], 2));
};
```

---

# Benefits

| Benefit            | Explanation           |
| ------------------ | --------------------- |
| Faster Loading     | Initial JS smaller    |
| Better Performance | Load only needed code |
| Code Splitting     | Separate bundles      |
| Lazy Loading       | On-demand loading     |

---

# Use Cases

* Charts
* Modals
* Large Components
* Video Players
* Editors
* Maps
* Third-party libraries

---

# Interview Questions

# Q1. What is Dynamic Import?

Dynamic import allows loading components or libraries only when needed instead of loading them initially.

---

# Q2. Why use Dynamic Imports?

* Improve performance
* Reduce bundle size
* Faster page loading
* Lazy loading support

---

# Q3. What is `dynamic()` in Next.js?

`dynamic()` is a Next.js function used for dynamically importing components.

---

# Q4. Why use `ssr: false`?

To disable server-side rendering for browser-only components.

---

# Difference Between Normal Import vs Dynamic Import

| Normal Import       | Dynamic Import      |
| ------------------- | ------------------- |
| Loads immediately   | Loads on demand     |
| Bigger bundle       | Smaller bundle      |
| Slower initial load | Faster initial load |

---

# Final Revision

```text id="ecq0b0"
Dynamic Import
    ↓
Load only when needed
    ↓
Better Performance
    ↓
Smaller Bundle
    ↓
Faster Website
```
