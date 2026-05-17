# Rust, Rollup, esbuild, Webpack, Babel, Turbopack

## 1. Rust

### What is Rust?

* Rust ek **programming language** hai.
* Mainly use hota hai:

  * High performance applications
  * System programming
  * Backend development
  * Browser engines
  * Game engines

### Important Points

* Fast like C/C++
* Memory safe
* Multithreading support strong hai
* Bugs kam aate hai because ownership system

### Interview One Line

> “Rust is a fast and memory-safe systems programming language used for performance-critical applications.”

---

# 2. Rollup

### What is Rollup?

* Rollup ek **JavaScript bundler** hai.
* Multiple JS files ko combine karke ek optimized bundle banata hai.

### Mostly Used For

* Libraries build karne ke liye
* Tree shaking ke liye famous

### Important Feature

* Unused code remove karta hai (Tree Shaking)

### Interview One Line

> “Rollup is a JavaScript bundler mainly used for building optimized libraries with excellent tree shaking support.”

---

# 3. esbuild

### What is esbuild?

* esbuild ek **super fast bundler and minifier** hai.
* Go language me likha gaya hai.

### Why Popular?

* Bahot fast build speed
* Webpack/Babel se kaafi fast

### Used For

* Bundling
* Minification
* Transpiling

### Interview One Line

> “esbuild is an extremely fast JavaScript bundler and transpiler written in Go.”

---

# 4. Webpack

### What is Webpack?

* Webpack ek **module bundler** hai.
* React projects me bahot use hota tha/still hota hai.

### Work

* JS, CSS, Images sabko bundle karta hai.

### Important Concepts

* Loaders
* Plugins
* Code Splitting

### Interview One Line

> “Webpack is a module bundler that bundles JavaScript and other assets like CSS and images for web applications.”

---

# 5. Babel

### What is Babel?

* Babel ek **JavaScript transpiler** hai.

### Work

* Modern JavaScript ko old browser compatible JavaScript me convert karta hai.

### Example

```js
// Modern JS
const add = (a,b) => a+b;
```

Old browser compatible version:

```js
var add = function(a,b){
  return a+b;
}
```

### Interview One Line

> “Babel converts modern JavaScript code into backward-compatible JavaScript for older browsers.”

---

# 6. Turbopack

### What is Turbopack?

* Turbopack ek **next-generation bundler** hai made by Vercel.
* Rust language me likha gaya hai.
* Next.js ke liye optimized hai.

### Why Introduced?

* Faster than Webpack
* Faster HMR (Hot Reloading)

### Important Point

* Incremental bundling use karta hai.

### Interview One Line

> “Turbopack is a Rust-based next-generation bundler by Vercel designed for very fast Next.js development builds.”

---

# Quick Difference Table

| Tool      | Type                 | Main Purpose          |
| --------- | -------------------- | --------------------- |
| Rust      | Programming Language | High performance apps |
| Rollup    | Bundler              | Library bundling      |
| esbuild   | Bundler/Transpiler   | Very fast builds      |
| Webpack   | Module Bundler       | App bundling          |
| Babel     | Transpiler           | Modern JS → Old JS    |
| Turbopack | Bundler              | Fast Next.js builds   |

---

# Easy Interview Difference

## Babel vs Webpack

* Babel → JS convert karta hai
* Webpack → Files bundle karta hai

## Webpack vs Turbopack

* Webpack slower
* Turbopack much faster and Rust based

## Rollup vs Webpack

* Rollup → Libraries ke liye better
* Webpack → Large apps ke liye better

## esbuild vs Babel

* esbuild faster
* Babel ecosystem bigger and more plugins available
