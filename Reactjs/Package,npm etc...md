# 📌 What is NPM?

## 🔹 Definition
NPM stands for:

# 👉 Node Package Manager

It is the default package manager for Node.js.

NPM helps developers:

* Install packages/libraries
* Manage dependencies
* Run scripts
* Share reusable code

---

# 📌 Simple Meaning

Instead of writing everything from scratch, developers install ready-made packages.

Example:

```bash id="1y8v5p"
npm install react
```

This installs React into the project.

---

# 📌 Why NPM is Important?

Modern applications need many libraries like:

* React
* Axios
* Redux
* Express
* Tailwind

NPM manages all of them.

---

# 📌 Main Uses of NPM

| Purpose          | Example               |
| ---------------- | --------------------- |
| Install packages | `npm install react`   |
| Remove packages  | `npm uninstall react` |
| Update packages  | `npm update`          |
| Run scripts      | `npm run start`       |

---

# 📌 What is package.json?

## 🔹 Definition

`package.json` is the main configuration file of a Node.js/React project.

It stores:

* Project information
* Dependencies
* Scripts
* Versions
* Metadata

---

# 📌 Example package.json

```json id="6wjlwm"
{
  "name": "my-app",
  "version": "1.0.0",
  "scripts": {
    "start": "react-scripts start"
  },
  "dependencies": {
    "react": "^18.0.0"
  }
}
```

---

# 📌 Why package.json is Important?

Without `package.json`:

❌ Difficult to manage dependencies
❌ Difficult to share project
❌ No script management

---

# 📌 Important Fields in package.json

| Field           | Purpose              |
| --------------- | -------------------- |
| name            | Project name         |
| version         | Project version      |
| scripts         | Custom commands      |
| dependencies    | Production packages  |
| devDependencies | Development packages |

---

# 🎯 Interview Answer

## ❓ What is package.json?

### ✅ Answer:

`package.json` is the configuration file in Node.js and React projects that stores project metadata, dependencies, scripts, and package information.

---

---

# 📘 Dependencies vs devDependencies

---

# 📌 What are Dependencies?

Dependencies are packages required for:

# 👉 Running the application in production.

These packages are needed after deployment.

---

# 🔥 Examples

* react
* react-dom
* axios
* redux

---

# 📌 Example

```bash id="n9g2x7"
npm install axios
```

Stored inside:

```json id="q2jlwm"
"dependencies": {
  "axios": "^1.0.0"
}
```

---

# 📌 What are devDependencies?

devDependencies are packages needed only during development.

They are NOT required in production.

---

# 🔥 Examples

* webpack
* babel
* eslint
* jest
* vite

---

# 📌 Example

```bash id="jlwmz7"
npm install webpack --save-dev
```

Stored inside:

```json id="ozw5la"
"devDependencies": {
  "webpack": "^5.0.0"
}
```

---

# 📌 Difference Between Dependencies and devDependencies

| Feature                        | dependencies | devDependencies |
| ------------------------------ | ------------ | --------------- |
| Needed in Production           | ✅ Yes        | ❌ No            |
| Needed During Development      | ✅ Yes        | ✅ Yes           |
| Example                        | React, Axios | Webpack, Babel  |
| Installed on Production Server | ✅ Yes        | ❌ Usually No    |

---

# 🎯 Interview Answer

## ❓ Difference Between dependencies and devDependencies?

### ✅ Answer:

Dependencies are packages required to run the application in production, while devDependencies are packages needed only during development such as testing tools, bundlers, and compilers.

---

---

# 📘 Scripts in package.json

---

# 📌 What are Scripts?

Scripts are custom commands defined inside `package.json`.

They help automate tasks.

---

# 📌 Example

```json id="xjlwm8"
"scripts": {
  "start": "react-scripts start",
  "build": "react-scripts build",
  "test": "react-scripts test"
}
```

---

# 📌 Running Scripts

```bash id="9d3jlwm"
npm run build
```

or

```bash id="jlwm0c"
npm start
```

---

# 📌 Common Scripts

| Script | Purpose                 |
| ------ | ----------------------- |
| start  | Run development server  |
| build  | Create production build |
| test   | Run tests               |
| dev    | Start development mode  |

---

# 📌 Why Scripts are Useful?

✅ Automation
✅ Easier commands
✅ Better project management

---

# 🎯 Interview Answer

## ❓ What are scripts in package.json?

### ✅ Answer:

Scripts are custom commands defined inside package.json used to automate tasks like starting the server, building the project, and running tests.

---

---

# 📘 npm vs npx

---

# 📌 What is npm?

npm installs packages permanently into project.

---

# 📌 Example

```bash id="5o3jlwm"
npm install create-react-app
```

Package gets installed.

---

# 📌 What is npx?

npx executes packages directly without permanently installing them globally.

---

# 📌 Example

```bash id="z2k9pd"
npx create-react-app my-app
```

Runs package temporarily.

---

# 📌 Difference Between npm and npx

| Feature               | npm              | npx              |
| --------------------- | ---------------- | ---------------- |
| Purpose               | Install packages | Execute packages |
| Permanent Install     | ✅ Yes            | ❌ No             |
| Global Install Needed | Sometimes        | ❌ No             |
| Saves Storage         | ❌ No             | ✅ Yes            |

---

# 🎯 Interview Answer

## ❓ Difference Between npm and npx?

### ✅ Answer:

npm is used to install and manage packages, while npx is used to execute packages directly without installing them globally.

---

---

# 📘 JS vs JSX

---

# 📌 What is JS?

JS stands for:

# 👉 JavaScript

It is a programming language used to create dynamic web applications.

---

# 📌 Example

```js id="jlwmv0"
const name = "Krupa";

console.log(name);
```

---

# 📌 What is JSX?

JSX stands for:

# 👉 JavaScript XML

It allows writing HTML-like syntax inside JavaScript.

Used mainly in React.

---

# 📌 Example

```jsx id="jlwmn3"
const element = <h1>Hello</h1>;
```

---

# 📌 Why JSX is Used?

Without JSX:

```js id="jlwm6f"
React.createElement(
  "h1",
  null,
  "Hello"
);
```

With JSX:

```jsx id="jlwmu9"
<h1>Hello</h1>
```

Much cleaner and easier.

---

# 📌 JSX Rules

---

# ✅ Must Return Single Parent

```jsx id="9mjlwm"
return (
  <div>
    <h1>Hello</h1>
  </div>
);
```

---

# ✅ Use className Instead of class

```jsx id="jlwmgf"
<div className="box"></div>
```

---

# ✅ JavaScript Inside {}

```jsx id="jlwmf5"
<h1>{name}</h1>
```

---

# 📌 JS vs JSX Difference

| Feature                      | JS         | JSX            |
| ---------------------------- | ---------- | -------------- |
| Full Form                    | JavaScript | JavaScript XML |
| Used For                     | Logic      | UI             |
| HTML Support                 | ❌ No       | ✅ Yes          |
| Browser Understands Directly | ✅ Yes      | ❌ No           |
| Needs Babel                  | ❌ No       | ✅ Yes          |

---

# 🎯 Interview Answer

## ❓ What is JSX?

### ✅ Answer:

JSX is a syntax extension for JavaScript used in React that allows developers to write HTML-like code inside JavaScript. Babel converts JSX into regular JavaScript.

---

---

# 📘 React Fragment

---

# 📌 What is Fragment?

Fragment allows grouping multiple elements without adding extra DOM nodes.

---

# ❌ Without Fragment

```jsx id="jlwm3v"
return (
  <div>
    <h1>Hello</h1>
    <p>Welcome</p>
  </div>
);
```

Extra `<div>` added to DOM.

---

# ✅ With Fragment

```jsx id="jlwmga"
return (
  <>
    <h1>Hello</h1>
    <p>Welcome</p>
  </>
);
```

No extra DOM element created.

---

# 📌 Another Syntax

```jsx id="jlwmk8"
import React from "react";

return (
  <React.Fragment>
    <h1>Hello</h1>
  </React.Fragment>
);
```

---

# 📌 Why Fragment is Important?

✅ Cleaner DOM
✅ Better performance
✅ Avoid unnecessary wrapper divs

---

# 📌 Real DOM Output

---

## Without Fragment

```html id="0jlwmx"
<div>
  <h1>Hello</h1>
  <p>Welcome</p>
</div>
```

---

## With Fragment

```html id="jlwm87"
<h1>Hello</h1>
<p>Welcome</p>
```

---

# 🎯 Interview Answer

## ❓ What is React Fragment?

### ✅ Answer:

React Fragment is used to group multiple elements without adding extra nodes to the DOM. It helps keep the DOM cleaner and improves performance.


# 📘 package-lock.json — Interview Notes

---

# 📌 What is package-lock.json?

`package-lock.json` is an automatically generated file created by **npm** when installing packages.

It stores the **exact version** of all installed dependencies and sub-dependencies.

---

# 📌 Why is it Needed?

It ensures that:

✅ Same package versions are installed for every developer
✅ Project works consistently on all machines
✅ No version mismatch issues

---

# 📌 Example

Suppose in `package.json`:

```json id="jlwmc7"
"axios": "^1.0.0"
```

`^` means npm can install newer minor versions.

But `package-lock.json` locks the exact version like:

```json id="jlwm84"
"axios": "1.0.2"
```

---

# 📌 Difference Between package.json and package-lock.json

| package.json         | package-lock.json             |
| -------------------- | ----------------------------- |
| Stores package names | Stores exact package versions |
| Developer editable   | Auto-generated                |
| Flexible versions    | Locked versions               |
| Main project config  | Dependency snapshot           |

---

# 📌 Important Interview Point

When another developer runs:

```bash id="jlwmx1"
npm install
```

npm reads `package-lock.json` and installs the exact same versions.

---

# 🎯 Interview Answer

## ❓ What is package-lock.json?

### ✅ Answer:

`package-lock.json` is an automatically generated npm file that stores the exact versions of installed dependencies and sub-dependencies to ensure consistent installations across all environments.

---
