# JavaScript Array Methods – Interview Quick Revision


# Array Access in JavaScript

# 1. Normal Array Access

```js
let arr = [10, 20, 30, 40];
````

## Access Value

```js
console.log(arr[0]); // 10
console.log(arr[1]); // 20
console.log(arr[2]); // 30
```

👉 Index always starts from `0`

| Index | Value |
| ----- | ----- |
| 0     | 10    |
| 1     | 20    |
| 2     | 30    |
| 3     | 40    |

---

# Add Value in Normal Array

## Add at Last

```js
arr[4] = 50;

console.log(arr);
// [10, 20, 30, 40, 50]
```

---

# Change Value in Normal Array

```js
arr[1] = 200;

console.log(arr);
// [10, 200, 30, 40]
```

---

# 2. Nested Array Access

```js
let nestedArr = [ [1, 2],[3, 4],[5, 6]];
```

## Access Nested Array Value

```js
console.log(nestedArr[0]); 
// [1, 2]
```

```js
console.log(nestedArr[0][0]); 
// 1
```

```js
console.log(nestedArr[0][1]); 
// 2
```

```js
console.log(nestedArr[1][0]); 
// 3
```

```js
console.log(nestedArr[2][1]); 
// 6
```

# Add Value in Nested Array

```js
nestedArr[0][2] = 100;

console.log(nestedArr);
// [ [1, 2, 100], [3, 4], [5, 6] ]
```

---

# Change Value in Nested Array

```js
nestedArr[1][1] = 400;

console.log(nestedArr);
// [ [1, 2], [3, 400], [5, 6] ]
```

## 1. push()

**Definition:** Array ke end me element add karta hai.

```js
let arr = [1, 2];
arr.push(3);

console.log(arr); // [1,2,3]
```

---

## 2. pop()

**Definition:** Last element remove karta hai.

```js
let arr = [1,2,3];
arr.pop();

console.log(arr); // [1,2]
```

---

## 3. unshift()

**Definition:** Starting me element add karta hai.

```js
let arr = [2,3];
arr.unshift(1);

console.log(arr); // [1,2,3]
```

---

## 4. shift()

**Definition:** First element remove karta hai.

```js
let arr = [1,2,3];
arr.shift();

console.log(arr); // [2,3]
```

---

# 5. concat()

**Definition:** Do ya jyada arrays ko merge karta hai.

```js
let a = [1,2];
let b = [3,4];

console.log(a.concat(b)); // [1,2,3,4]
```

---

# 6. join()

**Definition:** Array ko string me convert karta hai.

```js
let arr = ["hello", "world"];

console.log(arr.join(" ")); // hello world
```

---

# 7. slice()

**Definition:** Array ka copy part return karta hai.

```js
let arr = [1,2,3,4];

console.log(arr.slice(1,3)); // [2,3]
```

---

# 8. splice()

**Definition:** Add, remove ya replace karta hai.

```js
let arr = [1,2,3];

arr.splice(1,1,"hello");

console.log(arr); // [1,"hello",3]
```

---

# 9. includes()

**Definition:** Check karta hai value present hai ya nahi.

```js
let arr = [1,2,3];

console.log(arr.includes(2)); // true
```

---

# 10. indexOf()

**Definition:** Element ka first index return karta hai.

```js
let arr = [10,20,30];

console.log(arr.indexOf(20)); // 1
```

---

# 11. lastIndexOf()

**Definition:** Last occurrence ka index deta hai.

```js
let arr = [1,2,1,3];

console.log(arr.lastIndexOf(1)); // 2
```

---

# 12. reverse()

**Definition:** Array reverse karta hai.

```js
let arr = [1,2,3];

console.log(arr.reverse()); // [3,2,1]
```

---

# 13. sort()

**Definition:** Array ko sort karta hai.

```js
let arr = [5,2,1];

arr.sort((a,b)=>a-b);

console.log(arr); // [1,2,5]
```

---

# 14. at()

**Definition:** Specific index ki value deta hai.

```js
let arr = [10,20,30];

console.log(arr.at(-1)); // 30
```

---

# 15. flat()

**Definition:** Nested array ko flat karta hai.

```js
let arr = [1,[2,[3]]];

console.log(arr.flat(2)); // [1,2,3]
```

---

# 16. flatMap()

**Definition:** map + flat dono ek sath.

```js
let arr = [1,2,3];

console.log(arr.flatMap(x => [x,x*2]));
```

---

# 17. fill()

**Definition:** Array ko ek value se fill karta hai.

```js
let arr = [1,2,3];

arr.fill(0);

console.log(arr); // [0,0,0]
```

---

# 18. copyWithin()

**Definition:** Array ke andar values copy karta hai.

```js
let arr = [1,2,3,4];

arr.copyWithin(1,2);

console.log(arr); // [1,3,4,4]
```

---

# 19. find()

**Definition:** First matching value return karta hai.

```js
let arr = [1,2,3,4];

console.log(arr.find(x => x > 2)); // 3
```

---

# 20. findIndex()

**Definition:** Matching element ka index deta hai.

```js
let arr = [10,20,30];

console.log(arr.findIndex(x => x === 20)); // 1
```

---

# 21. findLast()

**Definition:** Last matching value return karta hai.

```js
let arr = [1,2,3,4];

console.log(arr.findLast(x => x > 2)); // 4
```

---

# 22. findLastIndex()

**Definition:** Last matching index return karta hai.

```js
let arr = [1,2,3,4];

console.log(arr.findLastIndex(x => x > 2)); // 3
```

---

# 23. forEach()

**Definition:** Har element pe loop chalata hai.

```js
let arr = [1,2,3];

arr.forEach(x => console.log(x));
```

---

# 24. map()

**Definition:** Naya transformed array return karta hai.

```js
let arr = [1,2,3];

let result = arr.map(x => x * 2);

console.log(result); // [2,4,6]
```

---

# 25. filter()

**Definition:** Condition true wale elements return karta hai.

```js
let arr = [1,2,3,4];

console.log(arr.filter(x => x % 2 === 0)); // [2,4]
```

---

# 26. reduce()

**Definition:** Array ko single value me convert karta hai.

```js
let arr = [1,2,3];

let sum = arr.reduce((acc,curr)=>acc+curr,0);

console.log(sum); // 6
```

---

# 27. reduceRight()

**Definition:** Right to left reduce karta hai.

```js
let arr = ["H","e","y"];

console.log(arr.reduceRight((a,b)=>a+b)); // yeH
```

---

# 28. some()

**Definition:** Ek bhi condition true ho to true return.

```js
let arr = [1,2,3];

console.log(arr.some(x => x > 2)); // true
```

---

# 29. every()

**Definition:** Sab elements condition satisfy kare to true.

```js
let arr = [2,4,6];

console.log(arr.every(x => x % 2 === 0)); // true
```

---

# 30. entries()

**Definition:** Index + value pair deta hai.

```js
let arr = ["a","b"];

for(let [i,v] of arr.entries()){
  console.log(i,v);
}
```

---

# 31. keys()

**Definition:** Sirf indexes return karta hai.

```js
let arr = ["a","b"];

console.log([...arr.keys()]); // [0,1]
```

---

# 32. values()

**Definition:** Sirf values return karta hai.

```js
let arr = ["a","b"];

console.log([...arr.values()]);
```

---

# 33. Array.isArray()

**Definition:** Check karta hai array hai ya nahi.

```js
console.log(Array.isArray([1,2])); // true
```

---

# 34. Array.from()

**Definition:** Array-like ko array banata hai.

```js
console.log(Array.from("hello"));
```

---

# 35. Array.of()

**Definition:** Values se naya array banata hai.

```js
console.log(Array.of(1,2,3));
```

---

# 36. toString()

**Definition:** Array ko string me convert karta hai.

```js
let arr = [1,2,3];

console.log(arr.toString()); // "1,2,3"
```

---

# 37. toLocaleString()

**Definition:** Local format me string return karta hai.

```js
let arr = [1000,2000];

console.log(arr.toLocaleString());
```

---

# 38. toReversed()

**Definition:** Original array change bina reverse karta hai.

```js
let arr = [1,2,3];

console.log(arr.toReversed());
```

---

# 39. toSorted()

**Definition:** Original change bina sort karta hai.

```js
let arr = [3,1,2];

console.log(arr.toSorted());
```

---

# 40. toSpliced()

**Definition:** Original change bina splice karta hai.

```js
let arr = [1,2,3];

console.log(arr.toSpliced(1,1));
```

---

# 41. with()

**Definition:** Specific index ki value replace karta hai.

```js
let arr = [1,2,3];

console.log(arr.with(1,100)); // [1,100,3]
```

---

# 42. length

**Definition:** Array ki length batata hai.

```js
let arr = [1,2,3];

console.log(arr.length); // 3
```

---

# Most Important Interview Methods ⭐

## Bahot jyada puchte hai:

* map()
* filter()
* reduce()
* find()
* some()
* every()
* splice()
* slice()
* push()
* pop()
* sort()
* forEach()

---

# map vs forEach

| map                         | forEach                |
| --------------------------- | ---------------------- |
| Naya array return karta hai | Kuch return nahi karta |
| Transformation ke liye      | Loop ke liye           |
| Chain ho sakta hai          | Chain nahi hota        |

---

# slice vs splice

| slice                | splice                |
| -------------------- | --------------------- |
| Original change nahi | Original change karta |
| Copy return karta    | Add/remove karta      |
| Non-destructive      | Destructive           |

---

# find vs filter

| find             | filter            |
| ---------------- | ----------------- |
| First match deta | Sare matches deta |
| Single value     | Array return      |

---

# some vs every

| some               | every                 |
| ------------------ | --------------------- |
| Ek bhi true → true | Sab true hone chahiye |

---

# Important Interview Note ⭐

## Mutable Methods (Original Array Change)

* push
* pop
* shift
* unshift
* splice
* sort
* reverse
* fill

---

## Immutable Methods (Original Change Nahi)

* map
* filter
* slice
* concat
* reduce
* find
* some
* every
