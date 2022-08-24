---
title: "React.memo HOC"
date: 2022-08-24T10:44:08+07:00
draft: true
description: "Tìm hiểu React.memo HOC"
summary: "Tìm hiểu React.memo HOC"
tags:
- React.memo HOC
- Hook
- React
- Tự học React
---

> - React.memo được gọi là Higher order component (HOC)
> - Dùng để ghi nhớ các props của một component, quyết định xem có render lại component đó hay không để tối ưu về hiệu năng.
>
> ***`React.memo` dùng để xử lý component tránh re-render trong tình huống không cần thiết.***


- Trong ví dụ này, Content thành phần hiển thị lại ngay cả khi các việc cần làm không thay đổi.

File *`App.js`*

```jsx
import { useState } from "react";
import Content from "./Content";

function App() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount(count + 1);
  };


  return (
    <div className="App" style={{ padding: "40px" }}>
      <Content />
      <h2>{count}</h2>
      <button onClick={handleClick}>Click me!</button>
    </div>
  );
}

export default App;
```

File *`Content.js`*

```jsx
const Content = () => {
  console.log("Re-renders");
  return <h1>Xin chào mọi người</h1>;
};

export default Content;

```

- Khi nhấn vào nút Click me, `Content` thành phần sẽ hiển thị lại.
- Nếu thành phần này phức tạp, nó có thể gây ra các vấn đề về hiệu suất.
- Sử dụng `memo` để khắc phục điều này.
- Sử dụng `memo` để giữ cho `Content` thành phần không cần phải kết xuất lại.

File *`App.js`*

```jsx
import { useState } from "react";
import Content from "./Content";

function App() {
  const [count, setCount] = useState(0);
  const [count2, setCount2] = useState(0);

  const handleClick = () => {
    setCount(count + 1);
  };

  const handleClick2 = () => {
    setCount2(count2 + 2);
  };

  return (
    <div className="App" style={{ padding: "40px" }}>
      <Content count={count} />
      <h2>{count}</h2>
      <h2>{count2}</h2>
      <button onClick={handleClick}>Click me!</button>
      <button onClick={handleClick2}>Click me 2!</button>
    </div>
  );
}

export default App;

```

File *`Content.js`*

```jsx
import { memo } from "react";

const Content = ({ count }) => {
  console.log("Re-renders");
  return <h1>Xin chào mọi người {count} </h1>;
};

export default memo(Content);

```

- Bây giờ `Content` thành phần chỉ hiển thị lại khi thành phần `count` được chuyển đến nó.
