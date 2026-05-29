# "use strict" in JavaScript

## What is "use strict"?

`"use strict"` is a special directive in JavaScript that enables **strict mode**.

It helps write:

* cleaner code
* safer code
* error-free code

---

## Syntax

```javascript
"use strict";

x = 10; // Error
```

---

## Why Use It?

* Prevents accidental global variables
* Throws errors for unsafe code
* Improves debugging
* Makes code more secure
* Helps optimize JavaScript engines

---

## Example Without Strict Mode

```javascript
x = 10;
console.log(x); // Works (bad practice)
```

---

## Example With Strict Mode

```javascript
"use strict";

x = 10; // Error: x is not defined
```

---

## Common Interview Points

### 1. Prevents Global Variables

```javascript
"use strict";

name = "Jarvis"; // Error
```

### 2. Duplicate Parameters Not Allowed

```javascript
"use strict";

function test(a, a) { // Error
}
```

### 3. Cannot Use Reserved Keywords

```javascript
"use strict";

let interface = 10; // Error
```

---

## Important

* Mostly used at the top of file/function
* ES6 modules automatically run in strict mode

---

## Interview One-Line Answer

`"use strict"` enables strict mode in JavaScript, which helps catch common coding mistakes and makes code safer and cleaner.
