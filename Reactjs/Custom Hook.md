
## 1. What are Custom Hooks?

Custom Hooks are **JavaScript functions** that start with `use` and allow you to **reuse stateful logic** across multiple components.

👉 They internally use React Hooks like:

* `useState`
* `useEffect`
* `useRef`
* etc.

**Example:**

```js
function useCounter() {
  const [count, setCount] = React.useState(0);

  const increment = () => setCount(count + 1);

  return { count, increment };
}
```

---

## 2. Why are Custom Hooks Needed?

👉 Without custom hooks:

* Code duplication ❌
* Hard to maintain ❌
* Logic scattered ❌

👉 With custom hooks:

* Reusable logic ✅
* Clean code ✅
* Better separation of concerns ✅

---

## 3. Real Problem Without Custom Hook

### ❌ Duplicate Logic in Multiple Components

```js
function ComponentA() {
  const [data, setData] = React.useState(null);

  React.useEffect(() => {
    fetch('/api/data').then(res => res.json()).then(setData);
  }, []);

  return <div>{data}</div>;
}

function ComponentB() {
  const [data, setData] = React.useState(null);

  React.useEffect(() => {
    fetch('/api/data').then(res => res.json()).then(setData);
  }, []);

  return <div>{data}</div>;
}
```

👉 Same logic repeated → bad practice

---

## 4. Solution Using Custom Hook

### ✅ Create Custom Hook

```js
function useFetch(url) {
  const [data, setData] = React.useState(null);
  const [loading, setLoading] = React.useState(true);

  React.useEffect(() => {
    fetch(url)
      .then(res => res.json())
      .then(result => {
        setData(result);
        setLoading(false);
      });
  }, [url]);

  return { data, loading };
}
```

---

### ✅ Use in Components

```js
function ComponentA() {
  const { data, loading } = useFetch('/api/data');

  if (loading) return <p>Loading...</p>;
  return <div>{data}</div>;
}

function ComponentB() {
  const { data } = useFetch('/api/data');
  return <div>{data}</div>;
}
```

👉 Clean + reusable + scalable

---

## 5. Rules of Custom Hooks

* Must start with `use` (e.g., `useAuth`, `useFetch`)
* Only call hooks at the top level
* Can call other hooks inside

---

## 6. Another Real Example (useLocalStorage)

```js
function useLocalStorage(key, initialValue) {
  const [value, setValue] = React.useState(() => {
    const stored = localStorage.getItem(key);
    return stored ? JSON.parse(stored) : initialValue;
  });

  React.useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [key, value]);

  return [value, setValue];
}
```

### Usage:

```js
const [name, setName] = useLocalStorage('name', '');
```

---

## 7. Benefits of Custom Hooks

* 🔁 Reusability
* 🧹 Cleaner components
* 🧠 Better logic separation
* 📈 Scalability in large apps
* 🧪 Easy testing

---

## 8. When to Create Custom Hooks?

👉 Create when:

* Logic is reused in multiple components
* Component becomes too large
* You want better abstraction

---

## 🎯 Final Interview Answer (Short)

👉 Custom Hooks are reusable functions that encapsulate React logic using built-in hooks.
👉 They help reduce duplication, improve readability, and make code scalable.

---

In interviews, always give a **real example (like useFetch or useLocalStorage)** — it shows practical knowledge.

