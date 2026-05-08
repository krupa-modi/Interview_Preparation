# 1. What is `getServerSideProps`?

`getServerSideProps` is a special async function in Next.js used to fetch data on the **server side for every request**.

👉 It runs:

* On the server only ✅
* Before page renders ✅
* On every request ✅

---

# 🔥 Simple Definition

👉 “getServerSideProps fetches fresh data from server before rendering the page.”

---

# 2. Why Do We Use `getServerSideProps`?

Used when page needs:

* Real-time data
* Dynamic content
* User-specific data
* Secure server-side fetching

---

# 🔥 Common Use Cases

| Use Case       | Why SSR Needed   |
| -------------- | ---------------- |
| Dashboard      | Fresh user data  |
| Weather App    | Live updates     |
| Stock Market   | Real-time prices |
| Authentication | Secure access    |

---

# 3. Basic Syntax

```js id="z8x2pm"
export async function getServerSideProps(context) {
  return {
    props: {}
  };
}
```

---

# 4. Basic Example

```js id="m3q7tw"
function Home({ users }) {
  return (
    <div>
      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))}
    </div>
  );
}

export async function getServerSideProps() {
  const res = await fetch('https://jsonplaceholder.typicode.com/users');

  const users = await res.json();

  return {
    props: {
      users
    }
  };
}

export default Home;
```

---

# 🔥 Flow of Execution

```text id="w6r2zp"
User Request
     ↓
getServerSideProps Runs
     ↓
Data Fetching
     ↓
Page Rendered on Server
     ↓
HTML Sent to Browser
```

---

# 5. Important Point 🔥

👉 `getServerSideProps` runs on EVERY request.

Example:

```text id="j7m4xv"
Refresh page → API runs again
```

👉 Always fresh data.

---

# 6. Where Can We Use It?

✅ Only inside:

```bash id="t4x8qn"
pages/
```

❌ NOT inside:

```bash id="h2v7pr"
app/
```

👉 Because App Router uses different data fetching methods.

---

# 7. Context Object (VERY IMPORTANT)

`getServerSideProps(context)` receives a context object.

---

# 🔥 Context Properties

| Property | Purpose              |
| -------- | -------------------- |
| params   | Dynamic route params |
| query    | Query params         |
| req      | Request object       |
| res      | Response object      |

---

# 🔍 Example: Access Params

```js id="n9m3qk"
export async function getServerSideProps(context) {
  console.log(context.params.id);

  return {
    props: {}
  };
}
```

---

# 🔍 Example: Access Query

URL:

```text id="g8v2rm"
/products?page=2
```

```js id="f6x4zt"
context.query.page
```

👉 Output:

```text id="p3w9qx"
2
```

---

# 8. Dynamic Routes Example

---

## 📂 File Structure

```bash id="r2m7vq"
pages/blog/[id].js
```

---

## 🔍 Code

```js id="d8x1mp"
function Blog({ post }) {
  return <h1>{post.title}</h1>;
}

export async function getServerSideProps(context) {
  const { id } = context.params;

  const res = await fetch(`https://api.com/posts/${id}`);
  const post = await res.json();

  return {
    props: { post }
  };
}

export default Blog;
```

---

# 9. Redirect using getServerSideProps

```js id="y4z8tn"
export async function getServerSideProps() {
  const isLoggedIn = false;

  if (!isLoggedIn) {
    return {
      redirect: {
        destination: '/login',
        permanent: false,
      },
    };
  }

  return {
    props: {},
  };
}
```

---

# 10. 404 Handling

```js id="u3q7xm"
export async function getServerSideProps() {
  const data = null;

  if (!data) {
    return {
      notFound: true,
    };
  }

  return {
    props: { data },
  };
}
```

👉 Automatically shows 404 page.

---

# 11. SEO Benefits (VERY IMPORTANT)

👉 Since HTML is generated on server:

* Search engines can read content easily
* Better SEO compared to client-side rendering

---

# 🔥 Why SSR Improves SEO?

Without SSR:

```text id="a5m9zr"
Browser gets empty HTML first
```

With SSR:

```text id="x2p8vq"
Browser gets complete HTML
```

👉 Better indexing by Google.

---

# 12. Performance Consideration

## ❌ Disadvantage

Because it runs on every request:

* Slower than static generation
* More server load

---

## ✅ Advantage

Always fresh data.

---

# 13. Difference Between SSR vs CSR

| Feature        | SSR            | CSR             |
| -------------- | -------------- | --------------- |
| Rendering      | Server         | Browser         |
| SEO            | Better ✅       | Poor ❌          |
| First Load     | Faster content | Blank initially |
| Data Freshness | Real-time      | Client fetch    |

---

# 14. Difference Between getServerSideProps vs getStaticProps

| Feature  | getServerSideProps | getStaticProps |
| -------- | ------------------ | -------------- |
| Runs     | Every request      | Build time     |
| Data     | Fresh              | Static         |
| Speed    | Slower             | Faster         |
| Use Case | Dynamic data       | Static pages   |

---

# 15. Important Rules 🔥

---

## ✅ Must Export

```js id="q9x2wm"
export async function getServerSideProps()
```

---

## ✅ Must Return Object

```js id="m7v4zt"
return {
  props: {}
}
```

---

## ❌ Cannot Use in Components

Only allowed in page files.

---

# 16. Real Interview Questions

---

## ❓ When to use getServerSideProps?

👉 Use when:

* Data changes frequently
* Need user-specific data
* Need secure server-side rendering

---

## ❓ Does it run on client side?

❌ No

👉 Runs only on server.

---

## ❓ Is it good for SEO?

✅ Yes

Because HTML is pre-rendered on server.

---

# 🎯 Final Interview Answer

👉 `getServerSideProps` is a server-side data fetching method in Next.js Pages Router that runs on every request before page rendering.

👉 It is used for:

* Dynamic data
* Real-time updates
* Authentication
* SEO-friendly pages

👉 It improves SEO because complete HTML is rendered on server before sending to browser.

---

# 💡 MNC Interview Pro Tip

Say this 👇

👉 “getServerSideProps provides fresh server-rendered data on every request, making it ideal for dynamic and SEO-sensitive applications.” 🚀
