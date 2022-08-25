---
title: "useMemo hook"
date: 2022-08-25T07:58:01+07:00
draft: true
description: "Tìm hiểu useMemo hook"
summary: "Tìm hiểu useMemo hook"
tags:
- useMemo hook
- Hook
- React
- Tự học React
---

> useMemo giúp tránh thực hiện lại một logic nào đó không cần thiết

## 1. Giới thiệu useMemo

- useMemo trả về một giá trị được ghi nhớ. Hãy xem ghi nhớ như một giá trị lưu vào bộ nhớ đệm để nó không cần phải tính toán lại.
- useMemo chỉ chạy khi một trong các phần phụ thuộc (deps) của nó cập nhật điều này làm cải thiện hiệu suất.

## 2. Ví dụ minh hoạ useMemo

- Trong ví dụ này, hàm total chạy trên mọi lần render.
- Khi thay đổi `name`, `price`, `products` sẽ gây ra sự chậm trễ trong quá trình thực thi.

```jsx
import { useMemo, useRef, useState } from "react";

function App() {
  const [name, setName] = useState("");
  const [price, setPrice] = useState("");
  const [products, setProducts] = useState([]);

  const nameRef = useRef();

  const handleSubmit = () => {
    setProducts([
      ...products,
      {
        name,
        price: +price,
      },
    ]);

    setName("");
    setPrice("");

    nameRef.current.focus();
  };

  const total = products.reduce((result, prod) => {
    console.log("Tính toán lại...");

    return result + prod.price;
  }, 0);

  return (
    <div className="App" style={{ padding: "40px" }}>
      <input
        ref={nameRef}
        value={name}
        placeholder="Nhập tên..."
        onChange={(e) => setName(e.target.value)}
      />
      <br />
      <input
        value={price}
        placeholder="Nhập giá..."
        onChange={(e) => setPrice(e.target.value)}
      />
      <br />
      <button onClick={handleSubmit}>Add</button>
      <br />
      Total: {total}
      <ul>
        {products.map((product, index) => (
          <li key={index}>
            {product.name} - {product.price}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;

```

- Để khắc phục sự cố hiệu suất này, sử dụng useMemo Hook để ghi nhớ `total`. Điều này sẽ làm cho chức năng chỉ chạy khi cần thiết.
- Sử dụng useMemo để kết thúc việc gọi `total`
- useMemo hook chấp nhận một tham số thứ hai để khai báo các phụ thuộc. `total` sẽ chỉ chạy khi các phụ thuộc (deps) của nó đã thay đổi.
- Trong ví dụ sau, hàm bên trong `total` sẽ chỉ chạy khi `products` được thay đổi chứ không phải `name` hoặc `price` thay đổi.

```jsx
import { useMemo, useRef, useState } from "react";

function App() {
  const [name, setName] = useState("");
  const [price, setPrice] = useState("");
  const [products, setProducts] = useState([]);

  const nameRef = useRef();

  const handleSubmit = () => {
    setProducts([
      ...products,
      {
        name,
        price: +price,
      },
    ]);

    setName("");
    setPrice("");

    nameRef.current.focus();
  };

  const total = useMemo(() => {
    const result = products.reduce((result, prod) => {
      console.log("Tính toán lại...");

      return result + prod.price;
    }, 0);
    return result;
  }, [products]);

  return (
    <div className="App" style={{ padding: "40px" }}>
      <input
        ref={nameRef}
        value={name}
        placeholder="Nhập tên..."
        onChange={(e) => setName(e.target.value)}
      />
      <br />
      <input
        value={price}
        placeholder="Nhập giá..."
        onChange={(e) => setPrice(e.target.value)}
      />
      <br />
      <button onClick={handleSubmit}>Add</button>
      <br />
      Total: {total}
      <ul>
        {products.map((product, index) => (
          <li key={index}>
            {product.name} - {product.price}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;
```

