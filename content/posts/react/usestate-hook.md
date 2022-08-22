---
title: "useState hook"
date: 2022-08-22T08:11:33+07:00
draft: true
description: "Tìm hiểu về useState hook"
summary: "Tìm hiểu về useState hook"
tags:
- useState hook
- Hook
- React
- Tự học React
---

> useState (Trạng thái của dữ liệu) ra đời để làm đơn giản hoá việc thể hiện trạng thái của dữ liệu sang giao diện người dùng.

### Dùng khi nào?

Khi muốn giao diện thay đổi thì giao diện tự động được cập nhật (render lại theo dữ liệu).

### Cách dùng

```jsx
import {useState} from 'react'

function Component() {
    const [state, setState] = useState(initState)

    ...

  }
```

> - useState() nhận đối số đầu vào vào là initState
> - initState là giá trị khởi tạo cho state, chỉ dùng một lần trong lần đầu thôi.
> - state là một biến lưu trữ được khởi tạo giá trị ban đầu là initState
> - setState là một hàm dùng để đặt lại giá trị cho state


### Lưu ý

> - Component được re-render sau khi setState, mỗi lần nhấn vào nút `Increase` thì hàm handleIncrease sẽ được thực hiện, mỗi lần setCounter thì tự động gọi lại hàm App (hàm App() sẽ được render lại sau mỗi lần gọi setCounter).
> - Initial state chỉ dùng lần đầu, lần đầu tiên chạy `counter` sẽ được đặt là 1 (giá trị khởi tạo) những lần sau `counter` sẽ được đặt bằng một giá trị `setCounter` trước đó.

```jsx
import { useState } from "react";
function App() {
  const [counter, setCounter] = useState(1);
  const handleIncrease = () => {
    setCounter(counter + 1);
  };
  return (
    <div className="App" style={{ padding: "20px" }}>
      <h1 >{counter}</h1>
      <button onClick={handleIncrease}>Increase</button>
    </div>
  );
}
export default App;
```

> Set state với callback? Nó sẽ lưu lại cái `counter` trước đó rồi render một lần (Gộp 3 setCounter lại rồi thực thi một lần).

```jsx
import { useState } from "react";
function App() {
  const [counter, setCounter] = useState(1);
  const handleIncrease = () => {
    setCounter((prev) => prev + 1);
    // setCounter((prev) => prev + 1);
    // setCounter((prev) => prev + 1);
  };
  return (
    <div className="App" style={{ padding: "20px" }}>
      <h1>{counter}</h1>
      <button onClick={handleIncrease}>Increase</button>
    </div>
  );
}

export default App;
```

> Initial state với callback? Đưa giá trị tính toán  vào làm giá trị khởi tạo nhằm tăng hiệu suất cho ứng dụng.

```jsx
import { useState } from "react";

const orders = [100, 200, 300];

function App() {
  const [counter, setCounter] = useState(() => {
    const total = orders.reduce((total, cur) => total + cur);
    return total;
  });
  const handleIncrease = () => {
    setCounter((prev) => prev + 1);
  };
  return (
    <div className="App" style={{ padding: "20px" }}>
      <h1>{counter}</h1>
      <button onClick={handleIncrease}>Increase</button>
    </div>
  );
}

export default App;
```

> Set state là thay thế state bằng giá trị mới. Khi setInfo được gọi chúng ta sẽ gán info một đối tượng mới. Trong đối tượng mới chúng ta sử dụng toán tử spread để đưa tất cả các giá trị cũ cho đối tượng mới và thêm một phần tử mới là `bio: "Yêu màu hồng"`

```jsx
import { useState } from "react";

const orders = [100, 200, 300];

function App() {
  const [info, setInfo] = useState({
    name: "Nguyễn Thị Hà",
    age: 18,
    address: "Phú Yên, Việt Nam",
  });
  const handleUpdate = () => {
    setInfo({
      ...info,
      bio: "Yêu màu hồng",
    });

    // Khi muốn viết logic thì dùng setState với callBack như bên dưới.
    // setInfo((prev) => {
    //   // Viết logic
    //   return {
    //     ...prev,
    //     bio: "Yêu màu hồng",
    //   };
    // });
  };
  return (
    <div className="App" style={{ padding: "20px" }}>
      <h1>{JSON.stringify(info)}</h1>
      <button onClick={handleUpdate}>Update</button>
    </div>
  );
}

export default App;

```