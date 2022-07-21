---
title: "Tạo dự án với React + Webpack"
date: 2022-07-21T16:08:42+07:00
draft: true
description: "Cách sử dụng Webpack để tạo một dự án làm việc với ReactJS"
summary: "Cách sử dụng Webpack để tạo một dự án làm việc với ReactJS"
tags:
- React
- Tự học React
- Create React App
- Tạo dự án với React + Webpack
---

## 1. Tìm hiểu Webpack

> Truy cập vào trang: <https://webpack.js.org/>   chúng ta sẽ thấy cái hình bên dưới:

![Webpack](/images/webpack.png)

- Webpack giúp chúng ta module hoá gần hết các file làm việc với Front-end như các file js, css, image...
- Đơn giản import, export các file có đuôi mở rộng như .js, .css, .jpg, .png...
- Một số ưu điểm khi dùng webpack:
- Giúp cho project dễ dàng phát triển, quản lý, customize
  - Tăng tốc độ cho project
  - Phân chia các module và chỉ load khi cần
  - Đóng gói tất cả file nguồn thành một file duy nhất, nhờ vào loader mà có thể biên dịch các loại file khác nhau
  - Biến các tài nguyễn tĩnh (image, css) trở thành 1 module
  - Chuyển đổi các mã nguồn: JSX, less, sass, scss thành js,... ES6->ES5 thông qua babel transpiler...

## 2. Tạo dự án với React + Webpack

#### Cấu trúc dự án

```
react-webpack # thư mục gốc
    | src # thư mục chứa source code chính
        | components # thư mục chứa components
        | index.js # File khởi tạo, render App vào #root
    | public
        | index.html # HTML page, nơi chứa #root element

```

#### Khởi tạo dự án

- Bước 1: Trong hướn dẫn này chúng ta sử dụng VSCode IDE. Mở VSCode rồi chọn File -> Add Folder to Workspace.
![Buoc1](/images/b1.png)
- Bước 2: Tiếp theo, bạn tự tạo một thư mục mới tên là react-webpack sau đó chọn thư mục đó và click vào Add.
![Buoc2](/images/b2.png)

#### Mở cửa sổ Terminal

![Buoc3](/images/b3.png)

Sau đó chạy dòng lệnh sau để khởi tạo dự án với Node:

```
npm init
```

> Gõ `npm init` vào Terminal sau đó nhấn phím Enter để chạy dòng lệnh.

Kết quả trông như sau:

![Buoc4](/images/b4.png)

Khi đó trong Terminal của bạn sẽ yêu cầu nhập một số thông tin để mô tả cho dự án của bạn. Bạn có thể nhập thông tin vào nếu muốn, trong hướng dẫn này mình để mặc định nên Enter hết.

![Buoc5](/images/b5.png)

Sau khi khởi tạo dự án thành công bạn sẽ thấy file package.json được tạo trong thư mục dự án.

![Buoc6](/images/b6.png)

> package.json là file chứa thông tin dự án như: tên dự án, phiên bản, mô tả, các thư viện được sử dụng trong dự án, v.v

#### Cài đặt webpack

Chạy lệnh sau để cài đặt 2 thư viện là webpack và webpack-cli:

```
npm install webpack webpack-cli --save-dev
```

> `--save-dev` để đánh dấu 2 thư viện này chỉ dùng trong khi phát triển, khi dự án đẩy lên production sẽ không có các thư viện này.

Sau khi lệnh trên chạy xong, `webpack` và `webpack-cli` sẽ được thêm vào `devDependencies`:

![Buoc7](/images/b7.png)

> `devDependencies` chứa các thư viện được cài đặt với flag `--save-dev`.

#### Cài đặt React và React-DOM

Chạy lệnh sau:

```
npm install react@17.0.2 react-dom@17.0.2 --save
```

> `--save` để thêm các thư viện được cài vào phần `dependencies` trong `package.json`. Đây là các thư viện được sử dụng trong dự án, bao gồm cả development & production. Từ phiên bản NPM 5 trở đi thì `--save` được thêm vào mặc định, nếu bạn đang sử dụng NPM >= 5 thì có thể không cần `--save`.

Sau khi cài đặt thành công:

![Buoc8](/images/b8.png)

## 3. Tài liệu tham khảo

<https://fullstack.edu.vn/blog/phan-1-tao-du-an-reactjs-voi-webpack-va-babel.html>
