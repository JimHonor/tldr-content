---
publishAt: "2023-12-29"
title: "javascript increment operator"
ctime: 2023-12-29
---

**1） x++**

If the operator is to the right of its operand, it fisrt returns the value and then add one to its operand.

For example:

```js
let x = 3;
let y = x++; // First, let y = x. Then, x = x + 1.

// Finally, x is 4, y is 3.
```

**2） ++x**

If the operator is to the left of its operand, it first adds one to its operand and then returns the value.

For example:

```js
let x = 3;
let y = ++x; // First, x = x + 1. Then, let y = x.

// Finally, x is 4, y is 4.
```

Source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Increment