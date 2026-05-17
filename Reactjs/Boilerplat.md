## 📌 What is Boilerplate?

Boilerplate matlab:

> “Repeated basic code template jo har project me baar baar likhna padta hai.”

---

# 🧠 Easy Definition (Interview)

> “Boilerplate is a reusable starter/template code that helps developers quickly start development without writing common setup code again and again.”

---

# 📌 Example Without Boilerplate

Har baar manually:

* API setup
* Imports
* Error handling
* Headers
* Configurations

likhna padega.

---

# 🔥 API Boilerplate Example

```js id="2fmfsf"
async function fetchData(url) {
  try {
    const response = await fetch(url, {
      method: "GET",

      headers: {
        "Content-Type":
          "application/json",
      },
    });

    if (!response.ok) {
      throw new Error("API Error");
    }

    const data = await response.json();

    return data;
  } catch (error) {
    console.log(error);
  }
}
```

---

# 📌 Why Boilerplate Important?

## ✅ Benefits

* Time save
* Reusable
* Clean structure
* Faster development
* Consistent code

---

# 🔥 React Boilerplate Example

```js id="0jdn4o"
import React, { useState } from "react";

function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
    </div>
  );
}

export default App;
```

---

# 📌 Common Boilerplates

| Boilerplate         | Use              |
| ------------------- | ---------------- |
| React Boilerplate   | React app setup  |
| API Boilerplate     | API calls        |
| Express Boilerplate | Backend setup    |
| Redux Boilerplate   | State management |

---

# 🔥 Interview Question

# ❓ Why boilerplate code is used?

> “Boilerplate code reusable hota hai aur repetitive setup code ko avoid karta hai.”

---

# 📌 Real Life Example

Jaise resume ka template baar baar use karte ho.

Waise hi coding me common setup/template ko boilerplate bolte hain.

---

# 🎯 Final Interview Answer

> “Boilerplate is a predefined reusable template code used to reduce repetitive coding and speed up development.”
