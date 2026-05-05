
## 1. What are Route Groups?

Route Groups are a feature in the **App Router (`/app`)** that let you **organize routes into folders without affecting the URL**.

👉 Created using parentheses:

```bash
(folderName)
```

**Example:**

```bash
app/
 ├── (auth)/
 │    ├── login/page.js
 │    ├── register/page.js
 ├── (dashboard)/
 │    ├── home/page.js
```

👉 URLs:

```bash
/login
/register
/home
```

❗ Notice: `(auth)` and `(dashboard)` **do not appear in URL**

---

## 2. Why use Route Groups?

👉 Main reasons:

* 📁 Organize large applications
* 🎯 Apply different layouts to different sections
* 🧠 Improve code readability
* 🔄 Separate concerns (auth vs main app)

👉 Without route groups, everything stays in one structure → messy

---

## 3. Do Route Groups affect URL?

❌ No, they do NOT affect the URL.

👉 They are only for **internal folder organization**

**Example:**

```bash
app/(auth)/login/page.js → /login
```

👉 `(auth)` is ignored in the URL

---

# 🔥 4. Use Case: Auth Layout Separation (Very Important)

## 🎯 Problem:

You want:

* Auth pages (login/register) → simple layout ❌ navbar
* Dashboard pages → full layout ✅ navbar/sidebar

---

## ✅ Solution using Route Groups

```bash
app/
 ├── (auth)/
 │    ├── layout.js
 │    ├── login/page.js
 │    ├── register/page.js
 │
 ├── (dashboard)/
 │    ├── layout.js
 │    ├── home/page.js
 │    ├── profile/page.js
```

---

## 🔹 Auth Layout Example

```js
// app/(auth)/layout.js
export default function AuthLayout({ children }) {
  return (
    <div>
      <h2>Auth Page</h2>
      {children}
    </div>
  );
}
```

👉 Applies only to:

* `/login`
* `/register`

---

## 🔹 Dashboard Layout Example

```js
// app/(dashboard)/layout.js
export default function DashboardLayout({ children }) {
  return (
    <div>
      <nav>Navbar</nav>
      {children}
    </div>
  );
}
```

👉 Applies to:

* `/home`
* `/profile`

---

# 🔥 5. Key Points (Interview Focus)

* Route Groups = `(folder)`
* Used for **organization + layout separation**
* Do NOT affect URL ❌
* Very useful in **large-scale apps**

---

# 🎯 Final Interview Answer (Short)

👉 Route Groups are used in App Router to organize routes and apply different layouts **without affecting the URL**.
👉 They are helpful for separating sections like **auth and dashboard**.

