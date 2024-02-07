---
author: Eka Prasetia
pubDatetime: 2020-06-10T20:30:00.737+07:00
title: useCallback to prevent re-created function
slug: usecallback-prevent-recreated-function
featured: false
ogImage: https://res.cloudinary.com/ddjsyskef/image/upload/v1707199786/prasetia-me/useCallback.png
tags:
  - react
description: React useCallback to avoid re-created function
---

## What is `useCallback`?

- `useCallback` is a React Hook introduced in React 16.8 that is used to **memoize callback functions**. Memoization essentially means caching the results of a function call based on its inputs, so that subsequent calls with the same inputs don't require recalculating the result. This is particularly useful for optimizing components to improve performance and prevent unnecessary re-renders.

## When to use `useCallback`:

- You need to pass a callback function as a prop to a child component, but you want to **avoid the child component re-rendering** whenever the parent component re-renders, even if the props haven't changed.
- You're using a callback function as an event handler within a component, and you want to **ensure the event handler remains the same identity** across re-renders, even if its dependencies haven't changed. This prevents unnecessary re-creations of the event handler, which can improve performance.

## How it works:

1. You call `useCallback` with two arguments:

   - **The callback function itself:** This is the function you want to memoize.
   - **An array of dependencies:** This array specifies the values that the callback function depends on. If any of these values change, the memoized callback function will be recreated. If the dependencies array is empty (`[]`), the callback function will only be created once.

2. `useCallback` returns a memoized version of the callback function. This function will have the same identity as long as its dependencies haven't changed. This means that if you pass the memoized function to a child component as a prop or use it as an event handler, React will be able to compare it to the previous version and determine if it has actually changed.

**Example:**

```javascript
import React, { useState, useCallback } from "react";

function ParentComponent() {
  const [count, setCount] = useState(0);
  const handleClick = useCallback(() => {
    setCount(count + 1);
  }, [count]); // Only recreate handleClick if count changes

  return (
    <div>
      <ChildComponent handleClick={handleClick} />
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

function ChildComponent({ handleClick }) {
  console.log("Child component rendered");
  // ...
}
```

In this example, `handleClick` is memoized using `useCallback` with `count` as a dependency. This ensures that `ChildComponent` only re-renders when `count` actually changes, even if `ParentComponent` itself re-renders due to other changes.

**Additional benefits:**

- `useCallback` can help reduce the number of child component re-renders, leading to improved performance.
- It can also be used to prevent memory leaks caused by stale event handlers.

**Remember:**

- Use `useCallback` judiciously, as unnecessary memoization can add overhead.
- Only memoize functions that are expensive to create or that have side effects.
- Be mindful of dependency arrays, as including unnecessary values can defeat the purpose of memoization.

## You can use `useCallback()` function to avoid re-created function

```jsx
import React, { useState, useCallback, useEffect } from "react";
import "./styles.css";

// Register functions
const functionsCounter = new Set();

export default function App() {
  const [counter, setCounter] = useState(0);
  const [otherCounter, setOtherCounter] = useState(0);

  // const increment = () => {
  //   setCounter(counter + 1);
  // }
  // const decrement = () => {
  //   setCounter(counter - 1);
  // }
  // const incrementOtherCounter = () => {
  //   setOtherCounter(otherCounter + 1)
  // }

  const increment = useCallback(() => {
    setCounter(counter + 1);
  }, [counter]);

  const decrement = useCallback(() => {
    setCounter(counter - 1);
  }, [counter]);

  const incrementOtherCounter = useCallback(() => {
    setOtherCounter(otherCounter + 1);
  }, [otherCounter]);

  useEffect(() => {
    functionsCounter.add(increment);
    functionsCounter.add(decrement);
    functionsCounter.add(incrementOtherCounter);
  }, [increment, decrement, incrementOtherCounter]);

  return (
    <div className="App">
      <h1>
        <code>useCallback()</code>
      </h1>
      <h3>{`function call: ${functionsCounter.size}`}</h3>
      <button onClick={decrement}>Decrement</button>
      {` ${counter} `}
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```

🚀 try [codesandbox](https://codesandbox.io/s/usecallback-k8zzs)

Thank you for reading this article, I hope you find it useful. Happy coding! 🔥
