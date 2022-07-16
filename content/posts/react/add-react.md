---
title: "Thêm React & React-DOM vào Website"
date: 2022-07-15T15:37:34+07:00
draft: true
description: "Thêm React vào Website, Github, NPMJS, UNPKG"
summary: "Thêm React vào Website, Github, NPMJS, UNPKG"
tags: 
- React
- Tự học React
- Thêm React & React-DOM vào Website
- Github, NPMJS, UNPKG
---

## 1. Github, NPMJS, UNPKG

> Mã nguồn React: [https://github.com/facebook/react](https://github.com/facebook/react)

- Không sử dụng trực tiếp mã nguồn của React , bên github chỉ dùng để lưu trữ mã nguồn thôi.

> Đường dẫn NPMJS: [https://www.npmjs.com](https://www.npmjs.com)

- NPMJS là viết tắt của Node Package manager Javascript (quản lý gói cho node), để tải thư viện React trên npm về sử dụng ta gõ cú pháp:  npm i react

> Đường dẫn UNPKG:  [https://unpkg.com](https://unpkg.com)

- UNPKG có tác dụng lấy các thư viện được lưu trữ ở NPMJS dưới dạng là cdn (content delivery network - mạng lưới phân phối nội dung).

## 2. Thêm React & React-DOM vào Website theo cú pháp cdn

> Copy cái này:  `<script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>` dán bên dưới thẻ title trong file html để thêm React vào Website
> Sau đó copy cái này: `<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>` dán bên dưới cú pháp trên để thêm React-DOM vào Website

Giống đoạn code phía dưới:
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ReactJS</title>
    <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
</head>
<body>
    <h1>Add React to website</h1>
      <script>

     </script>
     </body>
</html>
```

- Để kiểm tra nhúng thư viện React và React-DOM vào trang web có thành công hay không chúng ta tiến hành gõ lệnh *React* trên cửa sổ console

## 3. Tài liệu chính thức của React

> Tài liệu React: [https://reactjs.org/](https://reactjs.org/)
