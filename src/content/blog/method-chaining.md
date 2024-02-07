---
author: Eka Prasetia
pubDatetime: 2020-12-03T17:00:00.330+07:00
title: Method Chaining
slug: method-chaining
featured: false
tags:
  - javascript
description: Method chains allow a series of functions to operate in succession to reach a final result.
---

Method chaining in JavaScript involves chaining multiple method calls together on the same object or result. This pattern is commonly used with array methods like `filter`, `map`, `reduce`, and others, where each method returns a new array or value, allowing you to call another method on the result.

Let's take an example using array methods:

```javascript
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter(num => num % 2 === 0) // Filter even numbers
  .map(num => num * 2) // Double each remaining number
  .reduce((acc, num) => acc + num, 0); // Sum up the doubled numbers

console.log(result); // Outputs 18 (2*2 + 4*2 + 5*2)
```

In this example, numbers is an array, and we chain three array methods together: `filter`, `map`, and `reduce`. Here's how it works:

1. Filter: The filter method is used to create a new array containing only the even numbers from the original array.

2. Map: The map method is then applied to double each number in the filtered array, creating a new array.

3. Reduce: Finally, the reduce method is used to sum up all the doubled numbers in the mapped array, resulting in a single value (18 in this case).

Method chaining improves code readability and reduces the need for intermediate variables. It allows you to express a series of operations on data in a more concise and declarative manner.

Another common use case for method chaining is with `array of objects`, for example:

```javascript
let cart = [
  { name: "Drink", price: 3.12 },
  { name: "Steak", price: 45.15 },
  { name: "Drink", price: 11.01 },
];

const drinkTotal = cart
  .filter(item => item.name === "Drink")
  .map(item => item.price)
  .reduce((total, price) => total + price, 0)
  .toFixed(2);

console.log(`Total Drink Cost $${drinkTotal}`); // Total Drink $14.13
```

Thank you for reading this article, I hope you find it useful. Happy coding! 🔥
