---
author: Eka Prasetia
pubDatetime: 2020-04-28T22:00:00.737+07:00
title: Reduce function for Average
slug: reduce-function
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - javascript
description: Find Average with reduce function.
---

If you would like looking for average, you can try `reduce()`.

```js
const average = (...args) => {
  return args.reduce((acc, el) => acc + el, 0) / args.length;
};

console.log(average(1, 2, 3, 4)); // 2.5
```
