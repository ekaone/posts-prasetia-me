---
author: Eka Prasetia
pubDatetime: 2020-05-02T19:00:00.737+07:00
title: Simple Prototype
slug: simple-prototype
featured: false
tags:
  - javascript
description: Simple Prototype in Javascript.
---

## Prototypes in JavaScript:

- **Overview:** Prototypes are a fundamental concept in JavaScript's object-oriented programming model. They provide a way to **inherit properties and methods** from an object (the **prototype**) to other objects (instances).
- **Inheritance Mechanism:** When you create an object using a constructor function like `Foo`, JavaScript creates a new instance and links it to the constructor's `prototype` property. This link allows the instance to **access and inherit properties and methods** defined on the `prototype`.

Let's breakdown of the Code below:

```javascript
function Foo(params1) {
  this.params1 = params1;
}
```

- **`Function Foo(params1)`:** This line defines a constructor function named `Foo` that takes a single parameter `params1`.
- **`this.params1 = params1;`:** Inside the constructor, the `this` keyword refers to the newly created object instance. This line assigns the value of `params1` to a property named `params1` on the instance.

**Prototype Inheritance:**

- Every function in JavaScript has a `prototype` property, initially set to an empty object.
- When you create an instance of `Foo`, JavaScript does the following:
  1. Creates a new empty object.
  2. Sets the object's `__proto__` property (hidden internal property) to the `prototype` of the `Foo` function (which is initially an empty object).
  3. Executes the `Foo` function's code, passing the new object as `this`. This allows you to define properties like `params1` on the instance.

**Accessing Inherited Properties:**

- If an instance (like `const foo = new Foo("value")`) tries to access a property it doesn't have (e.g., `foo.nonexistent`), JavaScript automatically looks for it on the instance's `__proto__` (the `Foo.prototype` object).
- If the property is found on the `prototype`, it's inherited and made available to the instance.

## All `Javascript Object` inherit properties and methods from prototype.

Let's dive in for real world, firstly Create `Object Constructor`

```js
function Foo(params1) {
  this.params1 = params1;
}
```

Call property with new instance

```js
const instance = new Foo("Params 1");
console.log(instance.params1);
// ---- output: Params 1
```

We can not add new property to existing `Object Constructor`

```js
Foo.newProperty = "This is new Property";
console.log(instance.newProperty);
// ---- output: undefined
```

And last we can add new property to `Object Constructor`

```js
Foo.prototype.bar = "This is new Bar";
console.log(instance.bar);
// ---- output: This is new Bar
```

For complete codes

```js
function Foo(params1) {
  this.params1 = params1;
}

/**
 * Create new instance as representative of Foo
 * all Foo's stuff will be inherits to new instance
 */
const instance = new Foo("Params 1");

// take property default
console.log(instance.params1);
// ---- output: Params 1

// can not add new property
Foo.newProperty = "This is new Property";
console.log(instance.newProperty);
// ---- output: undefined

// add new property
Foo.prototype.bar = "This is new Bar";
console.log(instance.bar);
// ---- output: This is new Bar
```

**Key Points:**

- Prototypes provide a simple mechanism for inheritance in JavaScript.
- Instance properties take precedence over inherited properties from the prototype.
- You can modify the `prototype` property of a constructor function to add shared properties and methods for all instances.

Thank you for reading this article, I hope you find it useful. Happy coding! 🔥
