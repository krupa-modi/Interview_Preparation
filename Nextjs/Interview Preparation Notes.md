# Next.js Complete Interview Master Guide (A to Z)

# 1. What is Next.js?(16.2.6)

## Answer

Next.js is a React framework created by Vercel.

It provides:

* SSR
* SSG
* Routing
* API routes
* SEO optimization
* Image optimization
* Middleware
* Performance optimization

---

# 2. Why use Next.js instead of React?

## Answer

React only handles UI.

Next.js provides:

* File-based routing
* Server-side rendering
* Static generation
* Better SEO
* Backend APIs
* Faster performance

---

# 3. What is SSR?

## Answer

SSR = Server Side Rendering.

Page renders on server on every request.

## Use Cases

* Dashboard
* Live data
* Stock market
* User profile

## Example

```js
export async function getServerSideProps() {
  const res = await fetch("API_URL");
  const data = await res.json();

  return {
    props: { data }
  };
}
```

## Interview Line

> “SSR generates fresh HTML on every request.”

---

# 4. What is SSG?

## Answer

SSG = Static Site Generation.

Page generated during build time.

## Use Cases

* Blogs
* Documentation
* Landing pages

## Example

```js
export async function getStaticProps() {
  return {
    props: {}
  };
}
```

---

# 5. What is ISR?

## Answer

ISR = Incremental Static Regeneration.

Static page updates automatically after some interval.

## Example

```js
export async function getStaticProps() {
  return {
    props: {},
    revalidate: 60
  };
}
```

---

# 6. Difference between SSR, SSG, ISR

| SSR           | SSG        | ISR               |
| ------------- | ---------- | ----------------- |
| Every request | Build time | Regenerates later |
| Dynamic       | Static     | Semi-dynamic      |
| Slower        | Fastest    | Balanced          |

---

# 7. What is App Router?

## Answer

New routing system introduced in Next.js 13.

Uses:

```bash
app/
```

Supports:

* Nested layouts
* Server Components
* Loading states
* Error handling

---

# 8. What is Pages Router?

## Answer

Old routing system.

Uses:

```bash
pages/
```

---

# 9. Difference between App Router and Pages Router

| App Router        | Pages Router      |
| ----------------- | ----------------- |
| app folder        | pages folder      |
| Server Components | Traditional React |
| Nested layouts    | No nested layouts |
| New architecture  | Old architecture  |

---

# 10. File-Based Routing

## Example

```bash
app/about/page.js
```

Creates:

```bash
/about
```

---

# 11. Dynamic Routing

## Example

```bash
app/product/[id]/page.js
```

URL:

```bash
/product/10
```

## Access Params

```js
params.id
```

---

# 12. Catch-All Routes

## Example

```bash
[...slug]
```

URL:

```bash
/docs/react/hooks
```

Output:

```js
["react", "hooks"]
```

---

# 13. Optional Catch-All Route

## Example

```bash
[[...slug]]
```

Works with:

```bash
/docs
/docs/react
```

---

# 14. Route Groups

## Example

```bash
(auth)
```

Does not affect URL.

---

# 15. layout.js

## Answer

Shared UI across pages.

## Example

```js
export default function Layout({ children }) {
  return (
    <div>
      <Navbar />
      {children}
    </div>
  );
}
```

---

# 16. template.js

## Answer

Similar to layout but rerenders every navigation.

---

# 17. Difference between layout and template

| layout             | template        |
| ------------------ | --------------- |
| Preserves state    | Recreates state |
| Better performance | Fresh render    |

---

# 18. loading.js

## Answer

Shows loading UI automatically.

## Example

```js
export default function Loading() {
  return <h1>Loading...</h1>;
}
```

---

# 19. error.js

## Answer

Handles runtime errors.

## Example

```js
"use client";

export default function Error() {
  return <h1>Error</h1>;
}
```

---

# 20. not-found.js

## Answer

Custom 404 page.

---

# 21. route.js

## Answer

Used for backend API routes.

## Example

```js
export async function GET() {
  return Response.json({
    success: true
  });
}
```

---

# 22. What are Server Components?

## Answer

Default components in App Router.

Rendered on server.

## Benefits

* Smaller bundle size
* Better performance
* More secure

---

# 23. What are Client Components?

## Answer

Rendered in browser.

Needed when using:

* useState
* useEffect
* Browser APIs

## Example

```js
"use client";
```

---

# 24. Difference between Server and Client Components

| Server             | Client          |
| ------------------ | --------------- |
| Runs on server     | Runs in browser |
| Better performance | Interactive     |
| No hooks           | Hooks allowed   |

---

# 25. What is Hydration?

## Answer

React attaches events to server-rendered HTML.

---

# 26. What is Middleware?

## Answer

Runs before request completes.

## Use Cases

* Authentication
* Redirects
* Role-based access

## Example

```js
import { NextResponse } from "next/server";

export function middleware(req) {
  const token = req.cookies.get("token");

  if (!token) {
    return NextResponse.redirect(
      new URL("/login", req.url)
    );
  }
}
```

---

# 27. What is Link Component?

## Example

```js
import Link from "next/link";

<Link href="/about">About</Link>
```

---

# 28. Difference between Link and anchor tag

| Link                | a           |
| ------------------- | ----------- |
| Client-side routing | Full reload |
| Faster              | Slower      |

---

# 29. useRouter Example

```js
"use client";

import { useRouter } from "next/navigation";

const router = useRouter();

router.push("/dashboard");
```

---

# 30. usePathname

## Answer

Returns current URL path.

---

# 31. useSearchParams

## Example

```js
const params = useSearchParams();

params.get("id");
```

---

# 32. Image Optimization

## Example

```js
import Image from "next/image";

<Image
  src="/img.png"
  width={200}
  height={200}
  alt="img"
/>
```

## Benefits

* Lazy loading
* Responsive images
* Faster performance

---

# 33. Metadata

## Example

```js
export const metadata = {
  title: "Home",
  description: "Homepage"
};
```

---

# 34. API Routes GET Example

```js
export async function GET() {
  return Response.json({
    message: "Users fetched"
  });
}
```

---

# 35. API Routes POST Example

```js
export async function POST(req) {
  const body = await req.json();

  return Response.json({
    data: body
  });
}
```

---

# 36. Difference between GET and POST

| GET         | POST        |
| ----------- | ----------- |
| Fetch data  | Send data   |
| URL visible | Hidden body |

---

# 37. generateStaticParams

## Example

```js
export async function generateStaticParams() {
  return [
    { id: "1" },
    { id: "2" }
  ];
}
```

---

# 38. Revalidation

## Example

```js
export const revalidate = 60;
```

---

# 39. Dynamic Imports

## Example

```js
import dynamic from "next/dynamic";

const Heavy = dynamic(() => import("./Heavy"));
```

---

# 40. What is Lazy Loading?

## Answer

Loads component only when needed.

---

# 41. What is Code Splitting?

## Answer

Splits JS into smaller chunks automatically.

---

# 42. What is next.config.js?

## Answer

Main configuration file.

Used for:

* Redirects
* Rewrites
* Image domains
* Environment variables

---

# 43. Redirect Example

```js
async redirects() {
  return [
    {
      source: "/old",
      destination: "/new",
      permanent: true
    }
  ];
}
```

---

# 44. Rewrite Example

```js
async rewrites() {
  return [
    {
      source: "/about",
      destination: "/company/about"
    }
  ];
}
```

---

# 45. Environment Variables

## Example

```env
NEXT_PUBLIC_API_URL=url
```

Access:

```js
process.env.NEXT_PUBLIC_API_URL
```

---

# 46. What is Turbopack?

## Answer

Rust-based faster bundler introduced by Vercel.

Used to replace Webpack.

---

# 47. Turbopack vs Webpack

| Turbopack  | Webpack    |
| ---------- | ---------- |
| Rust based | JS based   |
| Faster     | Slower     |
| Better HMR | Slower HMR |

---

# 48. What is Streaming?

## Answer

UI loads in chunks instead of waiting for full page.

---

# 49. What is Edge Runtime?

## Answer

Runs code closer to user location.

Improves speed.

---

# 50. What is Partial Rendering?

## Answer

Only updated UI parts rerender.

---

# 51. Authentication Scenario Question

## Q: How do you protect private routes?

## Answer

Using middleware + token validation.

## Example

```js
export function middleware(req) {
  const token = req.cookies.get("token");

  if (!token) {
    return NextResponse.redirect(
      new URL("/login", req.url)
    );
  }
}
```

---

# 52. SEO Scenario Question

## Q: How did you improve SEO?

## Answer

* Used SSR/SSG
* Added metadata
* Optimized images
* Used semantic HTML

---

# 53. Performance Scenario Question

## Q: How did you optimize performance?

## Answer

* Used Server Components
* Used lazy loading
* Reduced client-side rendering
* Used caching
* Used next/image

---

# 54. Practical Coding Question

## Q: Fetch API data in App Router

## Example

```js
async function getUsers() {
  const res = await fetch(
    "https://jsonplaceholder.typicode.com/users"
  );

  return res.json();
}

export default async function Page() {
  const users = await getUsers();

  return (
    <div>
      {users.map((u) => (
        <h2 key={u.id}>{u.name}</h2>
      ))}
    </div>
  );
}
```

---

# 55. Tricky Question

## Q: Why can't we use useState in Server Components?

## Answer

Because Server Components run on the server and do not support browser interactivity.

---

# 56. Tricky Question

## Q: Why use "use client"?

## Answer

To convert component into Client Component so hooks and browser APIs can be used.

---

# 57. Tricky Question

## Q: Why is Next.js faster than React?

## Answer

Because Next.js provides:

* SSR
* SSG
* Code splitting
* Image optimization
* Better routing
* Server Components

---

# 58. Tricky Question

## Q: Difference between CSR and SSR?

| CSR                 | SSR                |
| ------------------- | ------------------ |
| Rendered in browser | Rendered on server |
| Slower first load   | Faster first load  |
| Weak SEO            | Better SEO         |

---

# 59. Tricky Question

## Q: When should we use Client Components?

## Answer

When using:

* useState
* useEffect
* Event handlers
* Browser APIs

---

# 60. Tricky Question

## Q: When should we avoid Client Components?

## Answer

When interactivity is not needed.

Because Client Components increase bundle size.

---

# 61. MNC-Level Scenario Question

## Q: Your page loads slowly. What will you do?

## Answer

* Use Server Components
* Optimize images
* Lazy load heavy components
* Reduce unnecessary API calls
* Use caching
* Use pagination

---

# 62. MNC-Level Scenario Question

## Q: Large dashboard rerenders too much. How do you optimize?

## Answer

* Use memoization
* Split components
* Use Server Components
* Avoid unnecessary state updates

---

# 63. MNC-Level Scenario Question

## Q: How do you handle secure APIs?

## Answer

* Validate tokens
* Use middleware
* Hide secrets in env variables
* Use server-side fetching

---

# 64. Coding Question

## Q: Create Dynamic Route

## Folder Structure

```bash
app/product/[id]/page.js
```

## Code

```js
export default function Product({ params }) {
  return <h1>{params.id}</h1>;
}
```

---

# 65. Coding Question

## Q: Create Loading UI

```js
export default function Loading() {
  return <h1>Loading...</h1>;
}
```

---

# 66. Coding Question

## Q: Create Error Boundary

```js
"use client";

export default function Error({ reset }) {
  return (
    <button onClick={() => reset()}>
      Retry
    </button>
  );
}
```

---

# 67. Coding Question

## Q: Redirect User Programmatically

```js
router.push("/dashboard");
```

---

# 68. Coding Question

## Q: Create API Route

```js
export async function GET() {
  return Response.json({
    success: true
  });
}
```

---

# 69. Real Project Interview Answer

## Q: What Next.js features have you used?

## Answer

> “I worked with App Router, SSR, dynamic routing, middleware authentication, API routes, lazy loading, metadata, server/client components, and image optimization.”

---

# 70. Real Project Interview Answer

## Q: How did you manage authentication?

## Answer

> “I protected routes using middleware and token validation with cookies/local storage.”

---

# 71. Real Project Interview Answer

## Q: How did you improve performance?

## Answer

> “I used lazy loading, dynamic imports, Server Components, caching, and optimized images.”

---

# 72. Most Important Rapid Fire Questions

| Question               | Answer                          |
| ---------------------- | ------------------------------- |
| What is SSR?           | Rendering on server per request |
| What is SSG?           | Build-time rendering            |
| What is ISR?           | Static regeneration             |
| What is hydration?     | Attach events to HTML           |
| What is middleware?    | Runs before request             |
| What is App Router?    | New routing system              |
| What is dynamic route? | Variable route params           |
| What is route.js?      | API route handler               |
| What is loading.js?    | Loading UI                      |
| What is error.js?      | Error handling                  |
| What is metadata?      | SEO config                      |
| What is useRouter?     | Navigation hook                 |
| What is next/image?    | Optimized image component       |
| What is Turbopack?     | Rust-based bundler              |

---

# 73. Super Important Final Interview Answers

## Why Next.js?

> “Next.js improves React applications using SSR, routing, SEO, optimization, API handling, and better performance.”

---

## Why App Router?

> “App Router provides layouts, Server Components, loading states, and better scalability.”

---

## Why Server Components?

> “They reduce bundle size and improve performance by rendering on server.”

---

## Why Middleware?

> “Middleware helps in authentication, redirects, and request interception.”

---

# 74. One-Day Revision Strategy

## Read in This Order

1. SSR / SSG / ISR
2. Routing
3. App Router
4. Server vs Client Components
5. Middleware
6. API routes
7. Dynamic routes
8. Performance optimization
9. Tricky questions
10. Scenario-based questions

---

# 75. Final MNC-Level Tip

## Best Interview Communication Style

Instead of saying:

❌ “I know Next.js.”

Say:

✅ “I have worked with App Router architecture, dynamic routing, middleware authentication, Server Components, SSR/SSG strategies, API routes, and performance optimization techniques in Next.js applications.”


# Next.js में routing कैसे काम करता है?

# What is Routing in Next.js?

Routing means navigating between pages in application.

Next.js provides:

# File-Based Routing

Meaning:
- File name = Route name

---

# Example

```text id="z0vfrs"
pages/
 ├── index.js
 ├── about.js
 └── contact.js
````

Routes become:

```text id="2t3d5q"
/           → index.js
/about      → about.js
/contact    → contact.js
```

---

# App Router (Next.js 13+)

Modern Next.js uses:

```text id="q9udmj"
app/
```

folder instead of `pages/`.

---

# Example

```text id="thxq6j"
app/
 ├── page.js
 ├── about/
 │    └── page.js
```

Routes:

```text id="l4ptt1"
/        → page.js
/about   → about/page.js
```

---

# Dynamic Routing

Used when route changes dynamically.

Example:

* Product details
* User profile

---

# Example

```text id="7hmqzh"
app/product/[id]/page.js
```

URL:

```text id="5xz9lq"
/product/1
/product/25
```

---

# Access Dynamic Route

```jsx
export default function Product({ params }) {
  return <h1>{params.id}</h1>;
}
```

---

# Nested Routing

Folders create nested routes automatically.

---

# Example

```text id="0ynrzm"
app/dashboard/settings/page.js
```

URL:

```text id="g3yr6f"
/dashboard/settings
```

---

# Link Navigation

Use `Link` component for navigation.

---

# Example

```jsx id="u7o0bm"
import Link from "next/link";

<Link href="/about">About</Link>
```

Benefits:

* Fast navigation
* No full page reload
* Client-side routing

---

# Programmatic Navigation

Use router for navigation through code.

---

# Example

```jsx id="8i90d9"
"use client";

import { useRouter } from "next/navigation";

const router = useRouter();

router.push("/about");
```

---

# Route Groups

Used to organize folders without affecting URL.

---

# Example

```text id="m2x6n4"
app/(auth)/login/page.js
```

URL:

```text id="0n7y9k"
/login
```

`(auth)` does not appear in URL.

---

# Loading Page

Create:

```text id="k7p4vr"
loading.js
```

Shows loading UI while page loads.

---

# Not Found Page

Create:

```text id="v3q6ts"
not-found.js
```

Custom 404 page.

---

# Layouts in Routing

`layout.js` creates shared UI.

Example:

* Navbar
* Sidebar
* Footer

---

# Example

```text id="2zq0ph"
app/dashboard/layout.js
```

Shared across dashboard pages.

---

# Important Interview Points

| Feature            | Purpose                   |
| ------------------ | ------------------------- |
| File-based routing | File name becomes route   |
| Dynamic routing    | Dynamic URLs              |
| Nested routing     | Folder-based nested pages |
| Link               | Client-side navigation    |
| useRouter          | Navigation using code     |
| layout.js          | Shared layouts            |
| loading.js         | Loading UI                |
| not-found.js       | 404 page                  |

---

# Common Interview Questions

## Q1: How routing works in Next.js?

Next.js uses file-based routing where file/folder structure automatically creates routes.

---

## Q2: What is dynamic routing?

Dynamic routing allows dynamic URLs using `[id]`.

Example:

```text id="dxx3ye"
product/[id]
```

---

## Q3: Difference between `<a>` and `Link`?

| `<a>` Tag        | `Link`                 |
| ---------------- | ---------------------- |
| Full page reload | Client-side navigation |
| Slower           | Faster                 |

---

# Short Interview Answer

```text id="o8rwyf"
Next.js uses file-based routing. 
Each file inside pages or app folder automatically becomes a route. 
Dynamic routing is created using [id]. 
Navigation is done using Link component or useRouter hook.
```

# Next.js में SEO कैसे improve करते हैं?

# What is SEO?

SEO (Search Engine Optimization) helps website rank better on Google and search engines.

Better SEO = Better visibility + More traffic.

---

# Why Next.js is Good for SEO?

React normally uses Client-Side Rendering (CSR).

Problem:
- Search engines may not see content properly.

Next.js solves this using:

- Server-Side Rendering (SSR)
- Static Site Generation (SSG)
- Metadata support

---

# Ways to Improve SEO in Next.js

---

# 1. Use Metadata

Add title and description.

---

# Example

```jsx id="evh7kx"
export const metadata = {
  title: "My Website",
  description: "Best website for learning"
};
````

Benefits:

* Better Google ranking
* Proper search preview

---

# 2. Use Server-Side Rendering (SSR)

Content rendered on server before sending to browser.

Better for:

* SEO
* Dynamic content

---

# Example

```jsx id="w4w0pw"
export async function getServerSideProps() {
  return {
    props: {}
  };
}
```

---

# 3. Use Static Site Generation (SSG)

Pre-build pages at build time.

Very fast and SEO friendly.

---

# Example

```jsx id="w8t0yl"
export async function getStaticProps() {
  return {
    props: {}
  };
}
```

---

# 4. Semantic HTML

Use proper tags:

```html
<header>
<nav>
<main>
<section>
<footer>
```

Helps search engines understand structure.

---

# 5. Optimize Images

Use Next.js Image component.

---

# Example

```jsx id="9wz03v"
import Image from "next/image";

<Image
  src="/logo.png"
  width={200}
  height={200}
  alt="Logo"
/>
```

Benefits:

* Lazy loading
* Faster website
* Better SEO

---

# 6. Fast Performance

Google prefers fast websites.

Next.js improves performance using:

* Code splitting
* Image optimization
* Static generation

---

# 7. Use Clean URLs

Good:

```text id="y86g20"
/products/shoes
```

Bad:

```text id="xmb6dg"
/page?id=123
```

---

# 8. Mobile Friendly Design

Responsive websites rank better.

Use:

* Responsive CSS
* Mobile-first design

---

# 9. Sitemap & Robots.txt

Help search engines crawl website properly.

---

# Example

```text id="z8h5pl"
sitemap.xml
robots.txt
```

---

# 10. Open Graph Tags

Used for social media preview.

---

# Example

```jsx id="ib6q3t"
export const metadata = {
  openGraph: {
    title: "My Site",
    description: "Learning Next.js"
  }
};
```

---

# Important Interview Points

| Feature          | SEO Benefit      |
| ---------------- | ---------------- |
| SSR              | Better indexing  |
| SSG              | Fast loading     |
| Metadata         | Better ranking   |
| next/image       | Optimized images |
| Semantic HTML    | Better structure |
| Fast performance | Better SEO score |

---

# Common Interview Questions

## Q1: Why is Next.js better for SEO than React?

Because Next.js supports SSR and SSG, which render content before page reaches browser.

---

## Q2: What is SSR?

Server renders page on every request.

---

## Q3: What is SSG?

Page generated at build time and served as static HTML.

---

## Q4: Why use next/image?

For automatic image optimization and faster loading.

---

# Short Interview Answer

```text id="p9d2ls"
SEO in Next.js is improved using SSR, SSG, metadata, optimized images, semantic HTML and fast performance. 
Next.js renders pages on server side which helps search engines crawl content easily.
```