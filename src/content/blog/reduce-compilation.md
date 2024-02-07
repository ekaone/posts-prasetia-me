---
author: Eka Prasetia
pubDatetime: 2020-04-30T19:30:00.737+07:00
title: Compilation of Reduce function
slug: compilation-reduce-function
featured: false
tags:
  - javascript
description: List of compilation using reduce() function
---

## What is `reduce`?

The `reduce` function is a powerful iterative method in JavaScript that allows you to accumulate a single value from an array based on a provided callback function. It executes the callback function on each element of the array, using the accumulated value and the current element in each iteration. The final return value of the callback function becomes the accumulated value for the next iteration.

**Syntax:**

```javascript
array.reduce(callbackFn, initialValue);
```

- `array`: The array to be reduced.
- `callbackFn`: The function to be executed on each element. It takes four arguments:
  - `accumulator`: The accumulated value from the previous iteration (or `initialValue` in the first iteration).
  - `currentValue`: The current element being processed.
  - `currentIndex`: The index of the current element.
  - `array`: The entire array being reduced.
- `initialValue`: (Optional) An initial value to be used as the `accumulator` for the first iteration. If omitted, the first element of the array will be used as the accumulator.

**How it works:**

1. If an `initialValue` is provided, it becomes the accumulator for the first iteration. Otherwise, the first element of the array becomes the accumulator.
2. The `callbackFn` is called with the accumulator, current element, current index, and the entire array as arguments.
3. The return value of the `callbackFn` becomes the new accumulator for the next iteration.
4. Steps 2 and 3 are repeated for each element in the array.
5. The final accumulated value is returned after processing all elements.

**Example:**

```javascript
const numbers = [1, 2, 3, 4, 5];

// Sum all numbers
const sum = numbers.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
);
console.log(sum); // Output: 15

// Concatenate strings
const words = ["hello", "world"];
const sentence = words.reduce(
  (accumulator, currentValue) => accumulator + " " + currentValue
);
console.log(sentence); // Output: hello world

// Find the maximum number
const max = numbers.reduce(
  (accumulator, currentValue) => Math.max(accumulator, currentValue),
  -Infinity
);
console.log(max); // Output: 5
```

## List of compilation using reduce() function

### Reduce function for Average

If you would like looking for average, you can try `reduce()`.

```js
const average = (...args) => {
  return args.reduce((acc, el) => acc + el, 0) / args.length;
};

console.log(average(1, 2, 3, 4)); // 2.5
```

### Reduce function for Array of Objects

```js
const worlds = [
  { id: "1", city: "Jakarta", country: "Indonesia", population: 23 },
  { id: "2", city: "Tokyo", country: "Japan", population: 14 },
  { id: "3", city: "New York", country: "United States", population: 25 },
];

result1 = worlds.reduce(acc => acc + 1, 0);
console.log(result1);
// 3

result2 = worlds.reduce((acc, pop) => acc + pop.population, 0);
console.log(result2);
// 62

result3 = worlds.reduce((acc, cty) => [...acc, cty.city], []);
console.log(result3);
// [ 'Jakarta', 'Tokyo', 'New York' ]

result4 = worlds.reduce((acc, world) => {
  if (acc === null || world.population > acc) return world.population;
  return acc;
}, null);
console.log(result4);
// 25

result5 = worlds.reduce((acc, world) => {
  if (acc === null || world.population < acc) return world.population;
  return acc;
}, null);
console.log(result5);
// 14

result6 = worlds.reduce((acc, world) => {
  if (acc !== null) return acc;
  if (world.city === "Tokyo") return world;
  return null;
}, null);
console.log(result6);
// { id: '2', city: 'Tokyo', country: 'Japan', population: 14 }
```

### Reduce function for array of numbers:

```js
const numbers = [1, 2, 3, 4];

const r1 = numbers.reduce(
  (previousValue, currentValue) => previousValue + currentValue
);
console.log(r1);
// 10

const r2 = numbers.reduce(
  (previousValue, currentValue) => previousValue * currentValue
);
console.log(r2);
// 24

const r3 = numbers.reduce((previousValue, currentValue) => {
  previousValue.push(currentValue * 2);
  return previousValue;
}, []);
console.log(r3);
// [ 2, 4, 6, 8 ]

const r4 = numbers.reduce((previousValue, currentValue) => {
  if (currentValue > 2) previousValue.push(currentValue);
  return previousValue;
}, []);
console.log(r4);
// [ 3, 4 ]

const r5 = numbers.reduce((total, amount) => {
  if (amount % 2 === 0) total.push(amount);
  return total;
}, []);
console.log(r5);
// [ 2, 4 ]

const r6 = numbers.reduce((total, amount) => {
  if (amount % 2 === 1) total.push(amount);
  return total;
}, []);
console.log(r6);
// [1, 3 ]
```

**Key points:**

- `reduce` is versatile and can be used for various accumulation tasks, like calculations, string manipulation, object creation, and more.
- It's important to ensure your `callbackFn` returns a value, or an error will occur.
- Understanding the accumulator-based approach is crucial for effective use.
- Consider arrow functions for concise callback definitions.

Thank you for reading this article, I hope you find it useful. Happy coding! 🔥
