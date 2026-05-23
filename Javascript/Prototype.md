# Prototypes & Inheritance in JavaScript

# 📌 What is Prototype?

In JavaScript, every object has a hidden property called `[[Prototype]]`.

This prototype is another object from which it can inherit properties and methods.

JavaScript uses prototypes for inheritance.

JavaScript me har object ke paas ek hidden property hoti hai:

```js id="jhd58h"
[[Prototype]]
```

Ye dusre object ko point karti hai.

Prototype ka use:

✅ Properties aur methods inherit karne ke liye hota hai.

---

# 📌 Simple Definition

> Prototype is an object from which other objects inherit properties and methods.

---

# 📌 Real Example

```js id="36d5o5"
const user = {
  greet() {
    console.log("Hello");
  }
};

const obj = {};

obj.__proto__ = user;

obj.greet();
```

---

# 📌 Output

```js id="ohgtkg"
Hello
```

---

# 📌 How It Works?

JavaScript pehle object ke andar property search karta hai.

Agar nahi mili:

✅ Prototype me search karta hai.

---

# 📌 Important Point

Almost everything in JavaScript is object.

Examples:

* Array
* Function
* Object

sab prototype inherit karte hain.

---

# 📌 Prototype Example with Function

```js id="4r3v56"
function Person(name) {
  this.name = name;
}

Person.prototype.sayHi = function() {
  console.log("Hi");
};

const p1 = new Person("Krupa");

p1.sayHi();
```

---

# 📌 Output

```js id="qjlwm6"
Hi
```

---

# 📌 Why Use Prototype?

Agar method constructor ke andar banayenge:

❌ Har object ke liye alag memory lagegi.

Prototype use karne se:

✅ Shared method create hota hai.

Memory optimize hoti hai.

---

# 📌 Prototype Chain

Prototype chain ka matlab:

> Object → prototype → parent prototype → Object.prototype → null

---

# 📌 Example

```js id="jz0p73"
const arr = [1, 2, 3];
```

Internally:

```js id="t8q61o"
arr
 ↓
Array.prototype
 ↓
Object.prototype
 ↓
null
```

---

# 📌 Property Lookup

```js id="ck8ncc"
arr.push()
```

JavaScript search karega:

1. `arr` me
2. `Array.prototype`
3. `Object.prototype`

---

# 📌 Example

```js id="wv8g31"
const obj = {
  name: "Krupa"
};

console.log(obj.toString());
```

---

# 📌 Why Works?

Kyuki:

```js id="bzjlwm"
toString()
```

`Object.prototype` se inherit hota hai.

---

# 📌 Important Prototype Methods

| Method                  | Use                          |
| ----------------------- | ---------------------------- |
| Object.create()         | Create object with prototype |
| hasOwnProperty()        | Own property check           |
| Object.getPrototypeOf() | Get prototype                |
| **proto**               | Access prototype             |

---

# 📌 Object.create Example

```js id="if0d2m"
const animal = {
  sound() {
    console.log("Animal sound");
  }
};

const dog = Object.create(animal);

dog.sound();
```

---

# 📌 Output

```js id="3d4m8u"
Animal sound
```

---

# 📌 Inheritance in JavaScript

Inheritance ka matlab:

> Ek object dusre object ki properties/methods use kar sake.

JavaScript me inheritance:

✅ Prototype ke through hota hai.

---

# 📌 Prototypal Inheritance

JavaScript ka original inheritance model.

Objects directly dusre objects se inherit karte hain.

---

# 📌 Example

```js id="hqjof0"
const parent = {
  greet() {
    console.log("Hello");
  }
};

const child = Object.create(parent);

child.greet();
```

---

# 📌 Output

```js id="q8lm1m"
Hello
```

---

# 📌 Classical Inheritance

Traditional OOP languages:

* Java
* C++
* C#

Classes use karti hain.

---

# 📌 Example

```js id="zz4xko"
class Animal {
  speak() {
    console.log("Animal speaking");
  }
}

class Dog extends Animal {}

const d = new Dog();

d.speak();
```

---

# 📌 Output

```js id="b6c62k"
Animal speaking
```

---

# 📌 Important Point 🔥

JavaScript internally:

✅ Prototype inheritance hi use karta hai.

Even:

```js id="0c7t4n"
class
```

sirf syntactic sugar hai.

---

# 📌 Classical vs Prototypal Inheritance

| Classical Inheritance | Prototypal Inheritance    |
| --------------------- | ------------------------- |
| Based on classes      | Based on objects          |
| Used in Java/C++      | Used in JavaScript        |
| Blueprint concept     | Direct object inheritance |
| `class` keyword       | `Object.create()`         |
| Rigid                 | Flexible                  |

---

# 📌 Interview Important Line

> JavaScript is prototype-based language, not class-based.

---

# 📌 Internal Working

```js id="8zb5m6"
class Dog {}
```

Internally prototype hi create hota hai.

---

# 📌 Example

```js id="hctuj0"
console.log(Dog.prototype);
```

---

# 📌 Output

Prototype object milega.

---

# 📌 Common Interview Questions 🔥

## Q1 → Difference between **proto** and prototype?

| **proto**               | prototype             |
| ----------------------- | --------------------- |
| Actual object reference | Function property     |
| Object me hota hai      | Functions me hota hai |

---

# 📌 Example

```js id="p6jcmv"
function Test() {}

const obj = new Test();

console.log(obj.__proto__);
console.log(Test.prototype);
```

Dono same object ko point karte hain.

---

# 📌 Q2 → Everything in JS inherits from?

```js id="qxdm82"
Object.prototype
```

---

# 📌 Q3 → End of prototype chain?

```js id="ryg6o0"
null
```

---

# 📌 Real Interview Definition

> Prototype is a mechanism in JavaScript through which objects inherit properties and methods from other objects. Prototype chaining allows JavaScript to search for properties through linked prototype objects until the property is found or null is reached.

---

# 📌 Interview Important Points 🔥

| Topic                   | Important       |
| ----------------------- | --------------- |
| JS inheritance          | Prototype based |
| Prototype chain ends at | null            |
| Shared methods          | prototype       |
| class keyword           | syntactic sugar |
| Property lookup         | chain traversal |

---

# 📌 Short Interview Answer

> Prototype is an object in JavaScript used for inheritance. Every object has a hidden reference to another object called its prototype. JavaScript uses prototype chaining to search properties and methods. Unlike classical inheritance, JavaScript mainly uses prototypal inheritance where objects inherit directly from other objects.


# `__proto__` in JavaScript

# 📌 What is `__proto__`?

`__proto__` JavaScript me ek hidden property hoti hai jo:

> Kisi object ke prototype ko point karti hai.

Simple words:

```js id="4kp2gj"
__proto__
```

batata hai object kis object se inherit kar raha hai.

---

# 📌 Simple Definition

> `__proto__` is a reference to the prototype object from which the current object inherits properties and methods.

---

# 📌 Example

```js id="qptv7m"
const user = {
  greet() {
    console.log("Hello");
  }
};

const obj = {
  name: "Krupa"
};

obj.__proto__ = user;

obj.greet();
```

---

# 📌 Output

```js id="1vr9o4"
Hello
```

---

# 📌 How It Works?

JavaScript pehle:

```js id="e6b1zy"
obj
```

me property search karta hai.

Agar nahi milti:

✅ `__proto__` ke andar search karta hai.

---

# 📌 Internal Flow

```js id="nfcjlwm"
obj
 ↓
obj.__proto__
 ↓
Object.prototype
 ↓
null
```

Isko:

# 🔥 Prototype Chain

bolte hain.

---

# 📌 Example

```js id="q8x3ji"
const arr = [1, 2, 3];

console.log(arr.__proto__);
```

---

# 📌 Output

```js id="i2td42"
Array.prototype
```

Kyuki array internally:

```js id="uhwzrf"
Array.prototype
```

se inherit karta hai.

---

# 📌 Another Example

```js id="g76d69"
function Person() {}

const p1 = new Person();

console.log(p1.__proto__);
```

---

# 📌 Output

```js id="q6p0d4"
Person.prototype
```

---

# 📌 Important Relation 🔥

```js id="fr2o3u"
obj.__proto__ === ConstructorFunction.prototype
```

---

# 📌 Example

```js id="a9k6u1"
function Test() {}

const obj = new Test();

console.log(obj.__proto__ === Test.prototype);
```

---

# 📌 Output

```js id="fjq7z2"
true
```

---

# 📌 Difference Between `prototype` and `__proto__`

| prototype                  | **proto**                  |
| -------------------------- | -------------------------- |
| Function property          | Object property            |
| Used to create inheritance | Points to inherited object |
| Available in functions     | Available in objects       |

---

# 📌 Example

```js id="e2y7wg"
function User() {}

const u1 = new User();

console.log(User.prototype);
console.log(u1.__proto__);
```

Both same object ko point karte hain.

---

# 📌 Why `__proto__` Important?

JavaScript inheritance internally:

✅ `__proto__` ke through hota hai.

Methods/property lookup:

```js id="pcjlwm"
prototype chain
```

me hoti hai.

---

# 📌 Example of Property Lookup

```js id="3hpljq"
const animal = {
  eats: true
};

const dog = {
  bark: true
};

dog.__proto__ = animal;

console.log(dog.eats);
```

---

# 📌 Output

```js id="jlwm5w"
true
```

---

# 📌 Why?

Kyuki:

```js id="7vps40"
eats
```

dog me nahi mila.

To JavaScript:

```js id="6ucjlwm"
dog.__proto__
```

me search karega.

---

# 📌 Modern Alternative

Directly:

```js id="ewd1yz"
__proto__
```

use avoid karte hain.

Modern methods:

```js id="4i1r0j"
Object.getPrototypeOf()
Object.setPrototypeOf()
```

---

# 📌 Example

```js id="evw4oc"
Object.getPrototypeOf(obj);
```

---

# 📌 Important Interview Points 🔥

| Topic                   | Important             |
| ----------------------- | --------------------- |
| `__proto__`             | Prototype reference   |
| Used for                | Inheritance           |
| Exists in               | Objects               |
| Prototype chain ends at | null                  |
| Modern alternative      | Object.getPrototypeOf |

---

# 📌 Common Interview Question

## Q → Is `__proto__` same as `prototype`?

❌ No.

* `prototype` → function property
* `__proto__` → object reference

---

# Why Prototype is Important?

Without prototype:

Every object gets separate copy of methods
More memory usage

With prototype:

Methods shared among all objects
Better performance

| Feature   | `__proto__`      | `prototype`                 |
| --------- | ---------------- | --------------------------- |
| Used in   | Objects          | Functions                   |
| Points to | Parent object    | Object used for inheritance |
| Purpose   | Access prototype | Used when creating objects  |


# 📌 Real Interview Definition

> `__proto__` is an internal reference in JavaScript objects that points to the object's prototype, enabling inheritance and prototype chaining.

---

# 📌 Short Interview Answer

> `__proto__` is a hidden property in JavaScript objects that points to the prototype object from which the current object inherits properties and methods. It is used internally for prototype-based inheritance.
