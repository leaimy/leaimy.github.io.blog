---
title: "useRef hook"
date: 2022-08-24T07:48:48+07:00
draft: true
description: "Tìm hiểu useRef hook"
summary: "Tìm hiểu useRef hook"
tags:
- useRef hook
- Hook
- React
- Tự học React
---

> useRef hook là một hàm trả về một object được gọi là current.

```jsx
const refContainer = useRef(initialValue);
```

## 1. Tổng quan về useRef hook

- useRef cho phép giữ lại giá trị giữa mỗi lần re-render.
- useRef có thể được sử dụng để lưu trữ một giá trị có thể thay đổi mà không re-render khi cập nhật.
- useRef có thể được sử dụng để truy cập trực tiếp vào một phần tử DOM.

## 2. Một số ví dụ minh hoạ

> #### Không gây ra Re-renders
>
>> Lưu các giá trị qua một tham chiếu bên ngoài

```jsx
import { useEffect, useRef, useState } from "react";

function App() {
  const [count, setCount] = useState(60);

  const timerId = useRef();

  const handleStart = () => {
    timerId.current = setInterval(() => {
      setCount((prevCount) => prevCount - 1);
    }, 1000);
  };

  const handleStop = () => {
    clearInterval(timerId.current);
  };

  return (
    <div className="App" style={{ padding: "40px" }}>
      <h1>{count}</h1>
      <button onClick={handleStart}>Start</button>
      <button onClick={handleStop}>Stop</button>
    </div>
  );
}

export default App;
```

> #### Theo dõi các thay đổi trạng thái
>
>> useRef hook được sử dụng để theo dõi các giá trị trạng thái trước đó. Bởi vì useRef giữ lại được các giá trị giữa mỗi lần Re-renders

```jsx
import { useEffect, useRef, useState } from "react";

function App() {
  const [count, setCount] = useState(60);

  const timerId = useRef();
  const prevCount = useRef();

  useEffect(() => {
    prevCount.current = count;
  }, [count]);

  const handleStart = () => {
    timerId.current = setInterval(() => {
      setCount((prevCount) => prevCount - 1);
    }, 1000);
  };

  const handleStop = () => {
    clearInterval(timerId.current);
  };
  console.log(count, prevCount.current);
  return (
    <div className="App" style={{ padding: "40px" }}>
      <h1>{count}</h1>
      <button onClick={handleStart}>Start</button>
      <button onClick={handleStop}>Stop</button>
    </div>
  );
}

export default App;
```

> Ví dụ trên sử dụng kết hợp `useEffect` và `useRef` để theo dõi trạng thái trước đó. Trong useEffect, tiến hành cập nhật lại `prevCount` mỗi khi giá trị `count` thay đổi.

> #### Truy cập các phần tử DOM
>
>> Trong React, thêm một ref thuộc tính vào một phần tử để truy cập nó trực tiếp trong DOM.

```jsx
import { useEffect, useRef, useState } from "react";

function App() {
  const [count, setCount] = useState(60);

  const timerId = useRef();
  const prevCount = useRef();
  const h1Ref = useRef();

  useEffect(() => {
    console.log(h1Ref.current);

    // Các thuộc tính của h1
    const rect = h1Ref.current.getBoundingClientRect();
    console.log(rect);
  });

  useEffect(() => {
    prevCount.current = count;
  }, [count]);

  const handleStart = () => {
    timerId.current = setInterval(() => {
      setCount((prevCount) => prevCount - 1);
    }, 1000);
  };

  const handleStop = () => {
    clearInterval(timerId.current);
  };
  console.log(count, prevCount.current);
  return (
    <div className="App" style={{ padding: "40px" }}>
      <h1 ref={h1Ref}>{count}</h1>
      <button onClick={handleStart}>Start</button>
      <button onClick={handleStop}>Stop</button>
    </div>
  );
}

export default App;
```


