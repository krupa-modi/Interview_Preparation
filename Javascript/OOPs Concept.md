# What is OOPs?

OOPs means **Object Oriented Programming System**.

JavaScript me OOPs ka use code ko:
* reusable banane ke liye
* organized rakhne ke liye
* real world objects ko represent karne ke liye hota hai.

Example:

* Car
* User
* Bank Account
* Employee

Ye sab objects ki tarah behave karte hai.

---

# Main OOPs Concepts

1. Object
2. Class
3. Constructor
4. this keyword
5. Encapsulation
6. Inheritance
7. super keyword
8. Polymorphism
9. Abstraction
10. Prototype

---

# 1. Object

Object ek collection hota hai:

* properties
* methods

## Example

```js
const user = {
  name: "Krupa",
  age: 25,

  greet() {
    console.log("Hello");
  }
};

console.log(user.name);
user.greet();
```

---

# Real Interview Definition

> Object is a collection of key-value pairs where properties store data and methods store functionality.

---

# 2. Class

Class ek blueprint hoti hai object banane ke liye.

## Example

```js
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello ${this.name}`);
  }
}

const user1 = new User("Krupa", 25);

user1.greet();
```

---

# Interview Definition

> Class is a template used to create objects.

---

# 3. Constructor

Constructor ek special method hota hai:

* automatically call hota hai
* jab new object create hota hai

## Syntax

```js
constructor() {}
```

---

## Example

```js
class Student {
  constructor(name) {
    this.name = name;
  }
}

const s1 = new Student("Rahul");

console.log(s1.name);
```

---

# Important Points

* constructor ka naam fixed hota hai
* ek class me sirf ek constructor hota hai
* object create hote hi execute hota hai

---

# Interview Question

## Q. Constructor ka use kya hai?

> Constructor ka use object initialization ke liye hota hai.

---

# 4. this Keyword

`this` current object ko refer karta hai.

## Example

```js
class Employee {
  constructor(name) {
    this.name = name;
  }

  show() {
    console.log(this.name);
  }
}

const emp = new Employee("Aman");

emp.show();
```

---

# Important

## Normal Function

```js
function test() {
  console.log(this);
}
```

* Browser me global object ko point karta hai.

---

## Arrow Function

Arrow function apna this nahi banata.

Wo parent ka this use karta hai.

```js
const obj = {
  name: "Krupa",

  show: () => {
    console.log(this);
  }
};

obj.show();
```

---

# Interview Definition

> this keyword refers to the object that is executing the current function.

---

# 5. Encapsulation

Data ko secure karna aur direct access ko control karna.

JavaScript me:

* private fields
* getters/setters

use karke encapsulation achieve karte hai.

---

## Example

```js
class Bank {
  #balance = 1000;

  getBalance() {
    return this.#balance;
  }
}

const b1 = new Bank();

console.log(b1.getBalance());
```

---

# Important

```js
console.log(b1.#balance);
```

❌ Error aayega because private field hai.

---

# Interview Definition

> Encapsulation means wrapping data and methods into a single unit and restricting direct access to data.

---

# 6. Inheritance

Ek class dusri class ki properties aur methods inherit kar sakti hai.

`extends` keyword use hota hai.

---

## Example

```js
class Animal {
  sound() {
    console.log("Animal Sound");
  }
}

class Dog extends Animal {
  bark() {
    console.log("Dog Bark");
  }
}

const d1 = new Dog();

d1.sound();
d1.bark();
```

---

# Benefits

* code reuse
* less duplication
* cleaner code

---

# Interview Definition

> Inheritance allows one class to acquire properties and methods of another class.

---

# 7. super Keyword

Parent class ko access karne ke liye use hota hai.

---

# Example 1 → Parent Constructor Call

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);

    this.breed = breed;
  }
}

const d1 = new Dog("Tommy", "Labrador");

console.log(d1);
```

---

# Example 2 → Parent Method Call

```js
class Animal {
  speak() {
    console.log("Animal speaking");
  }
}

class Dog extends Animal {
  speak() {
    super.speak();

    console.log("Dog barking");
  }
}

const d1 = new Dog();

d1.speak();
```

---

# Important

## super() must be called before using this

```js
class Child extends Parent {
  constructor() {
    super();

    this.name = "Krupa";
  }
}
```

---

# Interview Definition

> super keyword is used to access parent class constructor and methods.

---

# 8. Polymorphism

Same method different behavior show kare.

---

## Example

```js
class Animal {
  sound() {
    console.log("Animal sound");
  }
}

class Dog extends Animal {
  sound() {
    console.log("Dog bark");
  }
}

class Cat extends Animal {
  sound() {
    console.log("Cat meow");
  }
}

const d = new Dog();
const c = new Cat();

d.sound();
c.sound();
```

---

# Output

```js
Dog bark
Cat meow
```

---

# Interview Definition

> Polymorphism means one method can perform different actions based on the object.

---

# 9. Abstraction

Important details show karna aur internal implementation hide karna.

JavaScript me fully abstract class nahi hoti like Java.

Hum abstraction:

* methods
* private fields
* interfaces pattern

se achieve karte hai.

---

## Example

```js
class Car {
  start() {
    this.#engine();
  }

  #engine() {
    console.log("Engine Started");
  }
}

const c1 = new Car();

c1.start();
```

---

# Interview Definition

> Abstraction means hiding implementation details and showing only essential features.

---

# 10. Prototype

JavaScript prototype-based language hai.

Har object ek prototype inherit karta hai.

---

## Example

```js
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function () {
  console.log("Hello");
};

const p1 = new Person("Krupa");

p1.greet();
```

---

# Important

* methods prototype me store hote hai
* memory optimize hoti hai

---

# Interview Definition

> Prototype is a mechanism through which objects inherit properties and methods.

---

# Difference Between Class and Object

| Class                  | Object             |
| ---------------------- | ------------------ |
| Blueprint              | Real instance      |
| Logical entity         | Physical entity    |
| Used to create objects | Created from class |

---

# Difference Between Inheritance and Encapsulation

| Inheritance           | Encapsulation  |
| --------------------- | -------------- |
| Code reuse            | Data hiding    |
| extends keyword       | private fields |
| Parent-child relation | Security       |

---

# Frequently Asked Interview Questions

---

# Q1. What is OOPs?

> OOPs is a programming paradigm based on objects and classes.

---

# Q2. Difference between class and object?

> Class is a blueprint, object is an instance of a class.

---

# Q3. Why use constructor?

> Constructor is used to initialize object properties automatically.

---

# Q4. What is inheritance?

> Inheritance allows child class to use parent class properties and methods.

---

# Q5. Why use super keyword?

> super is used to access parent class constructor and methods.

---

# Q6. What is polymorphism?

> Same method behaving differently in different classes.

---

# Q7. What is encapsulation?

> Restricting direct access to data.

---

# Q8. What is abstraction?

> Hiding internal implementation and showing only important details.

---

# Q9. What is prototype in JavaScript?

> Prototype is a mechanism for inheritance in JavaScript.

---

# Q10. Difference between function constructor and class?

| Function Constructor    | Class          |
| ----------------------- | -------------- |
| Old way                 | Modern ES6     |
| Uses prototype manually | Cleaner syntax |
| Less readable           | More readable  |

---

# Function Constructor Example

```js
function User(name) {
  this.name = name;
}

User.prototype.greet = function () {
  console.log("Hello");
};

const u1 = new User("Krupa");

u1.greet();
```

---

# ES6 Class Example

```js
class User {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log("Hello");
  }
}
```

---

# Complete Real Life Example

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  introduce() {
    console.log(`I am ${this.name}`);
  }
}

class Employee extends Person {
  constructor(name, age, company) {
    super(name, age);

    this.company = company;
  }

  work() {
    console.log(`${this.name} works at ${this.company}`);
  }
}

const emp1 = new Employee(
  "Krupa",
  25,
  "Google"
);

emp1.introduce();
emp1.work();
```

---

# Most Important Interview Tips

## Remember These Keywords

```js
class
constructor
this
extends
super
prototype
new
```

---

# Important ES6 OOPs Keywords

| Keyword     | Use               |
| ----------- | ----------------- |
| class       | Create class      |
| constructor | Initialize object |
| this        | Current object    |
| extends     | Inheritance       |
| super       | Parent access     |
| new         | Create object     |

---

# Final Short Revision

| Concept       | Meaning                        |
| ------------- | ------------------------------ |
| Object        | Real entity                    |
| Class         | Blueprint                      |
| Constructor   | Initialize object              |
| this          | Current object                 |
| Inheritance   | Reuse code                     |
| super         | Parent access                  |
| Encapsulation | Data hiding                    |
| Polymorphism  | Same method different behavior |
| Abstraction   | Hide complexity                |
| Prototype     | Inheritance system             |

---

# Best Interview Line

> JavaScript follows prototype-based OOPs, and with ES6 classes it provides cleaner syntax for object-oriented programming concepts like inheritance, encapsulation, abstraction, and polymorphism.


# What Happens If Constructor Is Not Used in a Class?

In JavaScript, if we do not create a constructor inside a class, JavaScript automatically creates a default empty constructor.

Object creation still works, but values are not initialized automatically.

---

# Example Without Constructor

```js
class Person {
  greet() {
    console.log("Hello");
  }
}

const p1 = new Person();

p1.greet();
```

## Output

```js
Hello
```

---

# Internally JavaScript Creates Default Constructor

If we do not write a constructor, JavaScript internally behaves like this:

```js
class Person {
  constructor() {

  }

  greet() {
    console.log("Hello");
  }
}
```

This is called the default constructor.

---

# Problem Without Constructor

Without constructor, values passed during object creation are not stored automatically.

## Example

```js
class User {

}

const u1 = new User("Krupa", 25);

console.log(u1.name);
```

## Output

```js
undefined
```

Because:
- Constructor receives values
- Constructor assigns values
- Without constructor, values are ignored

---

# Correct Way Using Constructor

```js
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const u1 = new User("Krupa", 25);

console.log(u1.name);
```

## Output

```js
Krupa
```

---

# Important Interview Points

- Constructor is optional in JavaScript classes
- If not written, JavaScript creates a default empty constructor
- Object creation still works
- Properties are not initialized automatically
- Constructor is mainly used for object initialization

---

# Inheritance Case

If child class does not have constructor, parent constructor is automatically called.

## Example

```js
class Parent {
  constructor() {
    console.log("Parent Constructor");
  }
}

class Child extends Parent {

}

const c1 = new Child();
```

## Output

```js
Parent Constructor
```

---

# One-Line Interview Answer

If a constructor is not defined in a class, JavaScript automatically provides a default empty constructor. Objects can still be created, but values will not initialize automatically.

---

# Easy Memory Trick

| Situation | Result |
|---|---|
| No constructor | Default empty constructor |
| Object create | ✅ Works |
| Value initialize | ❌ Not automatic |
| In inheritance | Parent constructor auto call |


