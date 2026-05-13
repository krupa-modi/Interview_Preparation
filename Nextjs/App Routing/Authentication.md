# 1. What is Authentication?

Authentication means verifying:
👉 “Who is the user?”

It checks whether:

* User is logged in
* User is valid
* User can access protected resources

---

# 🔥 Real Example

```text
Email + Password
       ↓
Server verifies credentials
       ↓
User authenticated ✅
```

---

# 🔥 Common Authentication Types

| Type          | Example                 |
| ------------- | ----------------------- |
| JWT           | Token-based auth        |
| Session       | Cookie/session auth     |
| OAuth         | Google login            |
| Firebase Auth | Firebase authentication |

---

# 2. JWT Authentication 🔥🔥

---

# 👉 What is JWT?

JWT = JSON Web Token

👉 After successful login:

* Server creates token
* Token sent to client
* Client stores token

---

# 🔥 JWT Flow

```text
Login
   ↓
Server validates user
   ↓
JWT token generated
   ↓
Client stores token
   ↓
Token sent in future requests
```

---

# 🔍 JWT Example

```text
Authorization: Bearer token123
```

---

# 🔥 JWT Storage

Usually stored in:

* Cookies
* localStorage
* sessionStorage

---

# 🔥 JWT Advantages

| Advantage    | Explanation                  |
| ------------ | ---------------------------- |
| Stateless    | No session storage needed    |
| Scalable     | Good for distributed systems |
| API Friendly | Works well with mobile apps  |

---

# ❌ JWT Disadvantages

* Hard to invalidate
* Token theft risk
* Security handling important

---

# 🔍 JWT Login Example (Next.js API Route)

```js
import jwt from 'jsonwebtoken';

export default function handler(req, res) {
  const token = jwt.sign(
    { email: "test@gmail.com" },
    "secretKey"
  );

  res.status(200).json({ token });
}
```

---

# 3. Session Authentication 🔥🔥

---

# 👉 What is Session Authentication?

In session auth:
👉 Server stores session data.

Client stores only:

```text
Session ID
```

inside cookie.

---

# 🔥 Session Flow

```text
Login
   ↓
Server creates session
   ↓
Session ID stored in cookie
   ↓
Future requests use session ID
```

---

# 🔥 Session Advantages

| Advantage     | Explanation              |
| ------------- | ------------------------ |
| Easier logout | Session can be destroyed |
| More secure   | Data stored on server    |

---

# ❌ Session Disadvantages

* Uses server memory
* Harder to scale

---

# 🔍 Session Example

```js
req.session.user = {
  name: "Krupa"
};
```

---

# 4. JWT vs Session 🔥🔥🔥

| Feature         | JWT         | Session              |
| --------------- | ----------- | -------------------- |
| Storage         | Client side | Server side          |
| Scalability     | High        | Medium               |
| Logout Handling | Difficult   | Easy                 |
| Performance     | Faster      | Slightly slower      |
| Security        | Token-based | Cookie/session-based |

---

# 🔥 Important Interview Point

👉 JWT is stateless.
👉 Session is stateful.

---

# 🎯 Interview Answer

👉 JWT stores authentication data in token form on client side, while Session stores user data on server side and uses session ID in cookies.

---

# 5. Protected Routes 🔥🔥

---

# 👉 What are Protected Routes?

Protected routes are pages accessible only to authenticated users.

---

# 🔥 Example

```text
/dashboard
/profile
/admin
```

👉 If user not logged in:

```text
Redirect to /login
```

---

# 🔍 Example Using useEffect

```jsx
'use client';

import { useRouter } from 'next/navigation';
import { useEffect } from 'react';

export default function Dashboard() {
  const router = useRouter();

  useEffect(() => {
    const token = localStorage.getItem('token');

    if (!token) {
      router.push('/login');
    }
  }, []);

  return <h1>Dashboard</h1>;
}
```

---

# 🔥 Flow

```text
User visits protected page
        ↓
Check auth/token
        ↓
If invalid → redirect login
```

---

# 🔥 Why Important?

* Prevent unauthorized access
* Secure private pages

---

# 🎯 Interview Answer

👉 Protected routes restrict access to authenticated users and redirect unauthorized users to login page.

---

# 6. Middleware Authentication 🔥🔥🔥

---

# 👉 What is Middleware Auth?

Middleware checks authentication BEFORE route/page loads.

👉 Runs at edge/server level.

---

# 🔍 middleware.js Example

```js
import { NextResponse } from 'next/server';

export function middleware(req) {
  const token = req.cookies.get('token');

  if (!token) {
    return NextResponse.redirect(
      new URL('/login', req.url)
    );
  }
}
```

---

# 🔥 Flow

```text
Request
   ↓
Middleware runs
   ↓
Check token
   ↓
Allow OR redirect
```

---

# 🔥 Benefits

| Benefit          | Explanation          |
| ---------------- | -------------------- |
| Better security  | Blocks before render |
| Faster redirects | Edge execution       |
| Centralized auth | Single auth logic    |

---

# 🔥 Protect Specific Routes

```js
export const config = {
  matcher: ['/dashboard/:path*'],
};
```

---

# 🎯 Interview Answer

👉 Middleware authentication validates users before route rendering and redirects unauthorized users early.

---

# 7. Login Flow in Next.js 🔥🔥🔥

---

# 👉 Complete Login Flow

```text
User enters email/password
          ↓
Frontend sends request
          ↓
Server validates credentials
          ↓
JWT/session created
          ↓
Stored in cookie/localStorage
          ↓
Protected routes verify auth
```

---

# 🔍 Frontend Login Example

```js
const handleLogin = async () => {
  const res = await fetch('/api/login', {
    method: 'POST',
    body: JSON.stringify({
      email,
      password
    }),
  });

  const data = await res.json();

  localStorage.setItem('token', data.token);
};
```

---

# 🔍 Backend Login Example

```js
export default function handler(req, res) {
  const { email, password } = req.body;

  if (email === 'test@gmail.com' && password === '123') {
    return res.status(200).json({
      token: 'jwt-token'
    });
  }

  res.status(401).json({
    message: 'Invalid credentials'
  });
}
```

---

# 8. Authentication in App Router 🔥

---

# 👉 Recommended Modern Approach

Use:

* Middleware
* Server Actions
* Cookies
* NextAuth/Auth.js

---

# 🔥 Cookie Example

```js
import { cookies } from 'next/headers';

cookies().set('token', 'abc123');
```

---

# 9. Best Authentication Library 🔥

Popular libraries:

* NextAuth/Auth.js
* Clerk
* Firebase Auth
* Auth0

---

# 🔥 Most Popular

```text
NextAuth / Auth.js
```

---

# 10. Real Interview Questions 🔥

---

## ❓ Which is better JWT or Session?

👉 Depends on use case:

* JWT → scalable apps/APIs
* Session → traditional secure apps

---

## ❓ Why middleware better for auth?

👉 Because auth check happens before rendering.

---

## ❓ Can Next.js handle full authentication?

✅ Yes

Using:

* API Routes
* Middleware
* Cookies
* NextAuth

---

## ❓ What is protected route?

👉 Route accessible only after authentication.

---

# 🎯 Final Interview Summary

👉 Authentication verifies user identity.
👉 JWT stores auth data in token form.
👉 Session stores auth data on server.
👉 Protected routes block unauthorized users.
👉 Middleware authentication checks auth before rendering.
👉 Login flow includes validation, token/session creation, and route protection.

---

# 💡 MNC Interview Pro Tip

Say this 👇

👉 “Next.js authentication is commonly implemented using JWT/session-based auth with middleware-protected routes for secure and scalable applications.” 🚀
