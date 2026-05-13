# 1️⃣ What is DOM?

DOM stands for:

```text id="mupjcc"
Document Object Model
```

DOM is a tree-like structure created by the browser from HTML.

JavaScript uses the DOM to:

* Access elements
* Change content
* Change styles
* Add/remove elements
* Handle events

---

# ✅ Example DOM Structure

```html id="kslr9j"
<body>
  <div>
    <p>Hello</p>
  </div>
</body>
```

DOM Tree:

```text id="s6kq5j"
Document
 └── html
      └── body
           └── div
                └── p
```

---

# 🔥 DOM Manipulation

DOM Manipulation means:

```text id="f9vmys"
Changing or controlling HTML elements using JavaScript.
```

---

# 2️⃣ getElementById()

## ✅ Definition

Used to select an element by its `id`.

---

# ✅ Syntax

```js id="4by47r"
document.getElementById("idName")
```

---

# ✅ Example

```html id="5umovv"
<h1 id="title">Hello</h1>

<script>
const heading = document.getElementById("title");

console.log(heading);
</script>
```

---

# 📌 Important Points

* Returns single element
* `id` must be unique
* Fastest selector

---

# ✅ Use Case

```text id="s3dv7k"
When element has unique id.
```

---

# 3️⃣ querySelector()

## ✅ Definition

Used to select first matching CSS selector.

---

# ✅ Syntax

```js id="ps4cmy"
document.querySelector("selector")
```

---

# ✅ Example

```html id="11s7m8"
<p class="text">Hello</p>

<script>
const para = document.querySelector(".text");
</script>
```

---

# 📌 Supports

* id
* class
* tag
* attribute selectors

---

# ✅ Examples

```js id="s6m3zd"
document.querySelector("#id")

document.querySelector(".class")

document.querySelector("div")
```

---

# 4️⃣ getElementById vs querySelector

| Feature     | getElementById | querySelector          |
| ----------- | -------------- | ---------------------- |
| Select By   | Only id        | Any CSS selector       |
| Returns     | Single element | First matching element |
| Speed       | Faster         | Slightly slower        |
| Flexibility | Less           | More                   |
| Syntax      | Simple         | CSS style              |

---

# 🎯 Interview Line

```text id="g2fob8"
getElementById is faster, while querySelector is more flexible because it supports all CSS selectors.
```

---

# 5️⃣ createElement()

## ✅ Definition

Used to create new HTML element dynamically.

---

# ✅ Syntax

```js id="n9d9fi"
document.createElement("tagName")
```

---

# ✅ Example

```js id="j15eeh"
const div = document.createElement("div");

console.log(div);
```

---

# 📌 Real Use

Dynamic UI creation:

* Todo app
* Chat messages
* Dynamic cards

---

# 6️⃣ appendChild()

## ✅ Definition

Used to add a child element inside parent element.

---

# ✅ Syntax

```js id="d1t3ev"
parent.appendChild(child)
```

---

# ✅ Example

```html id="8r17dc"
<div id="container"></div>

<script>
const p = document.createElement("p");

p.innerText = "Hello World";

document
.getElementById("container")
.appendChild(p);
</script>
```

---

# ✅ Output

```html id="02xq8m"
<div id="container">
  <p>Hello World</p>
</div>
```

---

# 📌 Important Point

`appendChild()` always adds at the end.

---

# 🎯 Interview Line

```text id="oq0x64"
createElement() creates new elements, and appendChild() inserts them into the DOM.
```

---

# 7️⃣ innerHTML

## ✅ Definition

Gets or sets HTML content inside element.

---

# ✅ Example

```html id="17ihvg"
<div id="box"></div>

<script>
document.getElementById("box").innerHTML =
"<h1>Hello</h1>";
</script>
```

---

# ✅ Output

```html id="rk8czq"
<div id="box">
  <h1>Hello</h1>
</div>
```

---

# 📌 Important Point

HTML tags are rendered.

---

# ⚠️ Security Risk

Can cause:

```text id="72t8fz"
XSS attacks
```

if user input is inserted directly.

---

# 8️⃣ innerText

## ✅ Definition

Gets or sets only visible text.

---

# ✅ Example

```js id="xsy1b5"
document.getElementById("box").innerText =
"<h1>Hello</h1>";
```

---

# ✅ Output

```html id="g2h22s"
<div id="box">
  <h1>Hello</h1>
</div>
```

Shown as plain text.

---

# 📌 Important Point

HTML tags are NOT rendered.

---

# 9️⃣ innerHTML vs innerText

| Feature              | innerHTML | innerText |
| -------------------- | --------- | --------- |
| Reads HTML           | Yes       | No        |
| Supports Tags        | Yes       | No        |
| Returns Visible Text | No        | Yes       |
| Security Risk        | Higher    | Safer     |
| Performance          | Slower    | Faster    |
| Use Case             | Add HTML  | Add Text  |

---

# ✅ Example Difference

```js id="bg4l1g"
element.innerHTML = "<b>Hello</b>";
```

Output:

```text id="lyjkgi"
Hello (bold)
```

---

```js id="pkql50"
element.innerText = "<b>Hello</b>";
```

Output:

```text id="ocds2u"
<b>Hello</b>
```

---

# 🔥 Most Asked Interview Questions

---

# ✅ Q1. What is DOM?

Browser representation of HTML as objects.

---

# ✅ Q2. Difference between getElementById and querySelector?

`getElementById` selects by id only, while `querySelector` supports all CSS selectors.

---

# ✅ Q3. Difference between innerHTML and innerText?

`innerHTML` renders HTML tags, while `innerText` handles only plain text.

---

# ✅ Q4. Why is innerHTML risky?

Because it can allow XSS attacks.

---

# ✅ Q5. What does appendChild do?

Adds child element inside parent element.

---

# ✅ Q6. Why use createElement?

To dynamically create elements.

---

# 🚀 Complete Example

```html id="ol2ypm"
<div id="app"></div>

<script>

const heading = document.createElement("h1");

heading.innerText = "DOM Manipulation";

document
.getElementById("app")
.appendChild(heading);

</script>
```

---

# 🎯 Final Interview Summary

| Topic          | Purpose                   |
| -------------- | ------------------------- |
| getElementById | Select by id              |
| querySelector  | Select using CSS selector |
| createElement  | Create new element        |
| appendChild    | Add element to DOM        |
| innerHTML      | Insert HTML               |
| innerText      | Insert plain text         |
