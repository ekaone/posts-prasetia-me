---
author: Eka Prasetia
pubDatetime: 2020-05-01T23:00:00.737+07:00
title: Safety your private properties
slug: private-scope
featured: false
tags:
  - javascript
description: Private Scope for Safety your private properties
---

## Understanding Private Scope in JavaScript

In JavaScript, **private scope** refers to the ability to restrict access to variables and functions within a specific code block or object. While JavaScript doesn't have built-in mechanisms for true private members in classes (until ES6 modules), several techniques can achieve similar effects.

Here are some common ways to create private scope in JavaScript:

**1. Immediately Invoked Function Expressions (IIFEs):**

As you saw in the code example, IIFEs allow you to create a closure where variables and functions defined within the function are inaccessible from outside. Any values you want to expose publicly need to be returned from the IIFE.

**2. Module Pattern:**

This pattern leverages object literals and closures to create modules with private and public members. Variables are declared within the module function, and only specific functions are returned, making everything else private.

**3. Namespaces:**

Namespaces, while not true private scope, can help organize your code and create a level of separation between different parts. By using object literals or functions under a specific namespace, you can prevent naming conflicts and improve code organization.

**4. WeakMaps:**

These built-in objects allow you to create private properties on objects. The key is a weak reference (usually an object), keeping the property private unless you have access to the original key.

**5. ES6 Classes (with limitations):**

While not strictly private due to possible prototype manipulation, using `#` before variable names within an ES6 class provides a layer of security by making them harder to access directly.

**Benefits of Private Scope:**

- **Encapsulation:** Keeps implementation details hidden and promotes modularity.
- **Reduced Naming Conflicts:** Prevents accidental modification of variables used in other parts of your code.
- **Improved Maintainability:** Makes code easier to understand and modify.

## Example

You can pass desired properties, this approach intended to security reason.

```js
const privateScope = (() => {
  const foo = "Foo";
  const bar = "Bar";
  const printFoo = () => {
    return `hi, i am ${foo}`;
  };
  const printBar = () => {
    return `hi, i am ${bar}`;
  };

  return { printFoo, printBar };
})();

console.log(privateScope.printFoo()); // hi, i am Foo
console.log(privateScope.printBar()); // hi, i am Bar
console.log(privateScope.foo); // undefined
```

The code as above defines a **private scope** using an Immediately Invoked Function Expression (IIFE). Here's a breakdown of what's happening:

**1. Immediately Invoked Function Expression (IIFE):**

- `const privateScope = (() => { ... })();` is an IIFE. It defines a function and immediately invokes it using the second pair of parentheses. This creates a closure, where variables and functions defined within the IIFE are not accessible from outside.

**2. Variables and Functions within the IIFE:**

- `const foo = "Foo";` and `const bar = "Bar";` define private variables accessible only within the IIFE.
- `const printFoo = () => { ... };` and `const printBar = () => { ... };` define private functions that can access these private variables.

**3. Returning an Object:**

- The IIFE returns an object: `{ printFoo, printBar }`. This exposes only the functions to the outside world, keeping the variables `foo` and `bar` private.

**4. Usage:**

- `console.log(privateScope.printFoo());` and `console.log(privateScope.printBar());` call the exposed functions, which print the expected values.
- `console.log(privateScope.foo);` attempts to access `foo` directly, but since it's private, it results in `undefined`.

**Key Points:**

- IIFEs create private scopes, protecting variables and functions from the outside world.
- Only what's explicitly returned from the IIFE becomes accessible publicly.
- This code demonstrates encapsulation, hiding implementation details and only exposing necessary functionality through public functions.

**Choosing the Right Method:**

The best approach for private scope depends on your specific needs and coding style. Consider factors like code complexity, reusability, and compatibility with your JavaScript environment.

Remember that while these techniques provide a level of privacy, they are not foolproof. A determined developer could still access private members through various means.

I hope this comprehensive explanation clarifies the concept of private scope in JavaScript!
