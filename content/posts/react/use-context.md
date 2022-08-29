---
title: "useContext Hook"
date: 2022-08-29T08:41:18+07:00
draft: true
description: "Tìm hiểu useContex hook"
summary: "Tìm hiểu useContex hook"
tags:
  - useContext hook
  - Hook
  - React
  - Tự học React
---

> Đơn giản hoá việc truyền dữ liệu từ component cha xuống component con mà không cần sử dụng tới props

## 1. Tổng quan useContext hook

- React Context là một cách để quản lý trạng thái (state) toàn cục.
- React Context có thể được sử dụng cùng với `useState` Hook để chia sẻ trạng thái giữa các thành phần lồng vào nhau dễ dàng hơn so với một mình `useState`.

## 2. Ví dụ minh hoạ useContext hook

- Trạng thái nên được giữ bởi thành phần cha cao nhất trong ngăn xếp yêu cầu quyền truy cập vào trạng thái.
- Để minh hoạ chúng ta có nhiều thành phần lồng nhau. Thành phần ở trên cùng hoặc dưới cùng của ngăn xếp cần có quyền truy cập vào trạng thái.

> Khi chưa sử dụng React Context: Chuyển `props` qua các `component` lồng nhau

File _`App.js`_

```jsx
import { useState } from "react";
import Content from "./Context/Content";
import "./App.css";

function App() {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () => {
    setTheme(theme === "dark" ? "light" : "dark");
  };
  return (
    <div style={{ padding: "20px" }}>
      <button onClick={toggleTheme}>Toggle theme</button>
      <Content theme={theme} />
    </div>
  );
}

export default App;
```

File _`Content.js`_

```jsx
import Paragraph from "./Paragraph";
const Content = ({ theme }) => {
  return <Paragraph theme={theme} />;
};

export default Content;
```

File _`Paragraph.js`_

```jsx
const Paragraph = ({ theme }) => {
  console.log(theme);
  return (
    <p className={theme}>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
      veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
      commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
      velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
      cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id
      est laborum.
    </p>
  );
};

export default Paragraph;
```

> Khi sử dụng Context

File _`App.js`_

```jsx
import { useState, createContext } from "react";
import Content from "./Context/Content";
import "./App.css";

const ThemeContext = createContext();

function App() {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () => {
    setTheme(theme === "dark" ? "light" : "dark");
  };
  return (
    <ThemeContext.Provider value={theme}>
      <div style={{ padding: "20px" }}>
        <button onClick={toggleTheme}>Toggle theme</button>
        <Content />
      </div>
    </ThemeContext.Provider>
  );
}

export default App;
```

File _`Content.js`_

```jsx
import Paragraph from "./Paragraph";
const Content = () => {
  return <Paragraph />;
};

export default Content;
```

File _`Paragraph.js`_

```jsx
import { useContext } from "react";
import { ThemeContext } from "../App.js";

const Paragraph = () => {
  const theme = useContext(ThemeContext);

  return (
    <p className={theme}>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
      veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
      commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
      velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
      cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id
      est laborum.
    </p>
  );
};

export default Paragraph;
```
