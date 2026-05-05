# 🔥 Next.js Navigation (App Router) – In-Depth Interview Guide

---

## 1. What is `next/navigation`?

`next/navigation` is the **modern navigation API** used in the **App Router (`/app`)**.

👉 It replaces `next/router` and provides:

* Navigation (push, replace, back)
* Access to URL data (params, pathname, query)
* Works with **Server + Client Components**

---

## 2. Why `next/navigation` was introduced?

👉 Problems with `next/router`:

* Old (Pages Router only) ❌
* Not aligned with Server Components ❌

👉 Solution:

* Modern hooks-based API ✅
* Works with App Router ✅
* Better performance & flexibility ✅

---

# 🔥 3. Difference: `next/router` vs `next/navigation`

| Feature     | next/router   | next/navigation    |
| ----------- | ------------- | ------------------ |
| Used in     | Pages Router  | App Router         |
| Type        | Old ❌         | New ✅              |
| Params      | router.query  | useParams()        |
| Query       | router.query  | useSearchParams()  |
| Navigation  | router.push() | useRouter().push() |
| Recommended | ❌ No          | ✅ Yes              |

---

# 🔗 4. Hooks in `next/navigation`

---

## 4.1 useRouter()

👉 Used for **programmatic navigation**

```js id="q9f8z2"
'use client';
import { useRouter } from 'next/navigation';

const router = useRouter();

router.push('/dashboard');   // navigate
router.replace('/login');    // replace history
router.back();               // go back
```

---

## 4.2 usePathname()

👉 Returns the **current URL path**

```js id="e8c9vp"
'use client';
import { usePathname } from 'next/navigation';

const pathname = usePathname();

console.log(pathname); // /dashboard
```

👉 Useful for:

* Active links
* Conditional UI

---

## 4.3 useParams()

👉 Used to get **dynamic route parameters**

```bash id="9e4c4v"
app/blog/[id]/page.js
```

```js id="oz1l4r"
import { useParams } from 'next/navigation';

const params = useParams();

console.log(params.id);
```

👉 URL:

```id="0kqszn"
/blog/101 → id = 101
```

---

## 4.4 useSearchParams()

👉 Used to get **query parameters**

```js id="bnxk5w"
'use client';
import { useSearchParams } from 'next/navigation';

const searchParams = useSearchParams();

const page = searchParams.get('page');
```

👉 URL:

```id="a0p3q9"
/products?page=2
```

👉 Output:

```id="8k3w1r"
page = 2
```

---

# 🔥 5. Key Differences Between Hooks

| Hook            | Purpose                          |
| --------------- | -------------------------------- |
| useRouter       | Navigation (push, replace, back) |
| usePathname     | Current path                     |
| useParams       | Dynamic params                   |
| useSearchParams | Query params                     |

---

# 🔥 6. Important Points (Interview Focus)

* `next/navigation` is **App Router only**
* Hooks must be used in **Client Components (`'use client'`)**
* Cleaner and more modular than `next/router`

---

# 🎯 Final Interview Answer (Short)

👉 `next/navigation` is the modern navigation API for App Router.
👉 It replaces `next/router` and provides hooks like:

* `useRouter` → navigation
* `usePathname` → current path
* `useParams` → dynamic params
* `useSearchParams` → query

👉 It is more powerful and optimized for modern Next.js.

---

💡 **Pro Tip:**
Say this 👇
👉 “next/navigation is built for App Router and works with server components, unlike next/router” 🚀
