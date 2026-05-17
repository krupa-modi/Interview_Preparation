# ✅ Group By Key in JavaScript (Easy Interview Explanation)

# 🔥 What is Group By Key?

Group By means:
👉 **same key/value wale objects ko ek group me rakhna**

Mostly arrays of objects me use hota hai.

---

# ✅ Example Problem

Suppose:

```js id="frg6cg"
const users = [
  { name: "Aman", city: "Pune" },
  { name: "Rahul", city: "Mumbai" },
  { name: "Neha", city: "Pune" },
  { name: "Ankit", city: "Delhi" }
];
````

Ab hume `city` ke basis par group karna hai.

---

# ✅ Expected Output

```js id="v6s9uk"
{
  Pune: [
    { name: "Aman", city: "Pune" },
    { name: "Neha", city: "Pune" }
  ],

  Mumbai: [
    { name: "Rahul", city: "Mumbai" }
  ],

  Delhi: [
    { name: "Ankit", city: "Delhi" }
  ]
}
```

---

# 🚀 Most Common Interview Solution (Using reduce)

```js id="8px7un"
const users = [
  { name: "Aman", city: "Pune" },
  { name: "Rahul", city: "Mumbai" },
  { name: "Neha", city: "Pune" },
  { name: "Ankit", city: "Delhi" }
];

const grouped = users.reduce((acc, curr) => {

  // agar city ka group nahi hai to empty array banao
  if (!acc[curr.city]) {
    acc[curr.city] = [];
  }

  // current object push karo
  acc[curr.city].push(curr);

  return acc;

}, {});

console.log(grouped);
```

---

# 🔍 Easy Explanation

## `acc`

Accumulator object hai
Isme final grouped data store hota hai.

---

## `curr`

Current object.

```js id="2a1r9z"
{ name: "Aman", city: "Pune" }
```

---

## Step-by-Step

### First Iteration

```js id="lm4a4m"
acc = {}
curr.city = "Pune"
```

Pune key nahi hai → array banao

```js id="8y8jya"
acc = {
  Pune: []
}
```

Then push object

```js id="sl08rw"
acc = {
  Pune: [
    { name: "Aman", city: "Pune" }
  ]
}
```

---

# 🎯 Interview Definition

> Group By Key ka matlab hota hai same property/value wale objects ko ek group me organize karna.

Mostly `reduce()` se implement kiya jata hai.

---

# ⚡ Short Interview Answer

```js id="6z1n0q"
Array ko kisi specific property ke basis par
multiple groups me divide karna = Group By
```

---

# 🔥 One-Line Modern Method (ES2024)

```js id="4h7y34"
Object,groupBy(users,()=>...)// 2 parameter 1st jo array of object hai wo and 2nd callback function
Object.groupBy(users, user => user.city);
```

---

# ⚠️ Important Note

`Object.groupBy()` new feature hai
Har browser me support nahi hota.

Interview me mostly `reduce()` wala answer dena best hai.

---

# 🚀 Real Interview Questions

## Q1:

Group employees by department

## Q2:

Group products by category

## Q3:

Group students by class

👉 Sabka logic same rahega.

---

# 💡 Quick Revision

| Concept          | Meaning                           |
| ---------------- | --------------------------------- |
| Group By         | Same values ko ek group me rakhna |
| Mostly Used With | Array of Objects                  |
| Best Method      | reduce()                          |
| Output           | Object                            |

