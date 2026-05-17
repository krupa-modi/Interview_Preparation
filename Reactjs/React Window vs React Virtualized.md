# 🚀 react-window vs react-virtualized

* Dono libraries large list rendering optimize karne ke liye use hoti hain.
* Ye virtualization technique use karti hain.

Dono libraries ka purpose same hai:

👉 **Large lists ko efficiently render karna (Virtualization)**
👉 Sirf visible items render karna
👉 Baaki items DOM me mount nahi hote

---

# 🧠 What is Virtualization?

Virtualization ka matlab:

> “Screen pe sirf visible items render karna instead of poori large list render karna.”

---

# 🧠 Problem Kya Tha?

Agar 10,000 items ka list render kar diya:

* DOM heavy ho jayega
* Scroll lag karega
* Memory consumption badh jayega
* Re-render expensive ho jayega

---

# ✅ Solution → Windowing / Virtualization

Matlab:

👉 Screen pe jo visible hai sirf wahi render karo
👉 Baaki items scroll hone pe dynamically load karo

---

# 🔥 How Virtualization Works?

```txt id="mmd9ji"
User Scrolls
      ↓
Visible Items Calculate
      ↓
Only Visible Rows Render
      ↓
Off-screen Rows Remove
```

---

# 🔥 1️⃣ react-virtualized

📦 Older library
📅 Around 2016 popular hui
👨 Same author: Brian Vaughn

Feature-rich library hai.

---

# 📌 Features

* List
* Grid
* Table
* AutoSizer
* CellMeasurer
* InfiniteLoader
* Dynamic row height
* WindowScroller

---

# ✅ Pros

✔ Powerful
✔ Advanced features
✔ Complex tables support
✔ Dynamic heights support

---

# ❌ Cons

❌ Large bundle size
❌ Complex API
❌ More setup
❌ Slightly heavier performance

---

# 🔥 react-virtualized Example

```jsx id="s31v57"
import { List } from "react-virtualized";

function rowRenderer({ index, key, style }) {
  return (
    <div key={key} style={style}>
      Row {index}
    </div>
  );
}

<List
  width={300}
  height={400}
  rowCount={10000}
  rowHeight={35}
  rowRenderer={rowRenderer}
/>
```

---

# 🔥 2️⃣ react-window

📦 Lightweight version of react-virtualized
👨 Same author: Brian Vaughn

Modern optimized virtualization library.

---

# 📌 Features

* FixedSizeList
* VariableSizeList
* FixedSizeGrid
* VariableSizeGrid

---

# ✅ Pros

✔ Small bundle size
✔ Faster rendering
✔ Simple API
✔ Better performance
✔ Easy to learn

---

# ❌ Cons

❌ Limited advanced features
❌ Dynamic layouts harder
❌ Fewer built-in utilities

---

# 🔥 react-window Example

```jsx id="h91s9h"
import { FixedSizeList as List } from "react-window";

const Row = ({ index, style }) => (
  <div style={style}>
    Row {index}
  </div>
);

function App() {
  return (
    <List
      height={400}
      itemCount={10000}
      itemSize={35}
      width={300}
    >
      {Row}
    </List>
  );
}
```

---

# 📌 Important Props (react-window)

| Prop      | Use              |
| --------- | ---------------- |
| height    | Container height |
| width     | Container width  |
| itemCount | Total items      |
| itemSize  | Each row height  |

---

# 🔥 FixedSizeList vs VariableSizeList

| Hook             | Use                   |
| ---------------- | --------------------- |
| FixedSizeList    | Same row height       |
| VariableSizeList | Different row heights |

---

# 📊 Comparison Table

| Feature           | react-window | react-virtualized |
| ----------------- | ------------ | ----------------- |
| Bundle Size       | Small        | Large             |
| Performance       | Faster       | Slightly Heavy    |
| API               | Simple       | Complex           |
| Learning Curve    | Easy         | Medium            |
| Advanced Features | Limited      | Many              |
| Dynamic Heights   | Basic        | Excellent         |
| Recommended Today | ✅ Yes        | ⚠ Only if needed  |

---

# 🔥 Why react-window is Faster?

Because:

✅ Less abstraction
✅ Smaller codebase
✅ Less memory usage
✅ Less DOM calculations

---

# 📌 Real DOM Difference

Without virtualization:

```txt id="ib8v85"
10000 rows = 10000 DOM nodes
```

With virtualization:

```txt id="dr0d8w"
Visible 20 rows = Only 20 DOM nodes
```

---

# 🔥 Important Interview Questions

# ❓ Why use virtualization?

> To improve rendering performance for large lists.

---

# ❓ Why react-window preferred today?

> Because it is lightweight, faster, and simpler than react-virtualized.

---

# ❓ What problem do these libraries solve?

> Large list rendering and DOM performance issues.

---

# ❓ Difference between FixedSizeList and VariableSizeList?

| FixedSizeList    | VariableSizeList    |
| ---------------- | ------------------- |
| Same height rows | Dynamic height rows |

---

# 🧠 Kab Kaunsa Use Kare?

## ✅ Use react-window

* Large flat list
* Better performance needed
* Small bundle size
* Modern applications

---

## ✅ Use react-virtualized

* Complex tables/grids
* Dynamic row height
* Advanced infinite scrolling
* Enterprise dashboards

---

# 🔥 Real Production Insight

Modern apps mostly use:

* react-window
* TanStack Virtual
* MUI DataGrid (internally virtualized)

react-virtualized ab comparatively kam use hota hai.

---

# 🎯 Interview Answer (Best)

> “Both react-window and react-virtualized are used for list virtualization in React to improve performance by rendering only visible items. react-window is lightweight, faster, and preferred for modern applications, while react-virtualized provides more advanced features like dynamic row heights, tables, and grids but has a larger bundle size and more complex API.”
