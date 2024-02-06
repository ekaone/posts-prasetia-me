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

Without repetitive handler onChange function, this approach can be one of solutions

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
