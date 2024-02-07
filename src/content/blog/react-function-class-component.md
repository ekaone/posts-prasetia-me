---
author: Eka Prasetia
pubDatetime: 2020-05-05T20:00:52.737+07:00
modDatetime: 2022-01-05T18:00:47.500+07:00
title: React Function and Class Components
slug: react-function-class-component
featured: false
tags:
  - react
description: Different React Function and Class components.
---

In React, you have two main ways to define components: **function components** and **class components**. Both serve the same purpose—to create reusable blocks of UI—but they have different approaches and use cases.

**Function Components:**

- Defined as simple JavaScript functions that accept props (properties from parent components) as arguments and return JSX (a syntax extension for defining UI elements).
- Easier to write and understand, especially for simpler components.
- Don't have access to lifecycle methods (like `componentDidMount`) or state directly.
- Since React 16.8, can use hooks (like `useState`, `useEffect`) to handle state and side effects.

**Example:**

```javascript
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

**Class Components:**

- Defined as JavaScript classes that extend `React.Component`.
- More complex syntax, but offer lifecycle methods and direct state management.
- Suitable for components with complex behavior or interactions with external data sources.

**Example:**

```javascript
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  handleClick = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={this.handleClick}>Click me</button>
      </div>
    );
  }
}
```

Another ways sample React JS `Function` and `Class` components

## Function component

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

## Class component

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

## Demo

```jsx
import React from "react";
import ReactDOM from "react-dom";

function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

class WelcomeClass extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}

const element = <Welcome name="Eka" />;
const elementClass = <WelcomeClass name="Eka" />;

ReactDOM.render(element, document.getElementById("root"));
ReactDOM.render(elementClass, document.getElementById("root-class"));
```

**Choosing the Right Component:**

- **Simple UI:** Use function components for basic rendering without state or lifecycle needs.
- **Complex behavior or state:** Use class components for components with state management, external data fetching, or lifecycle methods.
- **Modern React:** Since React 16.8, function components with hooks are often preferred due to their simplicity and compatibility with future features.

**Additional Considerations:**

- **Performance:** Function components are generally considered slightly faster than class components, especially for simpler ones.
- **Readability:** Both can be readable, but function components with hooks sometimes provide cleaner syntax.
- **Community preference:** Function components with hooks are the current trend and often recommended in the React community.

Ultimately, the best choice depends on your specific component's needs and complexity. Consider all factors and experiment to find what works best for you and your project.

Thank you for reading this article, I hope you find it useful. Happy coding! 🔥
