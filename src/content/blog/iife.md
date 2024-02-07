---
author: Eka Prasetia
pubDatetime: 2020-06-02T18:00:00.737+07:00
title: IIFE (Immediately Invoked Function Expression)
slug: iife
featured: false
ogImage: https://res.cloudinary.com/ddjsyskef/image/upload/v1707202657/prasetia-me/iife.png
tags:
  - javascript
description: An IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined.
---

IIFE, short for Immediately Invoked Function Expression, is a fancy way of saying "function that runs as soon as it's defined."

Here's the breakdown:

- **Function:** It's a block of code designed to perform a specific task.
- **Expression:** It's a combination of values, variables, and operators that evaluates to a single result.
- **Immediately Invoked:** As soon as you write the expression, it runs the function without needing to call it separately.

**Why use IIFE?:**

- **Encapsulation:** Keeps variables and logic [private within the function](http://localhost:4321/posts/private-scope/), preventing conflicts with other parts of your code.
- **Module Pattern:** Creates isolated modules with their own variables and functions.
- **Code Cleanup:** Executes initialization code once without cluttering the global scope.
- **Avoiding Global Pollution:** Prevents accidental modification of global variables.

**How it looks:**

Imagine a party happening inside parentheses:

```javascript
(function () {
  // Code to be executed immediately
})();
```

The function is defined, wrapped in parentheses, and then immediately invoked by the second pair of parentheses.

Example of IIFE:

```js
(() => {
  console.log("IIFE");
})();
// output "IIFE"
```

IIFE is used to avoid polluting the global scope. It's a good practice to wrap your code in an IIFE to avoid polluting the global scope.

```js
(() => {
  const foo = "Foo";
  console.log(foo); // output "Foo"
})();

console.log(foo); // Uncaught ReferenceError: foo is not defined
```

IIFE is also used to create a new scope for your variables. This is useful when you want to avoid variable hoisting.

```js
(() => {
  console.log(foo); // undefined
  var foo = "Foo";
  console.log(foo); // output "Foo"
})();
```
