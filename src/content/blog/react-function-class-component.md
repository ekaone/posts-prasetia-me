---
author: Eka Prasetia
pubDatetime: 2020-05-05T20:00:52.737+07:00
title: Function and Class Components
slug: react-function-class-component
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - react
description: Different Function and Class components.
---

Simple demo React JS `Function` and `Class` components

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

🚀 more details [React JS component and props](https://reactjs.org/docs/components-and-props.html)

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
