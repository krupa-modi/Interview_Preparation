# 🚀 getStaticProps in Next.js – Complete Interview Guide (VERY IMPORTANT 🔥)

---

# 1. What is `getStaticProps`?

`getStaticProps` is a special function in Next.js used to fetch data at **build time** and generate static pages.

👉 The page is pre-rendered once during build.

---

# 🔥 Simple Definition

👉 “getStaticProps fetches data at build time and creates static HTML pages.”

---

# 2. Why Do We Use `getStaticProps`?

Used when:

* Data does not change frequently
* Want super fast performance
* Need SEO optimization
* Static content is enough

---

# 🔥 Common Use Cases

| Use Case        | Why SSG Needed         |
| --------------- | ---------------------- |
| Blog pages      | Content changes rarely |
| Documentation   | Static content         |
| Portfolio       | Fast loading           |
| Marketing pages | Better SEO + speed     |

---

# 3. Basic Syntax

```js id="x8m2qp"
export async function getStaticProps() {
  return {
    props: {}
  };
}
```

---

# 4. Basic Example

```js id="v4z7tw"
function Home({ users }) {
  return (
    <div>
      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))}
    </div>
  );
}

export async function getStaticProps() {
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

```text id="w2r8qx"
Build Time
    ↓
getStaticProps Runs
    ↓
Data Fetching
    ↓
Static HTML Generated
    ↓
HTML Served to Users
```

---

# 5. Important Point 🔥

👉 `getStaticProps` runs:

* During build time ✅
* NOT on every request ❌

---

# 🔍 Example

```text id="m4v7pz"
npm run build
```

👉 At this time:

* Data fetched
* Static pages generated

---

# 6. Super Important Advantage 🚀

Because page is already generated:

* Faster loading ⚡
* Better SEO ✅
* Less server load ✅

Used when:

* Data changes rarely
* Need very fast performance
* SEO important

---

# 7. Where Can We Use It?

✅ Only inside:

```bash id="t8q2wm"
pages/
```

❌ NOT inside:

```bash id="f7v4nx"
app/
```

👉 App Router uses different data fetching methods.

---

# 8. Return Object Structure

```js id="g3x9pk"
return {
  props: {}
}
```

---

# 🔥 Can Also Return

| Property   | Purpose                |
| ---------- | ---------------------- |
| props      | Pass data to component |
| notFound   | Show 404 page          |
| redirect   | Redirect user          |
| revalidate | ISR support            |

---

# 9. 404 Example

```js id="k2v8rm"
export async function getStaticProps() {
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

---

# 10. Redirect Example

```js id="j9m3xt"
export async function getStaticProps() {
  return {
    redirect: {
      destination: '/login',
      permanent: false,
    },
  };
}
```

---

# 11. Dynamic Routes with getStaticProps 🔥

When using dynamic routes:
👉 Need `getStaticPaths`

---

# 📂 File Structure

```bash id="y7q4zp"
pages/blog/[id].js
```

---

# 🔍 Example

```js id="u3v8tk"
function Blog({ post }) {
  return <h1>{post.title}</h1>;
}

export async function getStaticPaths() {
  return {
    paths: [
      { params: { id: '1' } },
      { params: { id: '2' } },
    ],
    fallback: false,
  };
}

export async function getStaticProps(context) {
  const { id } = context.params;

  const res = await fetch(`https://api.com/posts/${id}`);
  const post = await res.json();

  return {
    props: { post },
  };
}

export default Blog;
```

---

# 12. What is getStaticPaths?

👉 Used with dynamic routes to define:

* Which pages should be generated at build time

---

# 🔥 Example

```js id="z2m9xp"
paths: [
  { params: { id: '1' } },
  { params: { id: '2' } }
]
```

👉 Generates:

```text id="p6w3vt"
/blog/1
/blog/2
```

---

# 13. Fallback Modes (VERY IMPORTANT 🔥)

---

## fallback: false

```js id="e7v2mq"
fallback: false
```

👉 Only generated pages allowed.

Other routes:

```text id="k9m4xr"
404 page
```

---

## fallback: true

👉 Missing pages generated dynamically.

---

## fallback: 'blocking'

👉 User waits until page generated on server.

---

# 14. Incremental Static Regeneration (ISR) 🔥🔥

👉 Allows static pages to update after deployment.

---

# 🔍 Example

```js id="r4x8tp"
export async function getStaticProps() {
  return {
    props: {},
    revalidate: 10,
  };
}
```

👉 Rebuild page every:

```text id="h7v2qn"
10 seconds
```

---

# 🔥 Why ISR Important?

Without ISR:

```text id="d3x9pk"
Need full rebuild for updates
```

With ISR:

```text id="j8v4tm"
Automatic page regeneration
```

---

# 15. SEO Benefits 🔥

👉 Since HTML is already generated:

* Search engines can crawl easily
* Better indexing
* Better performance scores

---

# 16. Performance Advantage

## getStaticProps Pages Are:

* Extremely fast ⚡
* CDN cacheable ✅
* Low server cost ✅

---

# 17. Difference Between SSR vs SSG

| Feature        | getServerSideProps (SSR) | getStaticProps (SSG) |
| -------------- | ------------------------ | -------------------- |
| Runs           | Every request            | Build time           |
| Speed          | Slower                   | Faster               |
| Data Freshness | Real-time                | Static               |
| Server Load    | High                     | Low                  |
| SEO            | Good                     | Excellent            |

---

# 18. Difference Between CSR vs SSG

| Feature     | CSR     | SSG        |
| ----------- | ------- | ---------- |
| Rendering   | Browser | Build time |
| SEO         | Weak    | Strong     |
| Performance | Slower  | Faster     |

---

# 19. Important Rules 🔥

---

## ✅ Must Export

```js id="n6v2qx"
export async function getStaticProps()
```

---

## ✅ Must Return Object

```js id="w3m8tp"
return {
  props: {}
}
```

---

## ❌ Cannot Use in Components

Only inside page files.

---

# 20. Real Interview Questions

---

## ❓ When should we use getStaticProps?

👉 Use when:

* Data changes rarely
* Need high performance
* Need SEO optimization

---

## ❓ Does it run on every request?

❌ No

👉 Only during build time.

---

## ❓ Why is getStaticProps fast?

👉 Because HTML is pre-generated before users request page.

---

## ❓ Can static pages update after deployment?

✅ Yes using ISR (`revalidate`)

---

# 🎯 Final Interview Answer

👉 `getStaticProps` is a static site generation (SSG) method in Next.js that fetches data at build time and pre-renders pages as static HTML.

👉 It is mainly used for:

* Fast performance
* SEO optimization
* Static content websites

👉 It can also support dynamic updates using ISR (`revalidate`).

---

# 💡 MNC Interview Pro Tip

Say this 👇

👉 “getStaticProps generates pages at build time, making applications extremely fast, SEO-friendly, and scalable.” 🚀
