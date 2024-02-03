---
author: Eka Prasetia
pubDatetime: 2020-04-30T19:30:00.737+07:00
title: Spread Operator
slug: spread-operator
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - javascript
description: Merge with Spread Operator.
---

Merge with Spread Operator more easy. Take a `note`, if the objects contains same property, the right-post will overwrite.

```js
const user1 = {
  name: "John",
  age: 40,
  admin: true,
};

const user2 = {
  name: "Dow",
  age: 35,
};

const merged = {
  ...user1,
  ...user2,
};

console.log(merged);
// { name: 'Dow', age: 35, admin: true }
```
