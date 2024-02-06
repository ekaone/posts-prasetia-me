---
author: Eka Prasetia
pubDatetime: 2020-07-05T21:00:00.737+07:00
title: Simple function of Filter, Index and Every
slug: simple-function-filter-index-every
featured: false
ogImage: https://res.cloudinary.com/ddjsyskef/image/upload/v1707201295/prasetia-me/arrayfunction.png
tags:
  - javascript
description: Example of function of filter, index and every.
---

## Filter function

`filter()` method creates a new array with all elements that pass the test implemented by the provided function.

```js
const elements = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
```

Let's create `isEven` function.

```js
function isEven(element) {
  return element % 2 === 0;
}
```

Use `filter` to find even numbers, reach documentation 🚀 [filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter).

```js
elements.filter(isEven);
```

As complete codes.

```js
function isEven(element) {
  return element % 2 === 0;
}

const elements = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

console.log(elements.filter(isEven));
// output [2, 4, 6, 8, 10]
```

## Index function

`indexOf()` method returns the first index at which a given element can be found in the array, or -1 if it is not present.

```js
const cities = ["jakarta", "texas", "tokyo"];

const index = cities.indexOf("tokyo");

//index is `2`
```

You may use findIndex for an Objects array.

```js
const cities = [{ city: "jakarta" }, { city: "texas" }, { city: "tokyo" }];

const index = cities.findIndex((el, index) => {
  if (el.city === "texas") return true;
});

console.log(index); // index is 1
```

## Every function

`every()` method tests whether all elements in the array pass the test implemented by the provided function.

```js
[1, 2, 3, 4, 5].every(el => el < 10); // true
[1, 2, 3, 4, 5].every(el => el < 5); // false
[1, 2, 3, 4, 5].every(el => el > 0); // true
```
