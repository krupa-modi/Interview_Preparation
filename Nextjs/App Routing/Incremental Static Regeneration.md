# 2. What is ISR?

ISR means:(Incremental Static Regeneration)
👉 Static pages can update automatically after deployment.

Uses:

```js
revalidate
```

---

# 🔍 Example

```js
export async function getStaticProps() {
  return {
    props: {},
    revalidate: 10,
  };
}
```

👉 Page regenerates every:

```text
10 seconds
```

---

# 🔥 Flow of ISR

```text
Static Page Generated
      ↓
User Requests Page
      ↓
After Revalidate Time
      ↓
Page Regenerated in Background
```

---

# 🔥 Advantages

* Fast like SSG ⚡
* Fresh data like SSR ✅
* No full rebuild needed ✅

---

# ❌ Disadvantages

* Slightly complex
* Old data may show briefly

---

# 🔥 Best Use Cases

| Use Case      | Why ISR          |
| ------------- | ---------------- |
| News websites | Frequent updates |
| E-commerce    | Product updates  |
| Blogs         | Dynamic content  |

---