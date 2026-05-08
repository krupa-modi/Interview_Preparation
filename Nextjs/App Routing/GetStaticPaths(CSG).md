# 🚀 getStaticPaths in Next.js – Complete Interview Guide (VERY IMPORTANT 🔥)

---

# 1. What is `getStaticPaths`?

`getStaticPaths` is a special function in Next.js used with **dynamic routes** and `getStaticProps`.

👉 It tells Next.js:

* Which dynamic pages should be generated at build time.

---

# 🔥 Simple Definition

👉 “getStaticPaths defines all possible dynamic paths that need static generation.”

---

# 2. Why Do We Need `getStaticPaths`?

Suppose we have dynamic route:

```bash id="y4m8zp"
pages/blog/[id].js
```

👉 Next.js does NOT know:

* Which IDs exist
* Which pages to generate

👉 So we use:

```js id="j9x3vq"
getStaticPaths()
```

to tell Next.js all available paths.

---

# 3. Basic Syntax

```js id="q2v7tm"
export async function getStaticPaths() {
  return {
    paths: [],
    fallback: false,
  };
}
```

---

# 4. Basic Example

---

## 📂 File Structure

```bash id="z7m2pk"
pages/blog/[id].js
```

---

## 🔍 Full Example

```js id="w3v8tx"
function Blog({ post }) {
  return <h1>{post.title}</h1>;
}

export async function getStaticPaths() {
  return {
    paths: [
      { params: { id: '1' } },
      { params: { id: '2' } },
    ],
    fallback: false,
  };
}

export async function getStaticProps(context) {
  const { id } = context.params;

  const res = await fetch(`https://api.com/posts/${id}`);
  const post = await res.json();

  return {
    props: { post },
  };
}

export default Blog;
```

---

# 🔥 What Happens Here?

---

## During Build Time

Next.js creates pages:

```text id="u5x9qr"
/blog/1
/blog/2
```

👉 Static HTML generated for both pages.

---

# 5. Important Point 🔥

👉 `getStaticPaths` ONLY works with:

```js id="d4v7pm"
getStaticProps
```

❌ Cannot use with:

```js id="n8m2qt"
getServerSideProps
```

---

# 6. Structure of paths

---

## Example

```js id="r3v8xp"
paths: [
  { params: { id: '1' } },
  { params: { id: '2' } },
]
```

---

## URL Generated

```text id="m7q2vk"
/blog/1
/blog/2
```

---

# 7. Access Params

Inside:

```js id="j2m9wt"
getStaticProps(context)
```

👉 Access using:

```js id="v4x8pk"
context.params.id
```

---

# 8. fallback (VERY IMPORTANT 🔥🔥)

`fallback` controls behavior for paths NOT generated during build.

---

# 🔥 Types of fallback

| Mode     | Meaning                   |
| -------- | ------------------------- |
| false    | Unknown routes → 404      |
| true     | Generate page dynamically |
| blocking | Wait until page generated |

---

# 9. fallback: false

```js id="x3v7tm"
fallback: false
```

👉 Only predefined routes allowed.

---

## Example

Generated:

```text id="f8m2qp"
/blog/1
/blog/2
```

User visits:

```text id="e7v4zn"
/blog/3
```

👉 Output:

```text id="h9x2pk"
404 Page
```

---

# 10. fallback: true

```js id="p2m8wr"
fallback: true
```

👉 Missing pages generated on first request.

---

## Flow

```text id="n6v3qt"
Request unknown page
      ↓
Loading state shown
      ↓
Page generated dynamically
      ↓
Cached for next time
```

---

# 🔥 Important

Need loading handling:

```js id="m4x9vp"
import { useRouter } from 'next/router';

const router = useRouter();

if (router.isFallback) {
  return <p>Loading...</p>;
}
```

---

# 11. fallback: 'blocking'

```js id="w9q2xt"
fallback: 'blocking'
```

👉 User waits until page generated.

---

## Flow

```text id="u7m4pk"
Request unknown page
      ↓
Server generates page
      ↓
Send completed page
```

👉 No loading state.

---

# 🔥 Difference: true vs blocking

| Feature    | true  | blocking |
| ---------- | ----- | -------- |
| Loading UI | ✅ Yes | ❌ No     |
| User waits | ❌ No  | ✅ Yes    |

---

# 12. Real Use Cases

---

## Blog Website

```text id="a3v8mq"
/blog/1
/blog/2
/blog/3
```

---

## E-commerce Product Pages

```text id="k7m2zp"
/product/101
/product/102
```

---

## Documentation Sites

Dynamic docs pages.

---

# 13. Build-Time Generation Flow

```text id="s8v3qt"
npm run build
      ↓
getStaticPaths runs
      ↓
All paths generated
      ↓
getStaticProps fetches data
      ↓
Static HTML created
```

---

# 14. SEO Benefits

Because pages are statically generated:

* Fast loading ⚡
* Better SEO ✅
* CDN caching ✅

---

# 15. Performance Benefits

* Extremely fast
* Less server work
* Better scalability

---

# 16. Important Rules 🔥

---

## ✅ Only for Dynamic Routes

```bash id="d2m8xq"
[id].js
```

---

## ✅ Must Return

```js id="w6v3pt"
{
  paths: [],
  fallback: false
}
```

---

## ❌ Cannot Use Without getStaticProps

---

# 17. Difference: getStaticPaths vs getServerSideProps

| Feature   | getStaticPaths | getServerSideProps      |
| --------- | -------------- | ----------------------- |
| Purpose   | Generate paths | Fetch request-time data |
| Runs      | Build time     | Every request           |
| Used With | getStaticProps | Alone                   |

---

# 18. Real Interview Questions

---

## ❓ Why use getStaticPaths?

👉 To define dynamic routes that should be statically generated.

---

## ❓ Does it run on client side?

❌ No

👉 Runs only during build.

---

## ❓ Is fallback mandatory?

✅ Yes

Need:

```js id="f5v9qm"
fallback
```

---

## ❓ Which fallback is best?

Depends on use case:

* `false` → fixed pages
* `true` → loading allowed
* `blocking` → SEO-friendly dynamic pages

---

# 🎯 Final Interview Answer

👉 `getStaticPaths` is used in Next.js dynamic routes to define which pages should be generated at build time.

👉 It works together with `getStaticProps` and supports fallback modes for handling unknown routes dynamically.

---

# 💡 MNC Interview Pro Tip

Say this 👇

👉 “getStaticPaths enables static generation for dynamic routes by predefining all available paths during build time.” 🚀
