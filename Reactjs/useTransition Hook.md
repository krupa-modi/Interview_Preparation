# 📌 What is useTransition?

`useTransition` React ka ek hook hai jo UI ko smooth aur responsive banane ke liye use hota hai.

Ye heavy state updates ko **low priority** bana deta hai taaki important UI updates fast render ho sake.

useTransition heavy updates ko background me chalata hai taaki UI slow na ho.

---

# 📌 Syntax

```jsx id="jlwm5u"
const [isPending, startTransition] =
  useTransition();
```

---

# 📌 useTransition Kyu Use Karte Hai?

Jab koi heavy rendering ya large data filtering hoti hai tab UI slow ho sakta hai.

`useTransition` important updates ko fast rakhta hai aur heavy updates ko background me process karta hai.

---

# 📌 Example Situation

Suppose:

* User search input me typing kar raha hai
* Neeche 10,000 items filter ho rahe hain

Without `useTransition`:

❌ Typing lag ho sakti hai

With `useTransition`:

✅ Input smooth rahega

---

# 📌 Example

```jsx id="jlwm1p"
import {useState,useTransition} from "react";

function App() {
  const [input, setInput] = useState("");

  const [list, setList] = useState([]);

  const [isPending, startTransition] =useTransition();

  const handleChange = (e) => {
    setInput(e.target.value);

    startTransition(() => {
      const items = [];

      for (let i = 0; i < 10000; i++) {
        items.push(e.target.value);
      }

      setList(items);
    });
  };

  return (
    <div>
      <input
        value={input}
        onChange={handleChange}
      />

      {isPending && <h2>Loading...</h2>}

      {list.map((item, index) => (
        <p key={index}>{item}</p>
      ))}
    </div>
  );
}

export default App;


*********************************************************OR**************************************************************

import React, {
  useState,
  useTransition
} from "react";

function App() {
  const [message, setMessage] =useState("");

  const [isPending, startTransition] = useTransition();

  const handleClick = () => {
    startTransition(() => {
      setMessage("Data Loaded");
    });
  };

  return (
    <div>
      <button
        onClick={handleClick}
        disabled={isPending}
      >
        {isPending
          ? "Loading..."
          : "Click Me"}
      </button>

      <h2>{message}</h2>
    </div>
  );
}

export default App;
```

---

# 📌 Important Terms

---

# 🔥 isPending

```jsx id="jlwm7x"
isPending
```

Batata hai transition chal raha hai ya nahi.

---

# 🔥 startTransition

```jsx id="jlwm3v"
startTransition(() => {})
```

Heavy/non-urgent updates ko low priority me run karta hai.

---

# 📌 Benefits of useTransition

✅ Smooth UI
✅ Better performance
✅ Prevents UI lag
✅ Better user experience

---

# 📌 Real Use Cases

| Use Case            | Reason                |
| ------------------- | --------------------- |
| Search Filtering    | Large data rendering  |
| Heavy UI Updates    | Smooth interaction    |
| Large Lists         | Prevent lag           |
| Expensive Rendering | Better responsiveness |

---

# 📌 Interview Important Point

`useTransition` urgent updates aur non-urgent updates ko separate karta hai.

---

# 🎯 Interview Answers

---

# ❓ What is useTransition?

### ✅ Answer:

`useTransition` React hook hai jo heavy state updates ko low priority bana kar UI ko responsive aur smooth banata hai.

---

# ❓ Why use useTransition?

### ✅ Answer:

`useTransition` performance improve karne aur UI lag avoid karne ke liye use hota hai, especially large rendering ya filtering me.

---

# ❓ What does isPending do?

### ✅ Answer:

`isPending` batata hai ki transition currently chal raha hai ya nahi.

---

# 📌 Important Interview Keywords

* useTransition
* startTransition
* isPending
* Concurrent Rendering
* Low Priority Updates
* Performance Optimization
* Smooth UI
* Non-Urgent Updates
