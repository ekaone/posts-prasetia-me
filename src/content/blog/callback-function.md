---
author: Eka Prasetia
pubDatetime: 2020-06-10T20:30:00.737+07:00
title: useCallback to prevent re-created function
slug: usecallback-prevent-recreated-function
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - javascript
  - react
description: React useCallback to avoid re-created function
---

You can use `useCallback()` function to avoid re-created function

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