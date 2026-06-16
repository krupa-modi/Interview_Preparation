## 🔹 React Fiber kya hai?

**React Fiber** React ka **new reconciliation engine** hai  
jo React 16 se introduce hua.

👉 Simple words:
> Fiber React ka internal system hai jo rendering ko **fast, smooth aur interruptible** banata hai.

---
## 🔹 Fiber ki zarurat kyun padi?

Old React (Stack Reconciler) me problem thi:

❌ Rendering ek hi baar me hoti thi  
❌ Beech me pause nahi kar sakte the  
❌ UI block ho jata tha (jank)

👉 Fiber ne is problem ko solve kiya.

---

## 🔹 React Fiber kya improve karta hai?

- Rendering ko small chunks me tod deta hai
- High priority updates pehle karta hai
- Rendering ko pause / resume kar sakta hai
- Smooth UI (better UX)

---

## 🔹 Fiber vs Old Reconciler

| Feature | Old React | React Fiber |
|------|----------|------------|
| Rendering | Sync | Async |
| Pause / Resume | ❌ | ✅ |
| Priority based | ❌ | ✅ |
| Smooth UI | ❌ | ✅ |

---

## 🔹 Fiber ka main concept – "Units of Work"

Fiber rendering ko **chote-chote parts** me tod deta hai  
👉 inhe bolte hain **Units of Work**

Browser jab free hota hai tab React kaam karta hai  
( `requestIdleCallback` concept )

---

## 🔹 Fiber Node kya hota hai?

Har React element ke liye ek **Fiber Node** hota hai

👉 Fiber Node me hota hai:
- type (component type)
- props
- state
- child, sibling, parent reference

---

## 🔹 Reconciliation kya hota hai?

> Purane Virtual DOM aur naye Virtual DOM ko compare karna = Reconciliation

Fiber reconciliation ko **interruptible** bana deta hai.

---

## 🔹 Fiber & Priority (Very Important)

Fiber updates ko priority deta hai:

- User input (click, typing) → High priority
- API data → Low priority

👉 Isse UI responsive rehti hai

---

## 🔹 Fiber se kaunse features possible hue?

- Concurrent Mode
- Suspense
- Time slicing
- Transitions

👉 Ye sab Fiber ke bina possible nahi the

---

## 🔹 Kya developers directly Fiber use karte hain?

❌ Nahi  
Fiber React ka **internal implementation** hai

👉 Developer sirf features use karta hai:
- `Suspense`
- `startTransition`

---

## 🔹 Interview One-Line Answer

> React Fiber React ka reconciliation engine hai jo rendering ko asynchronous, interruptible aur priority-based banata hai.

---

## 🔥 Interview Q&A

### ❓ React Fiber React ka feature hai?
❌ Nahi  
👉 Ye React ka **internal architecture** hai

---

### ❓ Fiber kis version me aaya?
👉 React 16

---

### ❓ Fiber ka main benefit?
👉 Smooth UI + better performance

---

## 🧠 Easy Example (Real Life)

Socho tum ek bada kaam kar rahe ho  
👉 Agar urgent phone aa jaye to tum kaam pause karke phone utha lete ho  

👉 React Fiber bhi rendering ke saath ye hi karta hai 😄

---

## ✅ Short Interview Answer (2 Lines)

> React Fiber React ka internal rendering engine hai jo UI updates ko interrupt, prioritize aur efficiently render karta hai, jisse performance aur user experience improve hota hai.

---

## 🔥 Interview Tip

👉 "Asynchronous rendering" bolna  
👉 "Interruptible reconciliation" mention karna  
👉 "Priority based updates" add karna