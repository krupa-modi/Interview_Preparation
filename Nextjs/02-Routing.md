# 📄 Next.js Pages Router – Interview Notes (With Examples)

---

## 1. What is Pages Router?

Pages Router is the traditional routing system in Next.js where routes are created based on files inside the `/pages` folder.

👉 Each file automatically becomes a route.

**Example:**

```
pages/about.js → /about
```

---

## 2. How does file-based routing work?

Next.js uses the file structure inside `/pages` to define routes automatically.

**Example:**

```
pages/
 ├── index.js       → /
 ├── about.js       → /about
 ├── blog.js        → /blog
```

👉 No need to install or configure a router manually.

---

## 3. What is index.js?

`index.js` represents the default route of a folder.

**Example:**

```
pages/index.js → /
pages/blog/index.js → /blog
```

---

# 🔁 Dynamic Routes

## 4. What is dynamic routing?

Dynamic routing allows creating routes with dynamic values like IDs.

👉 Useful when pages depend on data (e.g., blog posts, product pages).

---

## 5. How to create dynamic routes? → `[id].js`

Create a file using square brackets:

```
pages/blog/[id].js
```

**URL Example:**

```
/blog/1
/blog/abc
```

---

## 6. How to access params using useRouter()?

```js
import { useRouter } from 'next/router';

const Blog = () => {
  const router = useRouter();
  const { id } = router.query;

  return <h1>Blog ID: {id}</h1>;
};

export default Blog;
```

---

## 7. What happens if param is missing?

* During initial render → `id` may be `undefined`
* Happens because data loads asynchronously

👉 Always handle it safely:

```js
if (!id) return <p>Loading...</p>;
```

---

# 🔥 Catch-all Routes

## 8. What are catch-all routes? → `[...slug].js`

Catch-all routes match multiple URL segments.

```
pages/docs/[...slug].js
```

---

## 9. How does URL map to array params?

**URL:**

```
/docs/a/b/c
```

**Result:**

```js
slug = ['a', 'b', 'c']
```

---

## 10. Real use case of catch-all routes?

* Documentation pages
* Nested categories
* Multi-level navigation

👉 Example:

```
/docs/react/hooks/useEffect
```

---

# 🔥 Optional Catch-all Routes

## 11. What are optional catch-all routes? → `[[...slug]].js`

Optional catch-all routes work like catch-all but also match the root path.

```
pages/docs/[[...slug]].js
```

---

## 12. Difference between catch-all vs optional catch-all?

| Feature             | Catch-all `[...slug]` | Optional Catch-all `[[...slug]]` |
| ------------------- | --------------------- | -------------------------------- |
| Root path (`/docs`) | ❌ Not supported       | ✅ Supported                      |
| Nested paths        | ✅ Yes                 | ✅ Yes                            |
| Param value         | Always array          | Array or undefined               |

---

## 🔥 Example Comparison

### Catch-all:

```
/docs → ❌ Error
/docs/a → ['a']
```

### Optional Catch-all:

```
/docs → undefined
/docs/a → ['a']
```

---

💡 **Interview Tip:**

* Dynamic routes → `[id]`
* Catch-all → `[...slug]`

  # 🚀 Next.js App Router vs Pages Router (Interview Ready)

---

## 13. What is Pages Router?

Pages Router is the **old/traditional routing system** in Next.js using the `/pages` folder.

👉 Each file becomes a route.

**Example:**

```id="p1"
pages/index.js → /
pages/about.js → /about
```

👉 Uses:

* `getServerSideProps`
* `getStaticProps`

---

## 14. What is App Router?

App Router is the **new modern routing system** in Next.js using the `/app` folder.

👉 Supports advanced features like layouts, server components, and streaming.

**Example:**

```id="p2"
app/page.js → /
app/about/page.js → /about
```

---

# 🔥 15. Key Differences

| Feature       | Pages Router                       | App Router                   |
| ------------- | ---------------------------------- | ---------------------------- |
| Folder        | `/pages`                           | `/app`                       |
| Type          | Old (Legacy)                       | New (Recommended)            |
| Routing       | File-based                         | File + Folder-based          |
| Layouts       | ❌ Manual                           | ✅ Built-in nested layouts    |
| Data Fetching | getServerSideProps, getStaticProps | Fetch directly in components |
| Components    | Client-side                        | Server + Client components   |
| Performance   | Good                               | Better (Streaming + SSR)     |

---

# 🔥 16. Routing Difference (Example)

## Pages Router:

```id="p3"
pages/blog/[id].js
```

👉 URL:

```
/blog/1
```

---

## App Router:

```id="p4"
app/blog/[id]/page.js
```

👉 URL:

```
/blog/1
```

👉 More structured and scalable.


# 🎯 Final Interview Answer (Short Version)

👉 Pages Router is the traditional routing system using `/pages` with functions like `getServerSideProps`.
👉 App Router is the modern system using `/app` with **server components, layouts, and better performance**.

👉 App Router is **recommended for new applications**.

---

💡 **Pro Tip:**
If interviewer asks “Which one should we use?” →
👉 Say: **App Router because of better performance, layouts, and scalability**.

* Optional → `[[...slug]]`
  👉 Focus on **real-world usage + param handling** to stand out.
