---
author: Eka Prasetia
pubDatetime: 2020-10-02T18:00:00.300+07:00
title: Higher Order Functions
slug: higher-order-functions
featured: false
ogImage: https://res.cloudinary.com/ddjsyskef/image/upload/v1707202066/prasetia-me/hof.png
tags:
  - javascript
description: A function that accepts another function as a parameter, or returns another function.
---

[Higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function) are functions that can take other functions as arguments or return them as results. In JavaScript, functions are first-class citizens, meaning they can be treated like any other value (such as strings, numbers, or objects). This allows for the creation and manipulation of higher-order functions.

There are **two main types** of higher-order functions:

## Functions that take a function as an argument

These functions are often called "callbacks." The function that is passed as an argument can be executed during the execution of the higher-order function.

```javascript
function higherOrderFunction(callback) {
  // ... do something ...
  callback();
}

higherOrderFunction(function () {
  console.log("This is a callback function");
});
```

Example mapping pairs of consecutive elements:

```javascript
function mapPairs(values, fn) {
  return values
    .slice(0, -1)
    .map((current, index) => fn(current, values[index + 1]));
}

const letters = ["a", "b", "c", "d", "e", "f", "g"];
const twoByTwo = mapPairs(letters, (x, y) => [x, y]);
console.log(twoByTwo);
// [[a,b], [b,c], [c,d], [d,e], [e,f], [f,g]]
```

## Functions that return a function

These functions are often used to create specialized functions based on the parameters provided.

```javascript
function createMultiplier(factor) {
  return function (number) {
    return number * factor;
  };
}

const double = createMultiplier(2);
console.log(double(5)); // Outputs 10
```

Higher-order functions are a powerful concept in functional programming and can lead to more modular, reusable, and expressive code. They allow for the abstraction of common patterns and behaviors, making it easier to write flexible and maintainable code. Examples of higher-order functions in JavaScript include `map`, `filter`, `reduce`, and functions that accept a callback, like `setTimeout` or `addEventListener`.
