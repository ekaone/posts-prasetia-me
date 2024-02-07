---
author: Eka Prasetia
pubDatetime: 2020-04-30T19:30:00.737+07:00
title: Spread Operator
slug: spread-operator
featured: false
tags:
  - javascript
description: Merge with Spread Operator.
---

In JavaScript, the spread operator (`...`) allows you to "spread" an iterable (like an array or object) into another. This can be used to achieve different effects, including merging arrays and objects.

## Merging Arrays with Spread Operator

Here's how you can merge two arrays using the spread operator:

```javascript
const array1 = [1, 2, 3];
const array2 = [4, 5, 6];

const mergedArray = [...array1, ...array2];

console.log(mergedArray); // Output: [1, 2, 3, 4, 5, 6]
```

In this example, we're spreading the elements of `array1` and `array2` into a new array `mergedArray`. This creates a new array containing all the elements from both original arrays.

## Merging Objects with Spread Operator

While merging objects with the spread operator is possible, it's important to understand its behavior:

- **Merging properties:** When merging objects, the spread operator adds properties from the rightmost object to the leftmost one. If a property exists in both objects, the value from the rightmost object takes precedence.
- **Shallow copy:** The spread operator only creates a shallow copy of the object. Nested objects within the merged object remain linked to the original object.

Here's an example:

```javascript
const obj1 = { name: "Alice", age: 30 };
const obj2 = { city: "New York", age: 35 };

const mergedObj = { ...obj1, ...obj2 };

console.log(mergedObj); // Output: { name: "Alice", age: 35, city: "New York" }

// Modifying nested object in mergedObj affects obj1
mergedObj.age = 40;
console.log(obj1.age); // Output: 40
```

As you can see, the `age` property from `obj2` takes precedence in the merged object. Additionally, modifying the nested object inside `mergedObj` also affects the original `obj1` due to the shallow copy.

## Cautions and Alternatives

While the spread operator provides a concise way to merge arrays and objects, be cautious of its shallow copy behavior when dealing with nested data. For deep merging objects, consider using alternative methods like `Object.assign` or libraries like Lodash\_.merge that handle nested objects correctly.

I hope this explanation clarifies the concept of merging with the spread operator in JavaScript!

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

Thank you for reading this article, I hope you find it useful. Happy coding! 🔥
