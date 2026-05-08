## Diffing Algorithm, Reconciliation, Fiber, createRoot

# 1. Diffing Algorithm

## What is Diffing Algorithm?

React DOM ko directly har baar update nahi karta.
Jab state ya props change hote hain, React old Virtual DOM aur new Virtual DOM ko compare karta hai.

Is compare process ko **Diffing Algorithm** bolte hain.

---

## Why React uses Diffing?

Agar React pura DOM reload kare har update pe:

* Performance slow ho jayegi
* Browser rendering expensive hoti hai

Isliye React sirf changed part ko update karta hai.

---

## Simple Flow

```txt
State Change
   ↓
New Virtual DOM Create
   ↓
Old vs New Compare
   ↓
Only Changed Part Update
```

---

## React Diffing Rules

### 1. Different Element Type → Full Replace

```jsx
<div>Hello</div>
```

changed to

```jsx
<span>Hello</span>
```

React pura element replace karega.

---

### 2. Same Element Type → Only Update Changed Props

```jsx
<input value="A" />
```

changed to

```jsx
<input value="B" />
```

Sirf value update hogi.

---

### 3. List Elements → Keys Important

```jsx
{users.map(user => (
  <li key={user.id}>{user.name}</li>
))}
```

`key` React ko batata hai kaunsa item change hua.

---

## Why key is Important?

Without key:

* unnecessary re-render
* wrong UI updates
* performance issue

---
---

## Common Interview Questions

### Q1. What is Diffing in React?

React old Virtual DOM aur new Virtual DOM compare karta hai aur sirf changed parts ko real DOM me update karta hai.

---

### Q2. Why keys are important?

Keys uniquely identify list items so React efficiently update/reorder/delete kar sake.

---

### Q3. Does React compare full DOM?

No. React Virtual DOM compare karta hai.

---

---

# 2. Reconciliation

## What is Reconciliation?

React ka process jisme:

```txt
Old Virtual DOM
      vs
New Virtual DOM
```

compare hota hai aur UI update decide hoti hai.

Ye complete process:

* compare
* diffing
* update

sab milke Reconciliation kehlata hai.

---

## Reconciliation Process

```txt
State/Props Change
        ↓
Render Phase
        ↓
New Virtual DOM
        ↓
Diffing
        ↓
Update Real DOM
```

---

## Important Point

Reconciliation ek process hai.

Diffing us process ka part hai.

---

## Example

```jsx
function App() {
  const [count, setCount] = useState(0);

  return <h1>{count}</h1>;
}
```

Jab count change hota hai:

* New Virtual DOM banta hai
* React compare karta hai
* Sirf text update hota hai

---

## Interview Questions

### Q1. What is Reconciliation?

React process of comparing old and new Virtual DOM and updating only changed UI efficiently.

---

### Q2. Difference between Diffing and Reconciliation?

| Diffing              | Reconciliation          |
| -------------------- | ----------------------- |
| Comparison algorithm | Complete update process |
| Old vs New compare   | Compare + Update        |

---

---

# 3. React Fiber

# React Fiber (Proper Interview Explanation)

---

# What Exactly is Fiber?

Fiber React ka **new rendering engine** hai.

Simple words me:

```txt id="rt1"
Fiber decides:
Kaunsa component kab render hoga
Kaunsi update important hai
Aur UI ko smooth kaise rakhna hai
```

React 16 se pehle old reconciliation system tha.
React 16 ke baad React Fiber introduce hua.

---

# Real Problem Before Fiber

Old React rendering:

```txt id="old1"
Synchronous Rendering
```

Matlab:

Agar rendering start hui to browser ko wait karna padta tha jab tak pura UI render na ho jaye.

---

## Example Problem

Suppose:

* Large dashboard hai
* 1000 components render ho rahe hai
* User button click karta hai

Old React:

```txt id="old2"
Pehle pura rendering complete hogi
Fir click handle hoga
```

Result:

* UI lag
* scrolling freeze
* typing delay

---

# Fiber Kya Karta Hai?

Fiber rendering ko small pieces me tod deta hai.

```txt id="fiber1"
Big Task
   ↓
Small Units
   ↓
Step by Step Processing
```

Isse React:

* pause kar sakta hai
* resume kar sakta hai
* important task pehle kar sakta hai

---

# Easy Real Life Example

Suppose tum room clean kar rahe ho.

## Old React

```txt id="room1"
Pure room ko ek hi baar me clean karo
Beech me koi kaam nahi
```

Agar mummy bula le:

```txt id="room2"
Wait karo 😅
```

---

## Fiber

```txt id="room3"
Thoda clean karo
Pause karo
Important kaam karo
Fir continue karo
```

Yahi Fiber ka concept hai.

---

# Main Goal of Fiber

## 1. Smooth UI

UI freeze nahi hota.

---

## 2. Priority Based Updates

Important updates pehle.

Example:

### High Priority

```txt id="high1"
Typing
Button click
Animation
```

### Low Priority

```txt id="low1"
API data rendering
Background rendering
```

---

# Fiber Internally

React har component ke liye ek:

```txt id="fiberNode"
Fiber Node
```

banata hai.

Ye Fiber node ek JavaScript object hota hai.

Isme information hoti hai:

* component type
* state
* props
* parent
* child
* sibling

---

# Fiber Tree

```txt id="tree1"
App
 ├── Header
 ├── Sidebar
 └── Content
      ├── Card1
      ├── Card2
      └── Card3
```

Har component ka ek Fiber node hota hai.

Together:

```txt id="tree2"
Fiber Tree
```

ban jata hai.

---

# Important Feature: Interruptible Rendering

Old React:

```txt id="sync1"
Cannot stop rendering
```

Fiber:

```txt id="sync2"
Can pause rendering
Can continue later
```

Ye React ka biggest improvement tha.

---

# Fiber and Concurrent Rendering

Fiber hi Concurrent Rendering possible banata hai.

Matlab:

React multiple tasks intelligently manage karta hai.

---

# Render Phase vs Commit Phase

## 1. Render Phase

Fiber calculate karta hai:

```txt id="render1"
Kya update karna hai?
```

Pause ho sakta hai.

---

## 2. Commit Phase

Actual DOM update hota hai.

```txt id="commit1"
Real DOM update
```

Ye fast hota hai.

---

# Most Important Interview Line

```txt id="imp1"
Fiber is React's reconciliation engine that breaks rendering work into small units so React can pause, prioritize, and resume rendering efficiently.
```

---

# Common Interview Questions

## Q1. What is React Fiber?

React Fiber is the new reconciliation engine introduced in React 16 for incremental and priority-based rendering.

---

## Q2. Why Fiber was introduced?

To solve:

* UI blocking
* slow rendering
* lack of priority handling

---

## Q3. What is Fiber Node?

Fiber node ek JavaScript object hota hai jo component ki information store karta hai.

---

## Q4. Difference Between Old React and Fiber?

| Old React      | Fiber                 |
| -------------- | --------------------- |
| Synchronous    | Interruptible         |
| No priorities  | Priority based        |
| UI blocking    | Smooth rendering      |
| Full rendering | Incremental rendering |

---

# One Line Revision

```txt id="last1"
Fiber = React ka smart rendering engine
jo rendering ko small tasks me break karta hai
taaki UI smooth aur fast rahe.
```

# 4. createRoot

## What is createRoot?

React 18 me new root API introduce hui.

Old way:

```jsx
ReactDOM.render(<App />, root);
```

New way:

```jsx
import { createRoot } from "react-dom/client";

const root = createRoot(document.getElementById("root"));

root.render(<App />);
```

---

## Why createRoot Introduced?

Ye React 18 ke new features enable karta hai:

* Concurrent Rendering
* Automatic Batching
* Better Performance

---

## Difference

| ReactDOM.render        | createRoot                  |
| ---------------------- | --------------------------- |
| Old API                | New API                     |
| React 17               | React 18                    |
| No concurrent features | Concurrent features enabled |

---

## Interview Important Point

Without `createRoot`, React 18 ke advanced features fully work nahi karte.

---

## Common Interview Questions

### Q1. What is createRoot?

New React 18 API used to create root container and enable concurrent rendering features.

---

### Q2. Difference between render and createRoot?

`createRoot` React 18 concurrent features support karta hai.

---

### Q3. Which package provides createRoot?

```jsx
react-dom/client
```

---

# Quick Revision

| Topic          | Main Purpose                |
| -------------- | --------------------------- |
| Diffing        | Compare old/new Virtual DOM |
| Reconciliation | Full update process         |
| Fiber          | New rendering engine        |
| createRoot     | React 18 root API           |

---

# Most Important Interview One-Liners

### Diffing

React efficiently compares Virtual DOM trees.

---

### Reconciliation

Process of updating UI after state/props changes.

---

### Fiber

React’s modern rendering engine for async and priority rendering.

---

### createRoot

React 18 API enabling concurrent features.
