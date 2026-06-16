# Usage of `break` and `continue` in For Loops and Nested Loops

## What is `break`?

The `break` statement is used to immediately terminate a loop when a specific condition is met.

Once `break` executes, the control exits the loop and moves to the next statement after the loop.

### Example

```javascript
for (let i = 1; i <= 5; i++) {
  if (i === 3) {
    break;
  }

  console.log(i);
}
```

### Output

```javascript
1
2
```

### Explanation

* Loop starts from 1.
* When `i` becomes 3, the `break` statement executes.
* The loop terminates immediately.

---

# What is `continue`?

The `continue` statement skips the current iteration and moves directly to the next iteration of the loop.

Unlike `break`, it does not terminate the loop.

### Example

```javascript
for (let i = 1; i <= 5; i++) {
  if (i === 3) {
    continue;
  }

  console.log(i);
}
```

### Output

```javascript
1
2
4
5
```

### Explanation

* When `i` becomes 3, `continue` skips that iteration.
* The loop continues with the next value.

---

# Difference Between `break` and `continue`

| break                                      | continue                                           |
| ------------------------------------------ | -------------------------------------------------- |
| Terminates the loop completely             | Skips only the current iteration                   |
| Control exits the loop                     | Control moves to the next iteration                |
| Used when no further iterations are needed | Used when a particular iteration should be ignored |

---

# Interview Tips

### When should you use `break`?

* Searching for an item.
* Stopping a loop when a condition is met.
* Avoiding unnecessary iterations.

### When should you use `continue`?

* Skipping invalid records.
* Ignoring specific conditions.
* Filtering data during iteration.

---

# Interview Answer (Short Version)

"`break` is used to terminate a loop immediately when a condition is met, while `continue` skips the current iteration and proceeds with the next one. In nested loops, both statements affect only the loop in which they are written. `break` is commonly used when searching for a value, and `continue` is useful when certain iterations need to be ignored."
