# 🚀 Next.js Interview Quick Answers (Short & Crisp)

## 1. What is Next.js?

Next.js is a React framework that enables server-side rendering (SSR), static site generation (SSG), routing, and performance optimizations out of the box.

---

## 2. Why use Next.js instead of React?

React is a library (UI only), while Next.js is a full framework that provides routing, SSR, SEO, and better performance without extra setup.

---

## 3. Key Features of Next.js

* Server-Side Rendering (SSR)
* Static Site Generation (SSG)
* File-based routing
* API routes (backend support)
* Image optimization
* Built-in CSS & performance optimization

---

## 4. What problems does Next.js solve?

* Poor SEO in React apps
* Slow initial load time
* Manual routing setup
* Complex performance optimization

---

## 5. What is SSR in Next.js?

SSR (Server-Side Rendering) means pages are rendered on the server for every request and sent as fully built HTML to the client.

---

## 6. What is SEO and how Next.js improves it?

SEO (Search Engine Optimization) improves website ranking on search engines.
Next.js improves SEO using SSR/SSG so content is pre-rendered and easily indexed by search engines.

---

## 7. What is File-based Routing?

Routing in Next.js is based on the file structure inside the `pages` or `app` directory.
Example: `pages/about.js` → `/about`

---

## 8. Difference between App Router and Page Router

| Feature       | App Router                   | Page Router                         |
| ------------- | ---------------------------- | ----------------------------------- |
| Folder        | `/app`                       | `/pages`                            |
| Rendering     | Supports SSR, SSG, Streaming | SSR & SSG only                      |
| Layouts       | Nested layouts supported     | No built-in layout system           |
| Data Fetching | Server Components (modern)   | getServerSideProps / getStaticProps |
| Recommended   | ✅ New (Modern)               | ❌ Legacy                            |

---

💡 Tip: In interviews, highlight **performance + SEO + built-in features** — that’s what companies care about most.

