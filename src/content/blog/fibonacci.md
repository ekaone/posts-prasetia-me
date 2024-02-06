---
author: Eka Prasetia
pubDatetime: 2020-11-09T12:30:00.737+07:00
title: Fibonacci numbers complex Time complexity
slug: fibonacci
featured: false
ogImage: https://res.cloudinary.com/ddjsyskef/image/upload/v1707200219/prasetia-me/fibonacci.png
tags:
  - javascript
  - fibonacci
description: Fibonacci numbers complex Time complexity
---

There are many ways how to solve the problem, compare `fibonacci` calculation with Big O notation

```js
function fibonacci(num) {
  if (num <= 1) {
    return 1;
  }

  return fibonacci(num - 1) + fibonacci(num - 2);
}
```

<br />

```js
function fibonacci(num) {
  var a = 1,
    b = 0,
    temp;

  while (num >= 0) {
    temp = a;
    a = a + b;
    b = temp;
    num--;
  }

  return b;
}
```

💁‍♀️ take a note that `while` loop more faster than `recursive`.

## Big O notation

| Algorithm | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| Recursive | O(2^n)          | O(n)             |
| Iterative | O(n)            | O(1)             |

## Conclusion

- Recursive is slower than Iterative
- Recursive has more space complexity than Iterative
- Iterative is faster than Recursive
- Iterative has less space complexity than Recursive
- Iterative is better than Recursive
- Iterative is the best solution for Fibonacci calculation
