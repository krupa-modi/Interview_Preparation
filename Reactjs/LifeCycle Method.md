
Here’s a **clean, interview-ready Markdown file** for React Lifecycle Methods 👇

---

# ⚛️ React Lifecycle Methods (Complete Guide for Interview)

## 📌 What are Lifecycle Methods?

**Lifecycle Methods** are special methods in React (class components) that get called at different stages of a component’s life.

👉 A component in React goes through **3 main phases:**

1. **Mounting** (component create & DOM me add hota hai)
2. **Updating** (state/props change hone par re-render)
3. **Unmounting** (component remove hota hai DOM se)

---

# 🔄 React Component Lifecycle Phases

---

## 🟢 1. Mounting Phase

👉 Jab component first time render hota hai

### Methods:

### 1️⃣ constructor()

* Component ka initial setup
* State initialize karte hai

```js
constructor(props) {
  super(props);
  this.state = { count: 0 };
}
```

---

### 2️⃣ static getDerivedStateFromProps()

* Props change hone par state update kar sakte hai
* Rarely used

```js
static getDerivedStateFromProps(props, state) {
  return null;
}
```

---

### 3️⃣ render() ⭐ (Important)

* UI return karta hai
* Required method

```js
render() {
  return <h1>Hello</h1>;
}
```

---

### 4️⃣ componentDidMount() ⭐ (Very Important)

* Component DOM me add hone ke baad call hota hai
* API calls, side-effects yahi karte hai

```js
componentDidMount() {
  console.log("Component Mounted");
}
```

👉 **Interview Point:**
✔ API calls
✔ Event listeners
✔ setTimeout

---

## 🔵 2. Updating Phase

👉 Jab **state ya props change hote hai**

### Methods:

### 1️⃣ static getDerivedStateFromProps()

* Same as mounting

---

### 2️⃣ shouldComponentUpdate() ⭐

* Decide karta hai re-render hona chahiye ya nahi
* Performance optimization ke liye

```js
shouldComponentUpdate(nextProps, nextState) {
  return true;
}
```

👉 Agar `false` return kare → re-render nahi hoga

---

### 3️⃣ render()

* UI update hota hai

---

### 4️⃣ getSnapshotBeforeUpdate()

* DOM update hone se pehle call hota hai

```js
getSnapshotBeforeUpdate(prevProps, prevState) {
  return null;
}
```

---

### 5️⃣ componentDidUpdate() ⭐

* Update hone ke baad call hota hai

```js
componentDidUpdate(prevProps, prevState) {
  console.log("Component Updated");
}
```

👉 Use cases:

* API call on update
* DOM operations

---

## 🔴 3. Unmounting Phase

👉 Jab component DOM se remove hota hai

### Method:

### 1️⃣ componentWillUnmount() ⭐

* Cleanup ke liye use hota hai

```js
componentWillUnmount() {
  console.log("Component Unmounted");
}
```

👉 Use cases:

* Event listeners remove
* Timers clear
* Memory leaks avoid

---

# ⚡ Lifecycle Flow Diagram (Simple Understanding)

```
Mounting:
constructor → render → componentDidMount

Updating:
getDerivedStateFromProps → shouldComponentUpdate → render → getSnapshotBeforeUpdate → componentDidUpdate

Unmounting:
componentWillUnmount
```

---

# 🔥 Important Interview Questions

## ❓ 1. Which lifecycle method is used for API calls?

👉 `componentDidMount()`

---

## ❓ 2. How to optimize performance?

👉 `shouldComponentUpdate()`

---

## ❓ 3. Cleanup kaha karte hai?

👉 `componentWillUnmount()`

---

## ❓ 4. Render method ka role kya hai?

👉 UI return karta hai

---

# ⚠️ Important Notes

* Lifecycle methods **only class components me hote hai**
* Functional components me same kaam:
  👉 `useEffect()` hook karta hai

---

# ⚛️ Functional Component Equivalent (Hook)

```js
useEffect(() => {
  console.log("Mounted");

  return () => {
    console.log("Unmounted");
  };
}, []);
```

---

# 💡 Pro Tips for Interview

✔ `componentDidMount` = API calls
✔ `componentDidUpdate` = updates handle
✔ `componentWillUnmount` = cleanup
✔ `shouldComponentUpdate` = performance

---

# 🎯 Final Summary

👉 Lifecycle methods = component ke life ke stages
👉 3 phases: Mounting, Updating, Unmounting
👉 Most important methods:

* componentDidMount
* componentDidUpdate
* componentWillUnmount
* shouldComponentUpdate


Agar tu chahe to next step me main tujhe **class lifecycle vs useEffect mapping**, ya **diagram + tricky interview questions** bhi de sakta hu — wo aur zyada helpful rahega 🔥
