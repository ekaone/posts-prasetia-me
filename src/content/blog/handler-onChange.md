---
author: Eka Prasetia
pubDatetime: 2020-04-26T15:57:52.737+07:00
title: React handler onChange
slug: react-handler-onchange
featured: false
ogImage: https://res.cloudinary.com/ddjsyskef/image/upload/v1707201521/prasetia-me/handleronchange.png
tags:
  - react
description: No more repetitive handler onChange.
---

**Understanding `onChange` in React:**

The `onChange` event handler is crucial for handling user input changes in various form elements like text inputs, checkboxes, radio buttons, and more. It triggers whenever the value of the element changes, allowing you to react to those changes and update your component's state accordingly.

**Key Considerations:**

- **Data Type:** Determine the data type you're working with (string, number, boolean, etc.) to choose the appropriate handling approach.
- **Single vs. Multiple Inputs:** Decide if you're dealing with a single input or multiple inputs that share the same handler.
- **Component State Updates:** Consider how you'll update the component's state based on the input change.

**Common approaches to handling `onChange` in React:**

1. **Single Input with String/Number Value:**

   - Create a state variable to store the input value.
   - Use the `onChange` handler to update the state variable using the event's `target.value`.

   ```javascript
   const [inputValue, setInputValue] = useState("");

   const handleChange = event => {
     setInputValue(event.target.value);
   };

   return <input type="text" value={inputValue} onChange={handleChange} />;
   ```

2. **Single Input with Checkbox/Radio Button:**

   - Use the `checked` attribute and state variable to reflect the checked state.
   - Update the state using the event's `target.checked` value in the `onChange` handler.

   ```javascript
   const [isChecked, setIsChecked] = useState(false);

   const handleChange = event => {
     setIsChecked(event.target.checked);
   };

   return <input type="checkbox" checked={isChecked} onChange={handleChange} />;
   ```

3. **Multiple Inputs with Shared Handler:**

   - Pass an identifier (e.g., name attribute) or index to differentiate inputs.
   - Use the `target.name` or `target.index` in the `onChange` handler to identify the changed input and update the corresponding state property.

   ```javascript
   const [inputs, setInputs] = useState({ name: "", email: "" });

   const handleChange = event => {
     setInputs({ ...inputs, [event.target.name]: event.target.value });
   };

   return (
     <form>
       <input
         type="text"
         name="name"
         value={inputs.name}
         onChange={handleChange}
       />
       <input
         type="email"
         name="email"
         value={inputs.email}
         onChange={handleChange}
       />
     </form>
   );
   ```

**Avoiding Repetitive Handler Functions:**

- **Named Handler Functions:** If the logic is complex or varies slightly, create named functions with descriptive names.
- **Arrow Functions:** For simple logic, consider using arrow functions within JSX for conciseness.
- **Higher-Order Components (HOCs):** For shared logic across components, create an HOC that encapsulates the `onChange` handling and wraps your components.

Another one, without repetitive handler onChange function, this approach can be one of solutions

```jsx
import React, { useState } from "react";

const Navbar = props => {
  return <input type="text" onChange={props.handlerChange("searchForm1")} />;
};

const View = props => {
  return <pre>{JSON.stringify(props.view, null, 2)}</pre>;
};

export default function App() {
  const [search, setSearch] = useState({
    searchForm1: "",
    searchForm2: "",
  });

  const handleChange = name => event => {
    setSearch({ ...search, [name]: event.target.value });
  };

  return (
    <>
      <Navbar handlerChange={handleChange} />
      <View view={search} />
    </>
  );
}
```

**Choosing the Right Approach:**

The best approach depends on your specific use case and complexity. Consider factors like component reusability, maintainability, and performance when making your decision.

I hope this comprehensive explanation helps you effectively handle `onChange` events in your React applications!
