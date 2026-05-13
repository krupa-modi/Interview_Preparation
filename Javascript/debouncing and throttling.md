# 📘 1. Debouncing in JavaScript – Complete Interview Notes

---

# 🔹 What is Debouncing?

Debouncing is a technique that:

```text id="a1d9f4"
Delays function execution until user stops triggering event for a specific time.
```

---

# 📌 Simple Definition

```text id="n7k3x2"
Debouncing ensures a function runs only after some delay once events stop firing.
```

---

# 🔥 Why Debouncing is Needed?

Some events trigger many times very quickly:

* typing
* scrolling
* resizing
* searching

Without debouncing:

```text id="w4q8m1"
Function executes too many times
```

which affects performance.

---

# 🔥 Real Life Example

```text id="t9v5r0"
Google Search Suggestions
```

When user types:

```text id="h3p2z7"
H
He
Hel
Hell
Hello
```

API should NOT call 5 times.

Instead:

```text id="u6b1n8"
Call API only after user stops typing.
```

---

# 🔥 Without Debouncing

```js id="g8f0y3"
input.addEventListener("input", () => {
  console.log("API Call");
});
```

Every keypress triggers function.

---

# ❌ Problem

Too many:

* API requests
* re-renders
* expensive operations

---

# ✅ Solution → Debouncing

---

# 🔥 How Debouncing Works

Every new event:

```text id="r5c7k1"
Clears previous timer and starts new timer.
```

Function executes only after delay completes.

---

# 📘 Debouncing Flow

```text id="m2w8d4"
Typing starts
   ↓
Timer starts
   ↓
New typing occurs
   ↓
Old timer cleared
   ↓
New timer starts
   ↓
User stops typing
   ↓
Function executes
```

---

# ✅ Debouncing Example

```js id="z4j1q6"
function debounce(fn, delay) {

  let timer;

  return function() {

    clearTimeout(timer);

    timer = setTimeout(() => {
      fn();
    }, delay);

  };

}

# ✅ Usage Example

function searchData() {
  console.log("API Call");
}

const betterFunction =
debounce(searchData, 1000);

input.addEventListener("input", betterFunction);

******************************************************OR******************************************************

<!DOCTYPE html>
<html>

<head>
  <title>Debouncing Example</title>
</head>

<body>

  <h1>Debouncing in JavaScript</h1>

  <input
    type="text"
    placeholder="Search..."
    onkeyup="handleSearch()"
  />

  <script>

    let timer;

    function callAPI() {
      console.log("API Call Done");
    }

    function handleSearch() {

      // Clear old timer
      clearTimeout(timer);

      // Start new timer
      timer = setTimeout(() => {

        callAPI();

      }, 1000);

    }

  </script>

</body>
</html>
```

---



---

# 📌 Explanation

If user types continuously:

```text id="q1m7t9"
Timer keeps resetting.
```

Function runs only after user stops typing for 1 second.

---

# 🔥 Most Common Debouncing Use Cases

| Use Case          | Why Debouncing       |
| ----------------- | -------------------- |
| Search bar        | Reduce API calls     |
| Resize event      | Improve performance  |
| Auto-save         | Avoid frequent saves |
| Form validation   | Delay validation     |
| Input suggestions | Better UX            |

---

# 🔥 Advantages of Debouncing

✅ Better performance

✅ Fewer API calls

✅ Reduced server load

✅ Smooth UI

---

# ⚠️ Disadvantages

❌ Delayed execution

❌ Not suitable for continuous real-time actions

---

# 🎯 Interview Questions

---

# ✅ Q1. What is debouncing?

Technique to delay execution until events stop firing.

---

# ✅ Q2. Why use debouncing?

To improve performance and reduce unnecessary function calls.

---

# ✅ Q3. Common use cases?

* Search input
* Resize event
* Form validation

---

# 🎯 Golden Interview Line

```text id="p8v2n6"
Debouncing delays execution until the event stops triggering for a specified time.
```

---

---

# 📘 2. Throttling in JavaScript – Complete Interview Notes

---

# 🔹 What is Throttling?

Throttling is a technique that:

```text id="k6y1m3"
Limits function execution to once in a fixed time interval.
```

---

# 📌 Simple Definition

```text id="f9w4r8"
Throttling controls how often a function can execute.
```

---

# 🔥 Why Throttling is Needed?

Some events fire continuously:

* scroll
* mousemove
* resize

Without throttling:

```text id="d3p7x5"
Function executes too many times.
```

---

# 🔥 Real Life Example

```text id="v2n8c1"
Instagram/Facebook scrolling
```

While scrolling:

```text id="q7r5t4"
Function should not execute on every pixel movement.
```

Instead:

```text id="s1m6y8"
Execute every 500ms.
```

---

# 🔥 How Throttling Works

```text id="j8x2v7"
Function runs immediately,
then waits for interval before running again.
```

---

# 📘 Throttling Flow

```text id="c4w9q2"
Event fires continuously
   ↓
Function executes once
   ↓
Wait fixed delay
   ↓
Execute again
```

---

# ✅ Throttling Example

```js id="r7v3k1"
function throttle(fn, delay) {

  let lastCall = 0;

  return function() {

    let currentTime = new Date().getTime();

    if(currentTime - lastCall >= delay) {

      lastCall = currentTime;

      fn();

    }

  };

}

function handleScroll() {
  console.log("Scrolling");
}

const betterScroll =
throttle(handleScroll, 1000);

window.addEventListener("scroll", betterScroll);


*****************************************************************OR******************************************

<!DOCTYPE html>
<html>

<head>
  <title>Throttling Example</title>

  <style>
    .box {
      height: 200px;
      width: 300px;
      overflow: auto;
      border: 2px solid black;
    }

    .content {
      height: 1000px;
    }
  </style>

</head>

<body>

  <h1>Throttling in JavaScript</h1>

  <div class="box" onscroll="handleScroll()">

    <div class="content">
      Scroll this content
    </div>

  </div>

  <script>

    function callAPI() {
      console.log("API Call Done");
    }

    let lastCall = 0;

    function handleScroll() {

      let now = Date.now();

      if(now - lastCall >= 1000) {

        lastCall = now;

        callAPI();

      }

    }

  </script>

</body>
</html>
```

---

---

# 📌 Explanation

No matter how fast scrolling happens:

```text id="n5q1w7"
Function runs only once every second.
```

---

# 🔥 Most Common Throttling Use Cases

| Use Case      | Why Throttling        |
| ------------- | --------------------- |
| Scroll event  | Improve performance   |
| Mouse move    | Reduce execution      |
| Window resize | Optimize rendering    |
| Game controls | Controlled updates    |
| Button clicks | Prevent rapid actions |

---

# 🔥 Advantages of Throttling

✅ Better performance

✅ Controlled execution

✅ Prevents overload

✅ Smooth scrolling

---

# ⚠️ Disadvantages

❌ Some events ignored

❌ Not suitable when latest value is important

---

# 🎯 Interview Questions

---

# ✅ Q1. What is throttling?

Technique that limits function execution rate.

---

# ✅ Q2. Why use throttling?

To control frequent event execution.

---

# ✅ Q3. Common use cases?

* Scroll
* Resize
* Mouse move

---

# 🎯 Golden Interview Line

```text id="x3p7m1"
Throttling limits function execution to once within a specified interval.
```

---

---

# 📘 3. Debouncing vs Throttling – Real World Use Cases & Interview Notes

---

# 🔥 Main Difference

| Feature        | Debouncing          | Throttling               |
| -------------- | ------------------- | ------------------------ |
| Execution      | After delay ends    | At fixed interval        |
| Purpose        | Wait for pause      | Limit execution rate     |
| Best For       | Search input        | Scroll/resize            |
| Event Handling | Final event matters | Continuous events matter |

---

# 🔥 Real World Use Cases

---

# 1️⃣ Search Bar → Debouncing

## ✅ Why?

User types quickly.

Without debounce:

```text id="u8v1q4"
Too many API calls
```

---

# ✅ Best Solution

```text id="r6m3x7"
Debouncing
```

Call API only after typing stops.

---

# 2️⃣ Infinite Scroll → Throttling

## ✅ Why?

Scroll event fires continuously.

Without throttle:

```text id="k4p9w2"
Performance becomes slow
```

---

# ✅ Best Solution

```text id="m7x1v5"
Throttling
```

Execute every fixed interval.

---

# 3️⃣ Window Resize

## ✅ Better Option

Usually:

```text id="p3q6r8"
Debouncing
```

because final size matters.

---

# 4️⃣ Mouse Movement Tracking

## ✅ Better Option

```text id="t1v9x4"
Throttling
```

because continuous updates required.

---

# 🔥 Visual Difference

---

# ✅ Debouncing

```text id="z7w4q1"
Typing: A B C D E
          ↓
      Only E executes
```

---

# ✅ Throttling

```text id="d5m8x3"
Scrolling continuously
↓
Runs every 1 second
```

---

# 🔥 Important Interview Difference

---

# ✅ Debouncing

```text id="n2p7v9"
Waits until event stops.
```

---

# ✅ Throttling

```text id="f4q1w6"
Executes repeatedly after fixed interval.
```

---

# 🎯 Most Asked Interview Questions

---

# ✅ Q1. Difference between debounce and throttle?

Debounce waits for inactivity,
while throttle limits execution frequency.

---

# ✅ Q2. Which is best for search input?

Debouncing.

---

# ✅ Q3. Which is best for scroll events?

Throttling.

---

# ✅ Q4. Why are debounce/throttle important?

They improve performance and reduce unnecessary executions.

---

# 🎯 Final Interview Summary

| Topic        | Meaning                           |
| ------------ | --------------------------------- |
| Debouncing   | Delay execution until event stops |
| Throttling   | Limit execution rate              |
| Debounce Use | Search input                      |
| Throttle Use | Scroll/resize                     |
| Main Goal    | Performance optimization          |
