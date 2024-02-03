---
author: Eka Prasetia
pubDatetime: 2020-05-01T23:00:00.737+07:00
title: Safety your private properties
slug: private-scope
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - javascript
description: Private Scope for Safety your private properties
---

You can pass desired properties, this approach better for security reason.

```js
const privateScope = (() => {
  const foo = "Foo";
  const bar = "Bar";
  const printFoo = () => {
    return `hi, i am ${foo}`;
  };
  const printBar = () => {
    return `hi, i am ${bar}`;
  };

  return { printFoo, printBar };
})();

console.log(privateScope.printFoo()); // hi, i am Foo
console.log(privateScope.printBar()); // hi, i am Bar
console.log(privateScope.foo); // undefined
```
