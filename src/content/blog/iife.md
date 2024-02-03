---
author: Eka Prasetia
pubDatetime: 2020-06-02T18:00:00.737+07:00
title: IIFE (Immediately Invoked Function Expression)
slug: iife
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - javascript
description: An IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined.
---

```js
(function () {
  // ...your codes
})();
```

...or use arrow function `() =>`

```js
(() => {
  // ...your codes
})();
```

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
