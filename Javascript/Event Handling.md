# 1️⃣ Event Propagation in JavaScript

## 🔹 What is Event Propagation?

जब भी browser में कोई event होता है
(jese click, keypress, submit etc.)

तो event सिर्फ target element पर ही execute नहीं होता,
बल्कि DOM tree में ऊपर और नीचे travel भी करता है।

इस process को **Event Propagation** कहते हैं।
 * preventDefault() JavaScript ka method hai jo browser ke default behavior ko rokta hai.
 * stop.Propagation() event ko parent elements tak bubble/capture hone se rokne ke liye hota hai.

---

# 🔥 Event Propagation ke 3 Phases

```text
1. Capturing Phase   ↓
2. Target Phase      🎯
3. Bubbling Phase    ↑
```

Example DOM:

```html
<body>
  <div id="parent">
    <button id="child">Click Me</button>
  </div>
</body>
```

---

## 🔹 Flow

```text
BODY
  ↓
DIV (parent)
  ↓
BUTTON (target)
  ↑
DIV
  ↑
BODY
```

---

# 📌 Real Meaning

* Event first top → bottom travel karta hai
  → Capturing

* Fir target element par aata hai
  → Target phase

* Fir bottom → top travel karta hai
  → Bubbling

---

# ✅ Example

```html
<div id="parent">
  <button id="child">Click Me</button>
</div>

<script>
const parent = document.getElementById("parent");
const child = document.getElementById("child");

parent.addEventListener("click", () => {
  console.log("Parent Clicked");
});

child.addEventListener("click", () => {
  console.log("Button Clicked");
});
</script>
```

### Output

```js
Button Clicked
Parent Clicked
```

Because default behavior = Bubbling.

---

# 📌 Kab Use Hota Hai?

Event propagation automatically browser handle karta hai.

Developer mostly use karta hai:

* Event delegation
* Prevent parent event
* Performance optimization
* Nested components handling

---

---

# 2️⃣ Event Bubbling

# 🔹 What is Event Bubbling?

Event target element se start hota hai
aur parent elements ki taraf upar move karta hai.

```text
Child → Parent → Grandparent
```

---

# ✅ Example

```html
<div id="parent">
  <button id="child">Click</button>
</div>

<script>
document.getElementById("parent")
.addEventListener("click", () => {
  console.log("Parent");
});

document.getElementById("child")
.addEventListener("click", () => {
  console.log("Child");
});
</script>
```

---

## ✅ Output

```js
Child
Parent
```

---

# 🔥 Why?

Because click first child par hua,
fir bubble hokar parent tak gaya.

---

# 📌 Real Life Example

```text
Button inside Card inside Page
```

Button click hone par:

* Button event
* Card event
* Page event

sab trigger ho sakte hain.

---

# 📌 stopPropagation()

Agar bubbling rokni ho:

```js
event.stopPropagation();
```

---

# ✅ Example

```js
child.addEventListener("click", (event) => {
  console.log("Child");
  event.stopPropagation();
});
```

### Output

```js
Child
```

Parent execute nahi hoga.

---

# 📌 Kab Use Karna Chahiye?

## ✅ Use Cases

### 1. Parent Handling

```text
Dropdown inside modal
```

### 2. Analytics Tracking

Parent par listener lagana.

### 3. Event Delegation

Most important use.

---

# 📌 Kaha Avoid Kare?

Nested buttons ya complex UI me unwanted triggers aa sakte hain.

---

---

# 3️⃣ Event Capturing

# 🔹 What is Event Capturing?

Capturing bubbling ka opposite hai.

Event top → bottom travel karta hai.

```text
Parent → Child
```

---

# 📌 Default Behavior?

JavaScript default me bubbling use karta hai.

Capturing enable karna padta hai.

---

# ✅ Syntax

```js
addEventListener(event, function, true)
```

OR

```js
addEventListener(event, function, {
  capture: true
})
```

---

# ✅ Example

```html
<div id="parent">
  <button id="child">Click</button>
</div>

<script>
parent.addEventListener("click", () => {
  console.log("Parent");
}, true);

child.addEventListener("click", () => {
  console.log("Child");
}, true);
</script>
```

---

# ✅ Output

```js
Parent
Child
```

Because capturing top → bottom hota hai.

---

# 📌 Kab Use Karna Chahiye?

## ✅ Use Cases

### 1. Early Event Handling

Parent pe pehle control chahiye.

### 2. Security / Validation

Before child executes.

### 3. Special UI Frameworks

Complex event systems.

---

# 📌 Real Example

```text
Modal ke bahar click detect karna
```

---

---

# 4️⃣ Event Delegation

# 🔹 What is Event Delegation?

Ek parent element par event listener lagakar
uske child elements ke events handle karna.

---

# 🔥 Why Important?

Agar 100 buttons hain:

❌ Wrong Approach

```js
100 listeners
```

✅ Better Approach

```js
1 parent listener
```

---

# ✅ Example

```html
<ul id="list">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>

<script>
document.getElementById("list")
.addEventListener("click", (event) => {

  if(event.target.tagName === "LI") {
    console.log(event.target.innerText);
  }

});
</script>
```

---

# ✅ Output

```js
Item 1
Item 2
Item 3
```

depending on clicked item.

---

# 🔥 event.target

```js
event.target
```

Actual clicked element return karta hai.

---

# 📌 Biggest Advantage

## ✅ Dynamic Elements Handle Hote Hai

```js
new elements automatically work karte hain
```

without new listener.

---

# 📌 Real Life Example

## ✅ Todo App

```text
Delete buttons
Checkboxes
Dynamic items
```

---

# 📌 Kab Use Karna Chahiye?

## ✅ Use Cases

### 1. Dynamic Elements

DOM me baad me add hone wale elements.

### 2. Performance Optimization

Thousands listeners avoid.

### 3. Tables / Lists

Large data rendering.

---

# 📌 Kaha Avoid Kare?

Agar child hierarchy bahut complex ho.

---

---

# 5️⃣ Difference Between Event Bubbling and Event Delegation

| Feature           | Event Bubbling                     | Event Delegation                      |
| ----------------- | ---------------------------------- | ------------------------------------- |
| Meaning           | Event child se parent tak jata hai | Parent listener se child handle karna |
| Purpose           | Browser mechanism                  | Developer technique                   |
| Automatic?        | Yes                                | No                                    |
| Uses              | Event propagation                  | Performance optimization              |
| Listener Position | Child + Parent                     | Mostly Parent                         |
| Dynamic Elements  | Directly support nahi              | Best support                          |
| Based On          | Propagation                        | Bubbling                              |
| Memory Efficient  | No                                 | Yes                                   |
| Common Use        | Nested events                      | Lists, tables, dynamic UI             |

---

# 🔥 Important Interview Point

## ✅ Event Delegation works because of Event Bubbling

Agar bubbling nahi hoti,
to delegation possible nahi hota.

---

# 🎯 Interview Questions

---

# ✅ Q1. What is Event Propagation?

DOM me event ka travel process.

---

# ✅ Q2. What is Event Bubbling?

Child → Parent event flow.

---

# ✅ Q3. What is Event Capturing?

Parent → Child event flow.

---

# ✅ Q4. Difference between Bubbling and Capturing?

| Bubbling         | Capturing       |
| ---------------- | --------------- |
| Bottom → Top     | Top → Bottom    |
| Default behavior | Manually enable |

---

# ✅ Q5. What is Event Delegation?

Parent listener use karke child events handle karna.

---

# ✅ Q6. Why Event Delegation is useful?

* Better performance
* Dynamic elements support
* Less memory usage

---

# ✅ Q7. What is event.target?

Actual clicked element.

---

# ✅ Q8. What is stopPropagation()?

Event ko parent tak jane se rokta hai.

---

# 🔥 Complete Example (MOST IMPORTANT)

```html
<div id="parent">
  <button id="btn">Click</button>
</div>

<script>

const parent = document.getElementById("parent");
const btn = document.getElementById("btn");

parent.addEventListener("click", () => {
  console.log("Parent Bubbling");
});

parent.addEventListener("click", () => {
  console.log("Parent Capturing");
}, true);

btn.addEventListener("click", () => {
  console.log("Button");
});

</script>
```

---

# ✅ Output

```js
Parent Capturing
Button
Parent Bubbling
```

---

# 🚀 Final Summary

| Concept    | Direction               | Default?      |
| ---------- | ----------------------- | ------------- |
| Capturing  | Top → Bottom            | No            |
| Bubbling   | Bottom → Top            | Yes           |
| Delegation | Parent handles children | Uses Bubbling |

---

# 🎯 Golden Interview Line

```text
Event Delegation internally works because of Event Bubbling.
```


# 📘 addEventListener() – Interview Notes

## 🔹 What is addEventListener()?

`addEventListener()` ka use kisi HTML element par event attach karne ke liye hota hai.

---

# ✅ Syntax

```js id="pt8y8g"
element.addEventListener(event, function, options)
```

---

# ✅ Example

```js id="6s8z8z"
button.addEventListener("click", () => {
  console.log("Button Clicked");
});
```

---

# 📌 Parameters

| Parameter | Meaning                           |
| --------- | --------------------------------- |
| event     | Event name (`click`, `mouseover`) |
| function  | Callback function                 |
| options   | Extra behavior control            |

---

# 🔥 addEventListener Options

---

# 1️⃣ capture

Event capturing enable karta hai.

```js id="0bq7rz"
element.addEventListener("click", fn, {
  capture: true
});
```

✅ Default:

```js id="rn6ws0"
false
```

---

# 2️⃣ once

Event sirf ek baar chalega.

```js id="9e3y3k"
element.addEventListener("click", fn, {
  once: true
});
```

---

# 3️⃣ passive

Browser ko batata hai ki `preventDefault()` use nahi hoga.

Performance improve hoti hai.

```js id="2a6mr6"
element.addEventListener("scroll", fn, {
  passive: true
});
```

---

# 4️⃣ signal

AbortController ke through listener remove kar sakte hain.

```js id="m6m5a2"
const controller = new AbortController();

element.addEventListener("click", fn, {
  signal: controller.signal
});

controller.abort();
```

---

# 🎯 Important Interview Points

* Multiple listeners add kar sakte hain
* Old `onclick` se better hai
* Bubbling + Capturing support karta hai
* Dynamic event handling me useful

---

# ✅ Difference: onclick vs addEventListener

| onclick       | addEventListener  |
| ------------- | ----------------- |
| Ek hi handler | Multiple handlers |
| Limited       | Flexible          |
| No options    | Options available |

---

# 🚀 Most Asked Interview Line

```text id="n1cvfd"
addEventListener() is used to attach events to elements with support for bubbling, capturing, and multiple handlers.
```

````md id="m8x2qp"
# ✅ JavaScript Events (Interview Notes)

# ✅ 1. addEventListener()

`addEventListener()` is used to attach an event to an element.

---

# ✅ Syntax

```js
element.addEventListener("event", callback);
````

---

# ✅ Example

```js id="p4m8tw"
const btn = document.querySelector("button");

btn.addEventListener("click", function() {
  console.log("Button Clicked");
});
```

---

# 🎯 Interview Definition

> `addEventListener()` is used to attach event handlers to HTML elements.

---

# ✅ Advantages of addEventListener()

✅ Multiple events attach kar sakte
✅ Better than inline events
✅ Supports event bubbling/capturing

---

# ✅ 2. Event Object

When an event occurs,
JavaScript automatically passes an event object.

It contains information about the event.

---

# ✅ Example

```js id="v7q1la"
const btn = document.querySelector("button");

btn.addEventListener("click", function(event) {

  console.log(event);

});
```

---

# 🔥 Important Properties

| Property                  | Meaning                      |
| ------------------------- | ---------------------------- |
| `event.target`            | Element that triggered event |
| `event.type`              | Event type                   |
| `event.preventDefault()`  | Prevent default behavior     |
| `event.stopPropagation()` | Stop bubbling                |

---

# ✅ event.target Example

```js id="k5r2vt"
btn.addEventListener("click", function(event) {

  console.log(event.target);

});
```

---

# 🎯 Interview Definition

> Event object contains information related to the triggered event.

---

# ✅ 3. stopPropagation()

Used to stop event bubbling.

---

# 🔥 What is Event Bubbling?

Event child → parent → grandparent tak move karta hai.

---

# ✅ Example Without stopPropagation()

```js id="x2m9pw"
<div id="parent">
  <button id="child">Click</button>
</div>
```

```js id="f8x2lm"
document.getElementById("parent")
.addEventListener("click", () => {
  console.log("Parent Clicked");
});

document.getElementById("child")
.addEventListener("click", () => {
  console.log("Button Clicked");
});
```

---

# ✅ Output

```js id="r4p7qa"
Button Clicked
Parent Clicked
```

Because event bubbled to parent.

---

# ✅ Using stopPropagation()

```js id="z6m1tw"
document.getElementById("child")
.addEventListener("click", (event) => {

  event.stopPropagation();

  console.log("Button Clicked");
});
```

---

# ✅ Output

```js id="c2q8vp"
Button Clicked
```

Parent event stop ho gaya.

---

# 🎯 Interview Definition

> `stopPropagation()` prevents an event from bubbling to parent elements.

---

# 🚀 Quick Revision Table

| Concept          | Purpose           |
| ---------------- | ----------------- |
| addEventListener | Attach event      |
| Event Object     | Event information |
| stopPropagation  | Stop bubbling     |
| event.target     | Triggered element |

---

# 💡 One-Line Memory Trick

```js id="j7p3lx"
stopPropagation() stops event from moving to parent elements.
```


