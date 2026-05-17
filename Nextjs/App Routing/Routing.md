## 1. File-Based Routing

Next.js uses **folder & file structure** for routing.

```bash
app/
 ├── about/
 │    └── page.js
```

URL:

```bash
/about
```

### Example

```js
// app/about/page.js

export default function About() {
  return <h1>About Page</h1>;
}
```

---

# 2. `page.js`

Represents the actual UI of a route.

### Example

```js
// app/contact/page.js

export default function Contact() {
  return <h1>Contact Page</h1>;
}
```

---

# 3. Nested Routes

Folders inside folders create nested URLs.

```bash
app/
 ├── blog/
 │    ├── tech/
 │    │    └── page.js
```

URL:

```bash
/blog/tech
```

---

# 4. Dynamic Routes `[id]`

Used for dynamic values.

### Example

```bash
app/
 ├── product/
 │    ├── [id]/
 │    │    └── page.js
```

URL:

```bash
/product/10
/product/20
```

### Example Code

```js
export default function Product({ params }) {
  return <h1>Product ID: {params.id}</h1>;
}
```

---

# 5. Catch-All Routes `[...slug]`

Handles multiple segments.

### Example

```bash
app/docs/[...slug]/page.js
```

URL:

```bash
/docs/react/hooks/useEffect
```

### Output

```js
params.slug
// ["react", "hooks", "useEffect"]
```

---

# 6. Optional Catch-All `[[...slug]]`

Route may or may not have params.

### Example

```bash
app/docs/[[...slug]]/page.js
```

Works for:

```bash
/docs
/docs/react
/docs/react/hooks
```

---

# 7. Route Groups `(group)`

Used to organize folders without affecting URL.

### Example

```bash
app/
 ├── (auth)/
 │    ├── login/
 │    ├── register/
```

URL:

```bash
/login
/register
```

---

# 8. `layout.js`

Shared UI across routes.

### Example

```js
// app/dashboard/layout.js

export default function DashboardLayout({ children }) {
  return (
    <div>
      <nav>Sidebar</nav>
      {children}
    </div>
  );
}
```

---

# 9. Root Layout

Mandatory in App Router.

```js
// app/layout.js

export default function RootLayout({ children }) {
  return (
    <html>
      <body>{children}</body>
    </html>
  );
}
```

---

# 10. `template.js`

Similar to layout but re-renders every navigation.

### Use Case

* Animation reset
* Fresh state every page change

### Example

```js
export default function Template({ children }) {
  return <div>{children}</div>;
}
```

---

# 11. `loading.js`

Shows loader during page loading.

### Example

```js
export default function Loading() {
  return <h1>Loading...</h1>;
}
```

---

# 12. `error.js`

Handles route errors.

### Example

```js
"use client";

export default function Error({ error, reset }) {
  return (
    <div>
      <h1>Error Occurred</h1>
      <button onClick={() => reset()}>
        Retry
      </button>
    </div>
  );
}
```

---

# 13. `not-found.js`

Custom 404 page.

### Example

```js
export default function NotFound() {
  return <h1>Page Not Found</h1>;
}
```

---

# 14. `route.js`

Used for API routes in App Router.

### Example

```js
// app/api/users/route.js

export async function GET() {
  return Response.json({
    message: "Users API"
  });
}
```

---

# 15. Route Handlers (GET, POST, PUT, DELETE)

### Example

```js
export async function POST(req) {
  return Response.json({
    success: true
  });
}
```

---

# 16. Parallel Routes `@folder`

Render multiple pages together.

### Example Structure

```bash
app/
 ├── dashboard/
 │    ├── @analytics/
 │    ├── @users/
```

### Use Case

* Dashboard sections
* Multiple panels

---

# 17. Intercepting Routes `(.)`

Open route inside current layout/modal.

### Example

```bash
(.)photo
```

### Use Case

* Instagram-like modal routing

---

# 18. Client Side Navigation

Using `Link`.

### Example

```js
import Link from "next/link";

<Link href="/about">About</Link>
```

---

# 19. Programmatic Navigation

Using `useRouter`.

### Example

```js
"use client";

import { useRouter } from "next/navigation";

const router = useRouter();

router.push("/dashboard");
```

---

# 20. `redirect()`

Redirect user to another page.

### Example

```js
import { redirect } from "next/navigation";

redirect("/login");
```

---

# 21. `usePathname()`

Get current URL path.

### Example

```js
import { usePathname } from "next/navigation";

const pathname = usePathname();
```

---

# 22. `useSearchParams()`

Read query params.

### URL

```bash
/products?id=10
```

### Example

```js
const params = useSearchParams();

params.get("id");
```

---

# 23. Search Params in Server Component

### Example

```js
export default function Page({ searchParams }) {
  return <h1>{searchParams.name}</h1>;
}
```

---

# 24. Static Routes

Fixed routes.

```bash
/about
/contact
```

---

# 25. Dynamic Rendering vs Static Rendering

## Static

Pre-generated at build time.

## Dynamic

Generated on every request.

### Example

```js
export const dynamic = "force-dynamic";
```

---

# 26. `generateStaticParams()`

Pre-build dynamic routes.

### Example

```js
export async function generateStaticParams() {
  return [
    { id: "1" },
    { id: "2" }
  ];
}
```

---

# 27. Middleware Routing

Runs before request completes.

### Example

```js
// middleware.js

import { NextResponse } from "next/server";

export function middleware(req) {
  return NextResponse.redirect(
    new URL("/login", req.url)
  );
}
```

### Use Case

* Auth protection
* Redirects

---

# 28. Rewrites

Changes route internally without changing URL.

### Example

```js
// next.config.js

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

# 29. Redirects in Config

### Example

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

# 30. Metadata Routing

SEO metadata per route.

### Example

```js
export const metadata = {
  title: "Home Page",
  description: "Welcome"
};
```

---

# 31. Private Folders `_folder`

Ignored by routing system.

### Example

```bash
_components/
_utils/
```

---

# 32. Route Segment Config

### Example

```js
export const revalidate = 60;
```

### Used For

* Caching
* Rendering control

---

# 33. Pages Router vs App Router

| Pages Router          | App Router        |
| --------------------- | ----------------- |
| Uses `pages` folder   | Uses `app` folder |
| Old approach          | New approach      |
| No layouts by default | Nested layouts    |
| Uses API routes       | Route handlers    |

---

# 34. Important Interview Points

## Difference: `layout.js` vs `template.js`

| layout.js              | template.js         |
| ---------------------- | ------------------- |
| Preserves state        | Recreates state     |
| Doesn't rerender fully | Rerenders           |
| Better performance     | Fresh UI every time |

---

## Difference: `Link` vs `a`

| Link                   | a                |
| ---------------------- | ---------------- |
| Client-side navigation | Full page reload |
| Faster                 | Slower           |

---

## Difference: Static vs Dynamic Route

| Static     | Dynamic         |
| ---------- | --------------- |
| Fixed path | Variable path   |
| `/about`   | `/product/[id]` |

---

# 35. Full Important App Router Files

| File           | Purpose                      |
| -------------- | ---------------------------- |
| `page.js`      | Route UI                     |
| `layout.js`    | Shared layout                |
| `template.js`  | Re-render wrapper            |
| `loading.js`   | Loader                       |
| `error.js`     | Error UI                     |
| `not-found.js` | 404 page                     |
| `route.js`     | API route                    |
| `default.js`   | Fallback for parallel routes |

---

# 36. Interview One-Line Summary

> “Next.js App Router uses file-based routing where folders define routes and special files like `layout.js`, `loading.js`, `error.js`, and `route.js` control UI, loading state, error handling, and APIs.”
