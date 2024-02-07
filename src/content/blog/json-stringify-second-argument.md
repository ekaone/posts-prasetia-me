---
author: Eka Prasetia
pubDatetime: 2020-07-07T17:15:00.737+07:00
title: JSON.Stringify on second argument
slug: json-stringify-second-argument
featured: false
tags:
  - javascript
description: What is second argument do on JSON.Stringify
---

In JavaScript, `JSON.stringify()` is a built-in method that converts a JavaScript value into a JSON string representation. JSON (JavaScript Object Notation) is a common format for exchanging data between web applications and APIs.

Here's a breakdown of `JSON.stringify()`:

**Syntax:**

```javascript
JSON.stringify(value, replacer, space);
```

- **value:** The JavaScript value to be converted (object, array, string, number, etc.).
- **replacer (optional):** A function or array that transforms the value before stringification.
- **space (optional):** A string (or number) used to indent the output for readability.

**What it Does:**

- Converts primitive values like strings, numbers, booleans, and `null` directly to their JSON equivalents.
- Converts arrays by iterating through their elements and stringifying each one.
- Converts objects by enumerating their properties and stringifying their key-value pairs.
- Excludes properties with `undefined` values or functions by default.
- Can be customized with the `replacer` and `space` options.

**Examples:**

```javascript
const object = { name: "Alice", age: 30 };
const jsonString = JSON.stringify(object); // '{"name":"Alice","age":30}'

const array = [1, 2, 3];
const jsonString = JSON.stringify(array); // '[1,2,3]'

const date = new Date();
const jsonString = JSON.stringify(date); // '2024-02-07T02:54:22.394Z' (not recommended)

// Customizing with replacer:
const object = { name: "Alice", age: 30, password: "secret" };
const jsonString = JSON.stringify(object, (key, value) => {
  if (key === "password") return undefined; // Exclude password
  return value;
});
```

Let's take a look another example, we have an array of objects and we want to get some specified properties and their value from the objects. For example given an Objects:

```js
const objects = [
  { name: "Eka Prasetia" },
  { city: "Jakarta" },
  { hobby: "Play codes" },
];
```

Get some specified properties.

```js
JSON.stringify(objects, ["name", "hobby"], 2);
// output "name" and "hobby" properties and their value
```

Another way, we can replace property value as follow.

```js
const result = JSON.stringify(
  objects,
  (key, value) => {
    if (key.match(/name|city/)) return "👨‍👩‍👧✌";
    return value;
  },
  2
);
// output [{ "name": "👨‍👩‍👧✌"},{"city": "👨‍👩‍👧✌"},{"hobby": "Play codes"}]
```

The second argument is a replacer function, which is called for each property in the object being stringified. The replacer function can return a string or a number that will be used to replace the property's value, or `undefined` if the property should be removed from the stringified output.

**Key Points:**

- `JSON.stringify()` is useful for sending data to servers or storing it in local storage.
- It's important to be mindful of circular references or functions when stringifying objects.
- Consider using `replacer` to customize the output or exclude sensitive information.
- Be cautious when stringifying dates as JSON doesn't have a native date type.

Thank you for reading this article, I hope you find it useful. Happy coding! 🔥
