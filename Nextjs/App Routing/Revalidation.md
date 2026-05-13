# What is Revalidation?

Revalidation Next.js ka feature hai jo:

> cached/static data ko certain time ke baad automatically refresh karta hai.

Simple words mein:

* page fast load hota hai because cached data use hota hai
* but kuch time baad fresh data bhi aa jata hai

---

# Why Revalidation Needed?

Suppose:

* products page hai
* news page hai
* blog page hai

Data frequently update hota hai.

Agar pure static bana diya:

```txt id="jlwmx1"
old data dikhega
```

Agar har request pe fetch kiya:

```txt id="jlwmx2"
slow ho jayega
```

So solution:

# Revalidation 🔥

---

# How Revalidation Works

Example:

```tsx id="jlwmx3"
revalidate: 60
```

Meaning:

* Next.js data cache karega
* 60 seconds tak same cached data serve hoga
* 60 sec ke baad next request pe fresh data fetch hoga
* cache update ho jayega

---

# Basic Example

```tsx id="jlwmx4"
async function getUsers() {

  const res = await fetch(
    "https://api.com/users",
    {
      next: {
        revalidate: 60
      }
    }
  );

  return res.json();
}
```

---

# Meaning

```tsx id="jlwmx5"
revalidate: 60
```

means:

> every 60 seconds fresh data fetch karo

---

# Flow of Revalidation

```txt id="jlwmx6"
1. First request → API fetch
2. Data cached
3. Next requests → cached data
4. After 60 sec → fresh fetch
5. Cache updated
```

---

# Benefits of Revalidation

| Benefit          | Meaning                   |
| ---------------- | ------------------------- |
| Fast Performance | Cached data fast hota     |
| Fresh Data       | Updated data milta        |
| Fewer API Calls  | Har request pe fetch nahi |
| Better SEO       | Server-rendered content   |

---

# Real World Example

## E-commerce Products

```tsx id="jlwmx7"
next: {
  revalidate: 300
}
```

Meaning:

* 5 minutes tak cached products
* uske baad updated products

---

# Difference Between no-store and revalidate

| Feature    | Meaning             |
| ---------- | ------------------- |
| no-store   | Always fresh fetch  |
| revalidate | Some time tak cache |

---

# no-store Example

```tsx id="jlwmx8"
fetch(url, {
  cache: "no-store"
});
```

Every request pe fresh API call.

---

# revalidate Example

```tsx id="jlwmx9"
fetch(url, {
  next: {
    revalidate: 60
  }
});
```

60 sec tak cached response.

---

# Important Interview Point

Revalidation basically:

# ISR (Incremental Static Regeneration)

ka modern App Router version hai.

---

# Page Level Revalidation

You can also do:

```tsx id="jlwmy0"
export const revalidate = 60;
```

---

# Example

```tsx id="jlwmy1"
export const revalidate = 60;

export default async function Page() {

  const res = await fetch(
    "https://api.com/users"
  );

  const data = await res.json();

  return <div>{data.length}</div>;
}
```

---

# Interview Questions

---

# Q1. What is Revalidation?

## Answer

> Revalidation Next.js ka feature hai jo cached/static data ko fixed interval ke baad refresh karta hai taaki fast performance aur fresh data dono mil sake.

---

# Q2. Why use Revalidation?

## Answer

* better performance
* reduced API calls
* updated data
* SEO friendly

---

# Q3. Difference Between SSR and Revalidation?

| SSR                    | Revalidation       |
| ---------------------- | ------------------ |
| Every request pe fetch | Cached data use    |
| Slower                 | Faster             |
| Always fresh           | Periodically fresh |

---

# Q4. Difference Between Cache and Revalidation?

| Cache            | Revalidation        |
| ---------------- | ------------------- |
| Data store karta | Cache refresh karta |

---

# Quick Revision

| Syntax                  | Meaning                 |
| ----------------------- | ----------------------- |
| revalidate: 60          | 60 sec baad refresh     |
| cache: "no-store"       | No caching              |
| export const revalidate | Page-level revalidation |

---

# Most Important Line for Interview

> Revalidation Next.js mein cached data ko fixed interval ke baad automatically refresh karne ke liye use hota hai.
