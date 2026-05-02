
# 🧠 1. What is Catch-all Routing?

Catch-all routes allow you to match **multiple URL segments** using a single dynamic route.

👉 Instead of `[id]`, you use:

```
[...slug]
```

---

# 🧱 2. Catch-all Route `[...slug]`

## 📁 Folder Structure:

```
app/
 └── docs/
      └── [...slug]/
           └── page.tsx
```

---

## ⚡ How It Works

This route matches:

```
/docs/a
/docs/a/b
/docs/a/b/c
```

👉 It captures all segments into an **array**

---

## ✅ Example:

```tsx
// app/docs/[...slug]/page.tsx

export default function DocsPage({ params }: { params: { slug: string[] } }) {
  return (
    <div>
      <h1>Docs Page</h1>
      <p>Path: {params.slug.join(" / ")}</p>
    </div>
  );
}
```

---

## 🔍 Output Examples:

```
/docs/react        → ["react"]
/docs/react/hooks  → ["react", "hooks"]
/docs/a/b/c        → ["a", "b", "c"]
```

---

## ⚠️ Important Rule

❌ `/docs` → **Will NOT match**

👉 Because at least **one segment is required**

---

# 🧠 3. Optional Catch-all Route `[[...slug]]`

This is a **more flexible version** of catch-all.

👉 Syntax:

```
[[...slug]]
```

---

## 📁 Folder Structure:

```
app/
 └── docs/
      └── [[...slug]]/
           └── page.tsx
```

---

## ⚡ How It Works

This route matches:

```
/docs
/docs/a
/docs/a/b
/docs/a/b/c
```

---

## ✅ Example:

```tsx
// app/docs/[[...slug]]/page.tsx

export default function DocsPage({ params }: { params: { slug?: string[] } }) {
  return (
    <div>
      <h1>Docs Page</h1>
      <p>
        Path: {params.slug ? params.slug.join(" / ") : "Home"}
      </p>
    </div>
  );
}
```

---

## 🔍 Output Examples:

```
/docs           → undefined
/docs/react     → ["react"]
/docs/a/b       → ["a", "b"]
```

---

## ⚠️ Important Behavior

✔ `slug` can be **undefined**
✔ You must handle this case in your code

---

# 🔥 4. Key Differences (Catch-all vs Optional Catch-all)

| Feature           | `[...slug]` (Catch-all) | `[[...slug]]` (Optional Catch-all) |
| ----------------- | ----------------------- | ---------------------------------- |
| Matches `/docs`   | ❌ No                    | ✅ Yes                              |
| Matches `/docs/a` | ✅ Yes                   | ✅ Yes                              |
| Param Type        | `string[]`              | `string[] \| undefined`            |
| Required Segments | At least 1              | 0 or more                          |
| Flexibility       | Less flexible           | More flexible                      |

---

# ⚡ 5. Visual Understanding

## `[...slug]`

```
/docs/a/b → ["a", "b"]
/docs     → ❌ Not matched
```

---

## `[[...slug]]`

```
/docs     → undefined
/docs/a   → ["a"]
```

---

# 🎯 6. When to Use What?

## ✅ Use `[...slug]` when:

* You **always expect path segments**
* Example:

  * Blog categories
  * Nested docs pages

---

## ✅ Use `[[...slug]]` when:

* You want a **default root page + nested pages**
* Example:

  * `/docs` → main docs page
  * `/docs/react` → sub page

---

# 💡 7. Real-World Example

### Docs Website

```
/docs                → Main Docs Page
/docs/react          → React Docs
/docs/react/hooks    → Hooks Docs
```

👉 Best choice:

```
[[...slug]]
```

---

# 🧠 Interview Summary (Must Remember)

* `[...slug]` → Requires at least one segment
* `[[...slug]]` → Allows zero or more segments
* Catch-all returns **array**
* Optional catch-all returns **array OR undefined**
* Used for **nested routing structures**

---

Just tell me 👍
