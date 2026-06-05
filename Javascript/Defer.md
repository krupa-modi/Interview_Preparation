# Defer in JavaScript

## Definition

`defer` is an attribute used inside the `<script>` tag in HTML.  
It tells the browser to download the JavaScript file in the background without blocking HTML parsing and execute it only after the HTML document is completely loaded.

---

# Syntax

```html
<script src="app.js" defer></script>
````

# Why We Use `defer`

Normally, when the browser encounters a script tag:

```html
<script src="app.js"></script>
```

the browser:

1. Stops HTML parsing
2. Downloads the JavaScript file
3. Executes the script
4. Continues parsing HTML

This can slow down page loading.

Using `defer` improves performance because HTML parsing continues while the script downloads in the background.

---

# How `defer` Works

## Without `defer`

```text
HTML Parsing Stops
↓
JavaScript Downloads
↓
JavaScript Executes
↓
HTML Parsing Continues
```

---

## With `defer`

```text
HTML Parsing Continues + JavaScript Downloads
↓
HTML Fully Loaded
↓
JavaScript Executes
```

---

# Important Features of `defer`

## 1. Non-Blocking

The browser does not stop HTML parsing while downloading the script.

---

## 2. Executes After HTML Loads

Deferred scripts run only after the complete DOM is ready.

---

## 3. Maintains Script Order

If multiple deferred scripts exist, they execute in the same order they appear.

```html
<script src="first.js" defer></script>
<script src="second.js" defer></script>
```

Execution Order:

```text
first.js
second.js
```

---

# Example

## Without `defer`

```html
<head>
  <script src="app.js"></script>
</head>

<body>
  <h1>Hello World</h1>
</body>
```

The browser pauses HTML rendering until the script is executed.

---

## With `defer`

```html
<head>
  <script src="app.js" defer></script>
</head>

<body>
  <h1>Hello World</h1>
</body>
```

The browser continues rendering HTML while downloading the script.

---

# Real DOM Example

## HTML

```html
<h1 id="title">JavaScript</h1>
<script src="app.js" defer></script>
```

## JavaScript

```js
console.log(document.getElementById("title"));
```

Output:

```js
<h1 id="title">JavaScript</h1>
```

Because the DOM is fully loaded before the script executes.

---

# `defer` vs `async`

| Feature                  | defer                    | async                                     |
| ------------------------ | ------------------------ | ----------------------------------------- |
| Blocks HTML parsing      | No                       | No                                        |
| Executes after HTML load | Yes                      | No                                        |
| Maintains order          | Yes                      | No                                        |
| Best used for            | Main application scripts | Independent scripts like ads or analytics |

---

# Advantages of `defer`

* Improves website loading performance
* Prevents blocking of HTML rendering
* Ensures DOM is fully available
* Maintains execution order of scripts

---

# When to Use `defer`

Use `defer` for:

* React applications
* Main JavaScript bundles
* DOM manipulation scripts
* Large applications

---

# When NOT to Use `defer`

Avoid `defer` when:

* The script must execute immediately
* Third-party analytics or ads scripts are used (`async` is better)

---

# Interview Answer (Short)

`defer` is an attribute used in the script tag that downloads JavaScript files in the background without blocking HTML parsing and executes them after the HTML document is fully loaded. It improves website performance and ensures the DOM is ready before script execution.

---

# Interview Answer (One Line)

`defer` allows JavaScript files to load in the background and execute after the HTML document has been completely parsed.
