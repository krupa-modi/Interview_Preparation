
# 📌 1. What is `page.tsx`?

## 🧠 Definition

`page.tsx` defines a **route (UI for a specific URL)** in Next.js App Router.

👉 Every folder becomes a route only if it contains a `page.tsx`.

---

## 📁 Example

```tsx
// app/dashboard/page.tsx

export default function DashboardPage() {
  return <h1>Dashboard Page</h1>;
}
```

👉 Accessible at:

```
/dashboard
```

---

## 🧠 Key Points

* Required to create a route
* Default export must be a React component
* Can be Server Component (default) or Client Component
* Works inside layouts

---

## 🔥 Interview Line

> "page.tsx represents a route in Next.js and renders the UI for that specific path."

---

# 📌 2. What is `layout.tsx`?

## 🧠 Definition

`layout.tsx` is used to create **shared UI across multiple pages**.

---

## 📁 Example

```tsx
// app/dashboard/layout.tsx

export default function DashboardLayout({ children }: { children: React.ReactNode }) {
  return (
    <div>
      <nav>Dashboard Navbar</nav>
      <main>{children}</main>
    </div>
  );
}
```

---

## 🧠 Key Points

* Wraps all pages inside that folder
* Supports nesting (multiple layouts)
* Persists between navigation
* Improves performance

---

## 🔥 Interview Line

> "layout.tsx defines persistent shared UI and wraps pages within a route segment."

---

# 📌 3. What is `loading.tsx`?

## 🧠 Definition

`loading.tsx` is used to show a **loading UI (fallback)** while a route or data is loading.

---

## 📁 Example

```tsx
// app/dashboard/loading.tsx

export default function Loading() {
  return <p>Loading dashboard...</p>;
}
```

---

## ⏱️ When does it trigger?

### 🔥 Automatically triggered when:

* Page is loading
* Data fetching is in progress
* Route is changing (slow network)

---

## 🧠 Internals

* Built on **React Suspense**
* Automatically wraps page/layout in Suspense boundary

---

## 🎯 Example with Data Fetching

```tsx
// app/dashboard/page.tsx

async function getData() {
  await new Promise(res => setTimeout(res, 3000));
  return "Data Loaded";
}

export default async function Page() {
  const data = await getData();
  return <div>{data}</div>;
}
```

👉 While waiting → `loading.tsx` shows

---

## 🔥 Interview Line

> "loading.tsx provides a Suspense fallback UI and is automatically shown during route or data loading."

---

# 📌 4. What is `error.tsx`?

## 🧠 Definition

`error.tsx` acts as an **Error Boundary** for a route segment.

👉 It catches runtime errors in:

* page
* layout
* child components

---

## 📁 Example

```tsx
// app/dashboard/error.tsx

"use client";

export default function Error({ error, reset }: { error: Error; reset: () => void }) {
  return (
    <div>
      <h2>Something went wrong!</h2>
      <button onClick={() => reset()}>Try again</button>
    </div>
  );
}
```

---

## ⚠️ Important

* MUST be a Client Component (`"use client"`)
* Receives:

  * `error`
  * `reset()` → retry rendering

---

## 🧠 How Error Boundary Works?

1. Error occurs in child component
2. Next.js catches it
3. Shows `error.tsx` UI
4. Prevents full app crash

---

## 🔄 Reset Flow

```tsx
reset()
```

👉 Re-renders the segment again

---

## 🔥 Interview Line

> "error.tsx acts as a route-level error boundary that catches rendering errors and provides a fallback UI with recovery support."

---

# 📌 5. What is `not-found.tsx`?

## 🧠 Definition

`not-found.tsx` is used to show a **custom 404 page**.

---

## 📁 Example

```tsx
// app/not-found.tsx

export default function NotFound() {
  return <h1>404 - Page Not Found</h1>;
}
```

---

## 🧠 When does it trigger?

### 🔥 Automatically when:

* Route doesn't exist
* You manually call `notFound()`

---

## 📌 Example (Manual Trigger)

```tsx
import { notFound } from "next/navigation";

export default function Page({ params }) {
  if (params.id !== "valid") {
    notFound();
  }

  return <div>Valid Page</div>;
}
```

---

## 🧠 Internals

* Throws a special error internally
* Caught by Next.js
* Renders nearest `not-found.tsx`

---

## 🔥 Interview Line

> "not-found.tsx handles 404 scenarios and can be triggered automatically or programmatically using the notFound() function."

---

# 📌 6. Folder Structure (All Together)

```bash
app/
 ├── layout.tsx
 ├── page.tsx
 ├── loading.tsx
 ├── error.tsx
 ├── not-found.tsx
 ├── dashboard/
 │    ├── layout.tsx
 │    ├── page.tsx
 │    ├── loading.tsx
 │    ├── error.tsx
```

---

# 📌 7. How They Work Together (Flow)

### 🔄 Navigation Flow:

1. Route requested
2. layout.tsx wraps page
3. page.tsx renders
4. If loading → loading.tsx
5. If error → error.tsx
6. If not found → not-found.tsx

---

# 🎯 Final Interview Summary

| File          | Purpose              |
| ------------- | -------------------- |
| page.tsx      | Defines route UI     |
| layout.tsx    | Shared persistent UI |
| loading.tsx   | Loading fallback UI  |
| error.tsx     | Error boundary       |
| not-found.tsx | 404 handling         |

---

# 🚀 One-Line Killer Answer

> "Next.js App Router provides special files like page.tsx for routing, layout.tsx for shared UI, loading.tsx for Suspense fallback, error.tsx for error boundaries, and not-found.tsx for 404 handling, enabling structured and resilient UI architecture."

---

## 💡 Pro Tip (Interview)

👉 Always mention:

* Suspense (for loading)
* Error Boundary (for error.tsx)
* Segment-based routing

---
