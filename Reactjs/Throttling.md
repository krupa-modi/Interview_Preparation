# Throttling in React JS

## What is Throttling?

Throttling is a technique used to limit how many times a function executes in a specific time interval.

Even if an event triggers many times, the function runs only after a fixed delay.

---

## Why Use Throttling?

Used to improve performance for:
- Scroll events
- Resize events
- Mouse move events
- Button clicks

Without throttling, functions may run hundreds of times and slow the app.

---

## Real Example

If user scrolls continuously:

Without throttling:
```text
API called 100 times
````

With throttling:

```text
API called only once every 1 second
```

---

## React Example Using lodash

### Install lodash

```bash
npm install lodash
```

---

## Example Code

```jsx id="y8k2vf"
import React, { useCallback } from "react";
import { throttle } from "lodash";

function App() {

  const handleScroll = useCallback(
    throttle(() => {
      console.log("Scrolling...");
    }, 1000),
    []
  );

  return (
    <div
      onScroll={handleScroll}
      style={{ height: "200px", overflow: "auto" }}
    >
      <div style={{ height: "1000px" }}>
        Scroll Here
      </div>
    </div>
  );
}

export default App;
```

---

## How It Works

```js id="x2fn9q"
throttle(fn, 1000)
```

Means:

* Function runs once
* Then waits 1000ms
* Ignores extra calls during that time

---

## Difference Between Debouncing and Throttling

| Debouncing                     | Throttling                |
| ------------------------------ | ------------------------- |
| Runs after delay ends          | Runs at fixed intervals   |
| Best for search input          | Best for scroll/resize    |
| Prevents unnecessary API calls | Limits repeated execution |

---

## Interview One-Line Answer

> Throttling is a performance optimization technique that limits how often a function executes within a specific time interval.
