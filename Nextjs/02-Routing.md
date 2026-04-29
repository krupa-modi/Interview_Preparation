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

  # 🔗 Next.js Navigation – Interview Quick Notes

---

## 1. What is `next/link`?

`next/link` is used for **client-side navigation** between pages in Next.js without full page reload.

👉 Faster than normal `<a>` tag.

**Example:**

```jsx
import Link from 'next/link';

<Link href="/about">Go to About</Link>
```

👉 Improves performance by avoiding page refresh.

---

## 2. What is `next/router`?

`next/router` is used for **programmatic navigation** and accessing route data (params, query, path).

**Example:**

```js
import { useRouter } from 'next/router';

const router = useRouter();

router.push('/about'); // navigate programmatically
```

👉 Also used to get params:

```js
const { id } = router.query;
```

---

## 3. Difference between `<Link>` vs `router.push()`

| Feature | `<Link>`                 | `router.push()`         |
| ------- | ------------------------ | ----------------------- |
| Usage   | Navigation in UI         | Programmatic navigation |
| Trigger | User click               | JS logic / events       |
| SEO     | ✅ Good                   | ❌ Not directly          |
| Example | `<Link href="/about" />` | `router.push('/about')` |

👉 **Interview Tip:**
Use `<Link>` for UI navigation, `router.push()` for logic-based navigation.

---

## 4. What is Shallow Routing?

Shallow routing allows changing the URL **without re-running data fetching methods** like `getServerSideProps`.

👉 Page does not reload fully.

**Example:**

```js
router.push('/?page=2', undefined, { shallow: true });
```

👉 Useful for filters, pagination.

---

## 5. What is Prefetching?

Prefetching means Next.js **loads page data in advance** before user clicks.

👉 Makes navigation super fast ⚡

**Example:**

```jsx
<Link href="/about" prefetch={true}>About</Link>
```

👉 By default, Next.js prefetches links in viewport (production mode).

---

# 🎯 Final Interview Summary

* `next/link` → Client-side navigation
* `next/router` → Programmatic navigation + route data
* `<Link>` vs `router.push()` → UI vs Logic
* Shallow Routing → Change URL without re-fetch
* Prefetching → Load page in advance for speed

# 📦 Next.js Params, Query & Routing APIs (Interview Notes)

---

## 1. What are Params in Next.js?

**Params** are dynamic route values defined in the URL using file names like `[id]`.

👉 Used in **dynamic routing**

**Example (Pages Router):**

```js
// pages/blog/[id].js
import { useRouter } from 'next/router';

export default function Blog() {
  const router = useRouter();
  const { id } = router.query;

  return <h1>Blog ID: {id}</h1>;
}
```

👉 URL:

```
/blog/101 → id = 101
```

---

## 2. What is Query in Next.js?

**Query** refers to key-value pairs in the URL after `?`

👉 Used for filters, search, pagination.

**Example:**

```
/products?page=2&category=mobile
```

**Access Query:**

```js
import { useRouter } from 'next/router';

const router = useRouter();
const { page, category } = router.query;
```

👉 Output:

```
page = 2
category = mobile
```

---

# 🔥 Difference: Params vs Query

| Feature    | Params          | Query              |
| ---------- | --------------- | ------------------ |
| Defined in | URL path        | URL after `?`      |
| Example    | `/blog/1`       | `/blog?page=1`     |
| Usage      | Dynamic routing | Filtering / search |

---

# 🔗 3. What is `next/router`?

`next/router` is used in **Pages Router** for:

* Navigation
* Accessing params & query
* Route info

**Example:**

```js
import { useRouter } from 'next/router';

const router = useRouter();

router.push('/about'); // navigate
console.log(router.pathname); // current path
```

---

# 🔗 4. What is `next/navigation`?

`next/navigation` is used in **App Router (modern Next.js)**.

👉 Replaces `next/router`

**Features:**

* Navigation
* Access params & search params
* Works with Server & Client components

---

## Example (App Router)

### 📌 Navigation:

```js
'use client';
import { useRouter } from 'next/navigation';

const router = useRouter();

router.push('/about');
```

---

### 📌 Get Params:

```js
import { useParams } from 'next/navigation';

const params = useParams();
console.log(params.id);
```

---

### 📌 Get Query:

```js
'use client';
import { useSearchParams } from 'next/navigation';

const searchParams = useSearchParams();

const page = searchParams.get('page');
```

---

# 🔥 5. Difference: `next/router` vs `next/navigation`

| Feature     | next/router  | next/navigation   |
| ----------- | ------------ | ----------------- |
| Used in     | Pages Router | App Router        |
| Type        | Old          | New               |
| Params      | router.query | useParams()       |
| Query       | router.query | useSearchParams() |
| Recommended | ❌ No         | ✅ Yes             |

---

# 🎯 Final Interview Answer (Short)

👉 **Params** are dynamic values from URL path (`/blog/[id]`)
👉 **Query** are key-value pairs after `?`

👉 `next/router` → used in Pages Router
👉 `next/navigation` → modern API for App Router



