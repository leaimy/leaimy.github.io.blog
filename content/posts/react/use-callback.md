---
title: "useCallback hook"
date: 2022-08-24T13:51:53+07:00
draft: true
description: "Tìm hiểu useCallback hook"
summary: "Tìm hiểu useCallback hook"
tags:
- useCallback hook
- Hook
- React
- Tự học React
---

> `useCallback` giúp tránh tạo ra những hàm mới một cách không cần thiết trong function component.

## 1. Giới thiệu useCallback

- `useCallback` trả về một hàm gọi lại đã ghi nhớ
- `useCallback` chỉ chạy khi một trong các phần phụ thuộc của nó cập nhật.
- `useCallback` được dùng để tối ưu quá trình render của React functional components.
- `useCallback` rất hữu ích đối với trường hợp một component liên tục được hiển thị lại không cần thiết.
- `useCallback` chỉ nên sử dụng cho những component có khả năng chậm, xử lý tác vụ nặng.
- Không nên lạm dụng quá đà `useCallback` vì nó cũng có nhược điểm, chủ yếu là độ phức tạp của code. 

## 2. Ví dụ minh hoạ

- Một lý do để sử dụng `useCallback` là ngăn chặn một `component` Re-rendering trừ khi các props của nó thay đổi.
- Trong ví dụ này, component `Content` sẽ không re-render trừ khi `handleClick` thay đổi:

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
      <Content handleClick={handleClick} />
      <h1>{count}</h1>
    </div>
  );
}

export default App;
```

File *`Content.js`*

```jsx
import { memo } from "react";

const Content = ({ handleClick }) => {
  console.log("Re-renders");
  return (
    <>
      <h1>Xin chào mọi người</h1>
      <button onClick={handleClick}>Click me!</button>
    </>
  );
};

export default memo(Content);
```

- Hãy thử chạy chương trình và nhấn vào nút `Click me!`, component `Content` sẽ re-render ngay cả khi `handleClick` không thay đổi.
- Sử dụng `memo`, vì vậy component `Content` không nên hiển thị lại vì `handleClick` không thay đổi khi số lượng tăng lên.
- Điều này là do một thứ gọi là "referential equality" (===)
- Mỗi khi component hiển thị, các hàm sẽ được tạo lại, hàm như nhau nhưng mỗi lần re-render thì sẽ khác địa chỉ lưu trữ. Bởi vì điều này, hàm `handleClick` đã thực sự thay đổi.

- Sử dụng useCallback hook để ngăn hàm được tạo lại trừ khi cần thiết.

File *`App.js`*

```jsx
import { useCallback, useState } from "react";
import Content from "./Content";

function App() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    setCount((prev) => prev + 1);
  }, []);

  return (
    <div className="App" style={{ padding: "40px" }}>
      <Content handleClick={handleClick} />
      <h1>{count}</h1>
    </div>
  );
}

export default App;
```

File *`Content.js`*

```jsx
import { memo } from "react";

const Content = ({ handleClick }) => {
  console.log("Re-renders");
  return (
    <>
      <h1>Xin chào mọi người</h1>
      <button onClick={handleClick}>Click me!</button>
    </>
  );
};

export default memo(Content);
```

- Bây giờ component `Content` sẽ chỉ re-render khi prop `handleClick` thay đổi.
