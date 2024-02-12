---
title: Uncontrolled vs Controlled React Components
author: Eka Prasetia
pubDatetime: 2023-11-03T19:00:06.700+07:00
slug: uncontrolled-vs-controlled-react-components
featured: false
draft: false
tags:
  - react
description: Two prevalent approaches to managing components are uncontrolled and controlled components.
---

# Introduction

React offers developers various methods to manage and handle components within applications. Two prevalent approaches to managing components are `uncontrolled` and `controlled` components. While both serve the same purpose of managing user inputs and interactions, they differ significantly in their implementation and use cases.

## Uncontrolled Components:

Uncontrolled components in React are those where the component state is handled by the **DOM itself rather than by React**. This means that React doesn't have direct control over the values within these components. Instead, the state is managed by the DOM, and React simply interfaces with it. Uncontrolled components are typically initialized with default values and then allow the DOM to manage changes thereafter.

_Advantages of Uncontrolled Components:_

1. **DOM-Driven**: In an uncontrolled component, the form data is managed by the DOM itself. The DOM maintains the state of form elements (e.g., input values) independently.
2. **Integration with Non-React Code**: Uncontrolled components are useful when integrating React with non-React code. Since the source of truth remains in the DOM, it’s easier to work with external libraries or legacy code.
3. **Simplified Implementation**: Uncontrolled components are often simpler to implement, especially for forms with a large number of inputs. Since there's no need to manage state within React, developers can focus solely on the presentation layer.
4. **Better Performance**: Uncontrolled components can offer better performance in certain scenarios, especially when dealing with large forms. Since React isn't directly involved in managing the state, there's less overhead involved in re-rendering components.

_Disadvantages of Uncontrolled Components:_

1. **Limited Control**: With uncontrolled components, React relinquishes control over the component state to the DOM. This can lead to issues when trying to enforce certain validation rules or when integrating with other React features like `PropTypes` or `Context API`.
2. **Difficulty in Testing**: Testing uncontrolled components can be more challenging since the component state is not managed by React. This makes it harder to simulate user interactions and assert expected outcomes during testing.

_Example:_

```javascript
import React, { useRef } from "react";

function UncontrolledForm() {
  const inputRef = useRef(null);

  function handleSubmit(event) {
    event.preventDefault();
    console.log("Submitted value:", inputRef.current.value);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" ref={inputRef} defaultValue="John Doe" />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default UncontrolledForm;
```

In this example, the input field is uncontrolled because its value is managed by the DOM itself. The `defaultValue` attribute sets the initial value of the input field, but React doesn't control subsequent changes to its value.

## Controlled Components:

Controlled components, on the other hand, are components where React controls the state of the component. This means that React manages the component's state and updates it in response to user interactions. In controlled components, the component's state is kept in sync with React's state.

_Advantages of Controlled Components:_

1. **Full Control**: With controlled components, React maintains full control over the component's state. This allows for easier enforcement of validation rules, integration with other React features, and better overall predictability in application behavior.
2. **Improved Testing**: Testing controlled components is often easier since React manages the component's state. Developers can simulate user interactions by directly modifying the component's state and assert expected outcomes more effectively.
3. **State Management**: In a controlled component, the form data (such as input values) is stored in the component’s state. Each form element (like input, select, textarea) is associated with a state variable. When the user interacts with the form (typing, selecting, etc.), the component’s state is updated accordingly.
4. **Event Handling**: We use event handlers (like `onChange`) to capture user input. For instance, when the user types in an input field, the `onChange` event updates the corresponding state variable.

_Disadvantages of Controlled Components:_

1. **Increased Complexity**: Controlled components can be more complex to implement, especially for forms with a large number of inputs. Developers need to manage the component's state explicitly, which can lead to boilerplate code and increased cognitive load.
2. **Potential Performance Overhead**: Since React manages the component's state, there can be performance implications, especially for large forms or components with frequent updates. Re-rendering controlled components can be more resource-intensive compared to uncontrolled components.

_Example:_

```javascript
import React, { useState } from "react";

function ControlledForm() {
  const [name, setName] = useState("John Doe");

  function handleChange(event) {
    setName(event.target.value);
  }

  function handleSubmit(event) {
    event.preventDefault();
    console.log("Submitted value:", name);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={handleChange} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default ControlledForm;
```

In this example, the input field is controlled because its value is managed by React state. The `value` attribute is set to the `name` state variable, and the `onChange` event handler updates the state whenever the input value changes.

Thank you for reading this article. Happy coding! 🚀
