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

JSON.Stringify` is used to convert an Objects to JSON String.

Given an Objects.

```js
const objects = [
  { name: "Eka Prasetia" },
  { city: "Jakarta" },
  { hobby: "Play codes" },
];
```

Get some specified properties.

```JS
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
