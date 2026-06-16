# Explain How JavaScript Handles Type Coercion Internally

## What is Type Coercion?

Type coercion is the automatic or implicit conversion of one data type into another by JavaScript when performing operations or comparisons.

JavaScript is a **dynamically typed language**, so variables can hold values of different types, and the engine automatically converts types when needed.

---

# Types of Type Coercion

## 1. Implicit Type Coercion

JavaScript automatically converts data types behind the scenes.

### Example

```javascript
console.log("5" + 2);
```

Output:

```javascript
"52"
```

Here JavaScript converts `2` into a string and performs string concatenation.

---

### Example

```javascript
console.log("5" - 2);
```

Output:

```javascript
3
```

Here JavaScript converts `"5"` into a number and performs subtraction.

---

## 2. Explicit Type Coercion

The developer manually converts one type into another.

### Example

```javascript
Number("10");
String(100);
Boolean(1);
```

---

# How JavaScript Performs Type Coercion Internally

When an operation involves different data types, the JavaScript engine follows rules defined in the ECMAScript specification.

The engine uses internal abstract operations such as:

* ToPrimitive()
* ToString()
* ToNumber()
* ToBoolean()

These operations convert values before executing the operation.

---

# ToPrimitive()

When JavaScript encounters an object in an operation, it first attempts to convert the object into a primitive value.

### Example

```javascript
const obj = {
  valueOf() {
    return 10;
  }
};

console.log(obj + 5);
```

Output:

```javascript
15
```

Internally:

```javascript
obj → valueOf() → 10
10 + 5 → 15
```

---

# ToString()

Used when JavaScript expects a string.

### Example

```javascript
console.log("Age: " + 25);
```

Internally:

```javascript
25 → "25"
```

Result:

```javascript
"Age: 25"
```

---

# ToNumber()

Used when arithmetic operations require numbers.

### Example

```javascript
console.log("10" * "2");
```

Internally:

```javascript
"10" → 10
"2" → 2
```

Result:

```javascript
20
```

---

# ToBoolean()

Used in conditional statements.

### Example

```javascript
if ("hello") {
  console.log("Runs");
}
```

Internally:

```javascript
Boolean("hello")
```

becomes:

```javascript
true
```

---

# Truthy and Falsy Values

## Falsy Values

```javascript
false
0
-0
0n
""
null
undefined
NaN
```

All other values are considered truthy.

---

### Example

```javascript
if (0) {
  console.log("Hello");
}
```

Output:

Nothing is printed because `0` is falsy.

---

# Type Coercion with Equality Operators

## Loose Equality (==)

Performs type coercion before comparison.

### Example

```javascript
console.log(5 == "5");
```

Output:

```javascript
true
```

Internally:

```javascript
Number("5") → 5

5 == 5
```

Result:

```javascript
true
```

---

## Strict Equality (===)

No type coercion occurs.

### Example

```javascript
console.log(5 === "5");
```

Output:

```javascript
false
```

Because:

```javascript
Number !== String
```

---

# Common Interview Examples

## Example 1

```javascript
console.log(true + 1);
```

Output:

```javascript
2
```

Internally:

```javascript
true → 1

1 + 1 = 2
```

---

## Example 2

```javascript
console.log(false + false);
```

Output:

```javascript
0
```

Internally:

```javascript
false → 0

0 + 0 = 0
```

---

## Example 3

```javascript
console.log([] + []);
```

Output:

```javascript
""
```

Internally:

```javascript
[] → ""

"" + "" = ""
```

---

## Example 4

```javascript
console.log([] + {});
```

Output:

```javascript
"[object Object]"
```

Internally:

```javascript
[] → ""
{} → "[object Object]"

"" + "[object Object]"
```

---

## Example 5

```javascript
console.log(null == undefined);
```

Output:

```javascript
true
```

Special rule in JavaScript:

```javascript
null == undefined
```

returns true.

---

# Why is === Recommended?

Using `===` avoids unexpected conversions and makes code more predictable.

### Bad

```javascript
if (value == 0)
```

### Better

```javascript
if (value === 0)
```

---

# Interview Summary

"JavaScript handles type coercion using internal abstract operations like ToPrimitive(), ToString(), ToNumber(), and ToBoolean(). When values of different types are used together, JavaScript automatically converts them according to ECMAScript rules before performing the operation. Loose equality (==) performs type coercion, while strict equality (===) does not. Understanding these conversion rules helps avoid unexpected behavior and write more reliable code."

**Short interview answer (1 minute):**

> JavaScript uses automatic type conversion called type coercion. Internally, the engine uses operations like ToPrimitive, ToString, ToNumber, and ToBoolean to convert values before executing expressions. For example, `"5" - 2` becomes `5 - 2`, while `"5" + 2` becomes `"52"` because the number is converted to a string. Loose equality (`==`) performs coercion, whereas strict equality (`===`) compares both value and type without conversion. That's why `===` is generally preferred in production code.
