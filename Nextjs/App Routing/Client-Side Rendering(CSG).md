Here are separate interview-focused markdown notes for SSR, SSG, CSR, and ISR.

# 🚀 SSR (Server-Side Rendering) in Next.js – Complete Interview Guide

---

# 1. What is SSR?

SSR means:
👉 HTML page is generated on the server for EVERY request.

In Next.js:

```js
getServerSideProps()
```

is used for SSR.

---

# 🔥 Flow of SSR

```text
User Request
    ↓
Server Fetches Data
    ↓
HTML Generated on Server
    ↓
HTML Sent to Browser
```

---

# 2. Why Use SSR?

Used when:

* Need fresh data every request
* User-specific content
* Authentication
* Real-time dashboards

---

# 🔍 Example

```js
export async function getServerSideProps() {
  const res = await fetch('https://api.com/users');
  const data = await res.json();

  return {
    props: { data }
  };
}
```

---

# 🔥 Advantages

* Fresh data always ✅
* Better SEO ✅
* Secure server-side fetching ✅

---

# ❌ Disadvantages

* Slower than static pages
* Server load higher

---

# 🔥 Best Use Cases

| Use Case     | Why SSR              |
| ------------ | -------------------- |
| Dashboard    | Real-time data       |
| Stock market | Live updates         |
| User profile | Personalized content |

---

# 🎯 Final Interview Answer

👉 SSR renders pages on server for every request using `getServerSideProps`.
👉 Best for dynamic and real-time data.

# ⚡ SSG (Static Site Generation) in Next.js – Complete Interview Guide

---

# 1. What is SSG?

SSG means:
👉 HTML pages are generated at BUILD TIME.

In Next.js:

```js
getStaticProps()
```

is used for SSG.

---

# 🔥 Flow of SSG

```text
Build Time
    ↓
Fetch Data
    ↓
Generate Static HTML
    ↓
Serve Same HTML to Everyone
```

---

# 2. Why Use SSG?

Used when:

* Data changes rarely
* Need very fast performance
* SEO important

---

# 🔍 Example

```js
export async function getStaticProps() {
  const res = await fetch('https://api.com/posts');
  const posts = await res.json();

  return {
    props: { posts }
  };
}
```

---

# 🔥 Advantages

* Extremely fast ⚡
* SEO friendly ✅
* Low server load ✅
* CDN caching ✅

---

# ❌ Disadvantages

* Data can become outdated
* Need rebuild for updates

---

# 🔥 Best Use Cases

| Use Case     | Why SSG        |
| ------------ | -------------- |
| Blog         | Static content |
| Portfolio    | Rare updates   |
| Docs website | Fast loading   |

---

# 🎯 Final Interview Answer

👉 SSG generates static HTML at build time using `getStaticProps`.
👉 Best for fast and SEO-friendly static websites.

# 🔥 CSR (Client-Side Rendering) & ISR (Incremental Static Regeneration) – Interview Guide

---

# 1. What is CSR?

CSR means:
👉 Browser loads minimal HTML first, then JavaScript fetches data and renders UI.

---

# 🔥 Flow of CSR

```text
Browser Receives Empty HTML
      ↓
JavaScript Loads
      ↓
Fetch Data
      ↓
Render UI
```

---

# 🔍 Example

```js
import { useEffect, useState } from 'react';

function Home() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('/api/data')
      .then(res => res.json())
      .then(setData);
  }, []);

  return <div>{data.length}</div>;
}
```

---

# 🔥 Advantages

* Rich interactivity
* Faster page transitions
* Good for SPAs

---

# ❌ Disadvantages

* Poor SEO ❌
* Initial blank screen ❌
* Slower first load ❌

---

# 🔥 Best Use Cases

| Use Case       | Why CSR            |
| -------------- | ------------------ |
| Admin panel    | SEO not important  |
| Internal tools | Dynamic UI         |
| SPA apps       | Client-heavy logic |

---



