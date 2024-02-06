---
author: Eka Prasetia
pubDatetime: 2021-10-15T18:00:00.700+07:00
title: React Cheatsheet
slug: react-cheatsheet
featured: false
tags:
  - react
description: Fibonacci numbers complex Time complexity
---

A quick reference guide of [React](https://react.dev/) that provides a summary of key concepts, syntax, and patterns used in React development. This cheatsheet is intended for developers who are already familiar with JavaScript and want to quickly review the essential aspects of React.

1. **JSX Syntax**: Describes the syntax for writing JSX (JavaScript XML), which is a syntax extension for JavaScript used in React.
2. **Components**: Explains how to create and use functional components and class components in React.
3. **Props**: Provides information on how to pass data between components using props.
4. **State**: Describes how to manage local component state and when to use it.
5. **Lifecycle Methods**: Summarizes the lifecycle methods available in functional components.
6. **Event Handling**: Covers how to handle events in React components.
7. **Conditional Rendering**: Explains how to conditionally render elements based on certain conditions.
8. **Lists and Keys**: Discusses how to render lists and the importance of using keys for efficient updates.
9. **Forms**: Provides guidance on handling forms in React.
10. **Hooks**: Introduces React Hooks, such as useState and useEffect, for managing state and side effects in functional components.
11. **Context API**: Explains how to use the Context API for managing global state.
12. **Routing**: Includes information on client-side routing in React applications.
13. **State Management Libraries**: Briefly introduces popular state management libraries like Redux, Zustand and MobX.

## Table of contents

## JSX Syntax

```jsx
import React from "react";

// Functional component using JSX
const MyComponent = () => {
  return (
    <div>
      <h1>Hello, React!</h1>
      <p>This is a simple JSX element in a React component.</p>
    </div>
  );
};

export default MyComponent;
```

💡[more info](https://react.dev/learn/writing-markup-with-jsx)

## Components

```jsx
import React from "react";
import MyComponent from "./MyComponent";

const App = () => {
  return (
    <div>
      <h1>My React App</h1>
      <MyComponent />
    </div>
  );
};

export default App;
```

💡[more info](https://react.dev/learn/importing-and-exporting-components)

## Props

```jsx
import React from "react";

// Functional component with JSX and props
const Greeting = props => {
  return (
    <div>
      <h1>Hello, {props.name}!</h1>
      <p>{props.message}</p>
    </div>
  );
};

// Example usage of the Greeting component
const App = () => {
  return (
    <div>
      <Greeting name="John" message="Welcome to my React app!" />
      <Greeting name="Alice" message="Have a great day!" />
    </div>
  );
};

export default App;
```

💡[more info](https://react.dev/learn/passing-props-to-a-component)

## State

```jsx
import React, { useState } from "react";

const Counter = () => {
  // useState hook to create a state variable 'count' with an initial value of 0
  const [count, setCount] = useState(0);

  // Event handler to increment the count
  const increment = () => {
    setCount(count + 1);
  };

  // Event handler to decrement the count
  const decrement = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <h1>Counter: {count}</h1>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

export default Counter;
```

💡[more info](https://react.dev/learn/state-a-components-memory)

## Lifecycle Methods

```jsx
import React, { useState, useEffect } from "react";

const FunctionalLifecycleExample = () => {
  // useState to manage component state
  const [count, setCount] = useState(0);

  // useEffect to mimic componentDidMount and componentDidUpdate
  useEffect(() => {
    console.log("Component did mount or update");
    return () => {
      console.log("Component will unmount");
    };
  }, [count]); // Dependency array to control when useEffect is called

  // Custom function to update count
  const handleClick = () => {
    setCount(prevCount => prevCount + 1);
  };

  console.log("Render method called");

  // Render the component's UI
  return (
    <div>
      <h1>Functional Lifecycle Example</h1>
      <p>Count: {count}</p>
      <button onClick={handleClick}>Increment Count</button>
    </div>
  );
};

export default FunctionalLifecycleExample;
```

💡[more info](https://react.dev/learn/lifecycle-of-reactive-effects)

## Event Handling

```jsx
import React, { useState } from "react";

const EventHandlingExample = () => {
  const [message, setMessage] = useState("");

  const handleInputChange = event => {
    setMessage(event.target.value);
  };

  const handleButtonClick = () => {
    alert(`Message: ${message}`);
  };

  return (
    <div>
      <h1>Event Handling Example</h1>
      <input type="text" onChange={handleInputChange} />
      <button onClick={handleButtonClick}>Show Message</button>
    </div>
  );
};
```

💡[more info](https://react.dev/learn/responding-to-events#adding-event-handlers)

## Conditional Rendering

```jsx
import React, { useState } from "react";

const ConditionalRenderingExample = () => {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  const handleLogin = () => {
    setIsLoggedIn(true);
  };

  const handleLogout = () => {
    setIsLoggedIn(false);
  };

  return (
    <div>
      {isLoggedIn ? (
        <div>
          <h1>Welcome, User!</h1>
          <button onClick={handleLogout}>Logout</button>
        </div>
      ) : (
        <div>
          <h1>Please log in</h1>
          <button onClick={handleLogin}>Login</button>
        </div>
      )}
    </div>
  );
};
```

💡[more info](https://react.dev/learn/conditional-rendering)

## Lists and Keys

```jsx
import React from "react";

const ListExample = () => {
  const items = ["Apple", "Banana", "Cherry", "Date"];

  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>{item}</li>
      ))}
    </ul>
  );
};
```

💡[more info](https://react.dev/learn/rendering-lists#keeping-list-items-in-order-with-key)

## Forms

```jsx
import React, { useState } from "react";

const FormExample = () => {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  const handleNameChange = event => {
    setName(event.target.value);
  };

  const handleEmailChange = event => {
    setEmail(event.target.value);
  };

  const handleSubmit = event => {
    event.preventDefault();
    alert(`Name: ${name}, Email: ${email}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label>Name:</label>
        <input type="text" value={name} onChange={handleNameChange} />
      </div>
      <div>
        <label>Email:</label>
        <input type="email" value={email} onChange={handleEmailChange} />
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};
```

Available on latest canary

```jsx
export default function Search() {
  function search(formData) {
    const query = formData.get("query");
    alert(`You searched for '${query}'`);
  }
  return (
    <form action={search}>
      <input name="query" />
      <button type="submit">Search</button>
    </form>
  );
}
```

💡[more info](https://react.dev/reference/react-dom/components/form)

## Hooks

```jsx
import React, { useState, useEffect } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
};
```

💡[more info](https://react.dev/reference/react/hooks)

## Context API

```jsx
import React, { createContext, useContext, useState } from "react";

// Create a context to store the user's authentication status
const AuthContext = createContext();

// Provider component to wrap the app and provide the context value
const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(null);

  const login = username => {
    setUser(username);
  };

  const logout = () => {
    setUser(null);
  };

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
};

// Custom hook to access the context value
const useAuth = () => {
  return useContext(AuthContext);
};

export { AuthProvider, useAuth };
```

💡[more info](https://react.dev/learn/passing-data-deeply-with-context)

## Routing

```jsx
import React from "react";
import { BrowserRouter as Router, Route, Link } from "react-router-dom";

const Home = () => <h1>Home</h1>;
const About = () => <h1>About</h1>;

const App = () => {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
          </ul>
        </nav>

        <Route path="/" exact component={Home} />
        <Route path="/about" component={About} />
      </div>
    </Router>
  );
};

export default App;
```

💡[more info](https://reactrouter.com/en/main)

## State Management Libraries

[MobX](https://mobx.js.org/): A simple, scalable state management library that makes it easy to manage the state of your React application. It uses observables to automatically track and update state changes.

[Recoil](https://recoiljs.org/): A state management library for React that is designed to be flexible and scalable. It introduces atoms, selectors, and a React hook API for managing state in a more intuitive way.

[Zustand](https://zustand-demo.pmnd.rs/): A small, fast, and lightweight state management library. It uses a hook-based API and is designed to be easy to use with minimal boilerplate.

[XState](https://xstate.js.org/): While originally designed for finite state machines, XState can also be used for more general state management. It's particularly powerful for managing complex UI behavior and asynchronous workflows.

[Valtio](https://valtio.pmnd.rs/): A proxy-state library for React. It's designed to provide reactivity with minimal boilerplate and integrates well with React's functional components.

[React Query](https://tanstack.com/query/v3/): While primarily focused on data fetching and caching, React Query can also be used for managing UI-related state in React applications. It excels in handling asynchronous data and side effects.

[Jotai](https://jotai.org/): A primitive and flexible state management library for React. It uses atoms and a custom hook-based API to provide a simple and scalable solution for managing state.

[Redux](https://redux.js.org/): A predictable state container for JavaScript apps. It helps manage the state of your application in a single store and provides a predictable way to update and access that state.
