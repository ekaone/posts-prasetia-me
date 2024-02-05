---
author: Eka Prasetia
pubDatetime: 2020-04-30T19:30:00.737+07:00
title: Compilation of Reduce function
slug: compilation-reduce-function
featured: false
ogImage: https://raw.githubusercontent.com/ekaone/assets/main/og-images/posts/og-reduce-function.png
tags:
  - javascript
description: List of compilation using reduce() function
---

List of compilation using reduce() function

## Reduce function for Average

If you would like looking for average, you can try `reduce()`.

```js
const average = (...args) => {
  return args.reduce((acc, el) => acc + el, 0) / args.length;
};

console.log(average(1, 2, 3, 4)); // 2.5
```

## Reduce function for Object

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

## And another example of using reduce() function for array of numbers:

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
