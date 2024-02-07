---
author: Eka Prasetia
pubDatetime: 2020-11-09T12:30:00.737+07:00
title: Fibonacci numbers complex Time complexity
slug: fibonacci
featured: false
ogImage: https://res.cloudinary.com/ddjsyskef/image/upload/v1707200219/prasetia-me/fibonacci.png
tags:
  - javascript
  - fibonacci
description: Fibonacci numbers complex Time complexity
---

## What is Fibonacci?

The Fibonacci sequence is a famous series of numbers where each number is the sum of the two preceding numbers. Starting from 0 and 1, the sequence continues as 1, 2, 3, 5, 8, 13, 21, 34, and so on. It's named after Leonardo Fibonacci, an Italian mathematician from the 13th century who introduced it while studying rabbit populations.

**Properties and Applications:**

The Fibonacci sequence exhibits fascinating mathematical properties and has real-world applications in various fields, including:

- **Mathematics:** Used in number theory, combinatorics, and analysis.
- **Computer science:** Found in algorithms for searching, sorting, and data compression.
- **Nature:** Observed in spirals in sunflowers, seashells, and even galaxies.
- **Financial markets:** Used in technical analysis to predict price movements.
- **Art and music:** Employed in patterns, compositions, and aesthetics.

**Generating Fibonacci Numbers:**

Here are two common ways to generate Fibonacci numbers:

**1. Recursive Approach:**

```javascript
function fibonacciRecursive(n) {
  // Base case
  if (n < 2) {
    return n;
  }

  // Recursive case
  return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
}

// Example usage
const recursiveResult = fibonacciRecursive(10);
console.log("Recursive result:", recursiveResult);
```

This method defines a function `fibonacci` that takes a number `n` and recursively calls itself to calculate the `n`th Fibonacci number. It can be computationally expensive for larger values of `n`.

**2. Iterative Approach:**

```javascript
function fibonacciIterative(n) {
  // Initialize variables
  let a = 0;
  let b = 1;

  // Iterate up to the desired number
  for (let i = 0; i < n; i++) {
    const temp = a + b;
    a = b;
    b = temp;
  }

  return a;
}

// Example usage
const iterativeResult = fibonacciIterative(10);
console.log("Iterative result:", iterativeResult);
```

This approach uses two variables to store the previous two Fibonacci numbers and iteratively updates them to compute the next one. It's more efficient for bigger `n`.

**Two different ways to calculate the Fibonacci sequence in JavaScript:**

**Recursive Approach:**

```javascript
function fibonacci(num) {
  if (num <= 1) {
    return 1;
  }

  return fibonacci(num - 1) + fibonacci(num - 2);
}
```

This function uses **recursion** to calculate the nth Fibonacci number. Here's how it works:

1. **Base Case:** If `num` is less than or equal to 1, it returns 1 because the first two numbers in the sequence are 1 and 1.
2. **Recursive Case:** Otherwise, it calls itself twice with `num - 1` and `num - 2` as arguments. These represent the previous two Fibonacci numbers needed to calculate the current one.
3. The returned values from the recursive calls are added and returned as the `num`th Fibonacci number.

**Iterative Approach:**

```javascript
function fibonacci(num) {
  var a = 1,
    b = 0,
    temp;

  while (num >= 0) {
    temp = a;
    a = a + b;
    b = temp;
    num--;
  }

  return b;
}
```

This function uses an **iterative approach** to calculate the `num`th Fibonacci number. Here's how it works:

1. It initializes two variables `a` and `b` with the first two Fibonacci numbers (1 and 0).
2. It uses a `while` loop that iterates as long as `num` is non-negative.
3. Inside the loop, it performs the following:
   - It stores the current value of `a` in a temporary variable `temp`.
   - It updates `a` with the sum of `a` and `b`.
   - It updates `b` with the previous value of `a` stored in `temp`.
   - It decrements `num` by 1, effectively counting down the number of iterations needed.
4. After the loop completes, `b` holds the `num`th Fibonacci number, which is returned.

**Key Differences:**

- The recursive approach is concise but can be less efficient for large `num` values due to repeated function calls.
- The iterative approach is more efficient for larger `num` values but uses more explicit variables and steps.

Both approaches ultimately produce the same result, though the iterative approach is generally preferred for better performance with larger numbers.

> 💁‍♀️ take a note that `while` loop more faster than `recursive`.

## Big O notation

In a nutshell, [Big O notation](https://en.wikipedia.org/wiki/Big_O_notation) is a way to express the growth rate of an algorithm's execution time (or space complexity) in relation to the size of its input. It helps us compare and analyze the efficiency of different algorithms without getting bogged down in specific implementation details.

| Algorithm | Time Complexity | Space Complexity |
| --------- | --------------- | ---------------- |
| Recursive | O(2^n)          | O(n)             |
| Iterative | O(n)            | O(1)             |

## Recap

**Beyond the Basics:**

- The ratio of consecutive Fibonacci numbers approaches the **golden ratio** (φ ≈ 1.618) as `n` increases.
- The Fibonacci sequence can be extended to negative indices using different rules.
- Generalized Fibonacci sequences with different starting values or summation rules exist.

**Summary:**

- Recursive is slower than Iterative
- Recursive has more space complexity than Iterative
- Iterative is faster than Recursive
- Iterative has less space complexity than Recursive
- Iterative is better than Recursive
- Iterative is the best solution for Fibonacci calculation
