## 1. How to Redirect in App Router?

In the App Router, redirection is handled using the **`redirect()` function** from `next/navigation`.

👉 It allows you to **navigate users programmatically on the server side**

---

### 📌 Example

```js id="z8r2x1"
import { redirect } from 'next/navigation';

export default function Page() {
  const isLoggedIn = false;

  if (!isLoggedIn) {
    redirect('/login');
  }

  return <h1>Dashboard</h1>;
}
```

👉 If condition fails → user is redirected to `/login`

---

## 2. What is `redirect()`?

`redirect()` is a function used to **redirect users to another route instantly**.

👉 Key Points:

* Works in **Server Components**
* Stops execution immediately
* Performs **server-side redirect**
* No need for `useRouter`

---

### 🔥 Behind the Scenes

👉 When `redirect()` is called:

* It throws a special error internally
* Next.js catches it and performs redirect

---

### 📌 Use Cases

* Authentication (redirect to login)
* Role-based access control
* Conditional navigation

---

## 3. Redirect in Client Component (Alternative)

```js id="a2k9m0"
'use client';
import { useRouter } from 'next/navigation';

const router = useRouter();

router.push('/login');
```

👉 Used for **client-side navigation**

---

# ❌ 4. What is `notFound()`?

`notFound()` is used to **show a 404 page when data or route is not found**

---

### 📌 Example

```js id="l1p9z3"
import { notFound } from 'next/navigation';

export default async function Page({ params }) {
  const data = await getData(params.id);

  if (!data) {
    notFound();
  }

  return <div>{data.name}</div>;
}
```

---

## 🔥 How it Works

👉 When `notFound()` is called:

* Stops execution
* Shows `not-found.tsx` UI
* Returns 404 status

---

### 📂 Example Structure

```bash id="n7r3xp"
app/
 ├── not-found.tsx
 ├── blog/
 │    ├── [id]/
 │    │     ├── page.tsx
```

---

### 🔍 not-found.tsx Example

```jsx id="v4m2q7"
export default function NotFound() {
  return <h1>404 - Page Not Found</h1>;
}
```

---

# 🔥 5. redirect() vs notFound()

| Feature         | redirect()                    | notFound()    |
| --------------- | ----------------------------- | ------------- |
| Purpose         | Navigate to another page      | Show 404 page |
| Use Case        | Auth, condition-based routing | Missing data  |
| Status Code     | 3xx                           | 404           |
| Stops Execution | ✅ Yes                         | ✅ Yes         |

---

# 🎯 Final Interview Answer (Short)

👉 `redirect()` is used to navigate users to another route (server-side).
👉 `notFound()` is used to display a 404 page when data or route doesn’t exist.

👉 Both stop execution and are part of `next/navigation`.

---

💡 **Pro Tip:**
Say this 👇
👉 “redirect handles navigation, notFound handles missing resources” 🚀
