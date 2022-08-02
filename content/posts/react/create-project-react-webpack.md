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


#### Cài đặt Babel

Chạy lệnh sau:

```
npm install @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev
```

- babel-core: Chuyển đổi ES6 về ES5
- babel-loader: Cho phép chuyển các files Javascript sử dụng Babel & Webpack
- babel-preset-env: Cài đặt sẵn giúp bạn sử dụng Javascript mới nhất trên nhiều môi trường khác nhau (nhiều trình duyệt khác nhau). Gói này đơn giản là support chuyển đổi ES6, ES7, ES8, ES… về ES5.
- babel-preset-react: Hỗ trợ chuyển đổi JSX về Javascript

Sau khi cài đặt xong:

![Buoc9](/images/b9.png)

#### Tạo index.html

Tại thư mục gốc của dự án hãy tạo file public/index.html và thêm vào cấu trúc HTML mặc định như sau:

![Buoc10](/images/b10.png)

> Thêm nhanh cấu trúc HTML mặc định với VSCode, gõ ! và nhấn Tab.

Tiếp theo, hãy tạo #root element:

![Buoc11](/images/b11.png)

#### Tạo file index.js

Tại thư mục gốc của dự án hãy tạo file src/index.js và thêm vào nội dung sau:

```
import React from 'react' // nạp thư viện react
import ReactDOM from 'react-dom' // nạp thư viện react-dom

// Tạo component App
function App() {
    return (
        <div>
            <h1>Xin chào mọi người!!!</h1>
        </div>
    )
}

// Render component App vào #root element
ReactDOM.render(<App />, document.getElementById('root'))


```
## 3. Cấu hình webpack
#### Cài đặt CSS-Loader và Style-Loader

2 thư viện này giúp webpack có thể tải file .css dưới dạng module.

Chạy:

```
npm install css-loader style-loader --save-dev
```

#### Tạo webpack.config.js

Tạo file webpack.config.js tại thư mục gốc của dự án với nội dung sau:
```
const path = require("path");

module.exports = {
  entry: "./src/index.js", // Dẫn tới file index.js ta đã tạo
  output: {
    path: path.join(__dirname, "/build"), // Thư mục chứa file được build ra
    filename: "bundle.js" // Tên file được build ra
  },
  module: {
    rules: [
      {
        test: /\.js$/, // Sẽ sử dụng babel-loader cho những file .js
        exclude: /node_modules/, // Loại trừ thư mục node_modules
        use: ["babel-loader"]
      },
      {
        test: /\.css$/, // Sử dụng style-loader, css-loader cho file .css
        use: ["style-loader", "css-loader"]
      }
    ]
  },
  // Chứa các plugins sẽ cài đặt trong tương lai
  plugins: [
  ]
};

```

Anh em lưu ý đặt file `webpack.config.js` ở thư mục gốc, ngang hàng với `package.json` nhé:

![Buoc12](/images/b12.png)


#### Tạo file .babelrc

File .babelrc dùng để cấu hình cho thư viện Babel.

> Lưu ý tên file bắt đầu bằng dấu .

Tại thư mục gốc dự án tạo file `.babelrc` và thêm nội dung sau:

```
{
    "presets": [
        "@babel/preset-env",
        "@babel/preset-react"
    ]
}
```

> Cài đặt này để cho Babel biết sử dụng preset-env và preset-react trong việc hỗ trợ chuyển đổi mã.

Đây là ảnh chụp file đã tạo:

![Buoc13](/images/b13.png)

#### Thêm scripts cho dự án

Tại package.json thêm nội dung sau:

```
"scripts": {
    ...
    "start": "webpack --mode development --watch",
    "build": "webpack --mode production"
}
```

Làm đúng thì trông nó sẽ như thế này:
![Buoc14](/images/b14.png)

> Cấu hình `scripts` này để bạn có thể chạy lệnh tương ứng qua Terminal. Ví dụ: `npm start` sẽ chạy lệnh ở phần `start`, `npm run build` sẽ chạy lệnh ở phần `build`. Trừ `start` ra thì bạn cần thêm từ `run` nữa nhé. 

## 4. Chạy dự án

#### Biên dịch code với Webpack

Tại Terminal hãy chạy:

```
npm start
```

> Lệnh này sẽ chạy `webpack --mode development --watch` mà ta đã cấu hình trong package.json, --watch để webpack sẽ luôn lắng nghe thay đổi, khi file thay đổi webpack sẽ thực hiện biên dịch nhé.

Kết quả trông như sau:
- Có file mới được tạo ra trong build/bundle.js (vì ta đã cấu hình như vậy trong `webpack.config.js`)
- Nội dung trong `build/bundle.js` chính là code của file src/index.js đã được Babel chuyển đổi, bạn có thể mở ra để quan sát.

Mọi người sẽ thấy có rất nhiều code trong này vì nó bao gồm cả code của những thư viện chúng ta đã import như: react và react-dom.


#### Chạy dự án với Live Server (VSCode)

Phần này chúng ta làm 2 việc:
- Thêm thẻ script link tới file build/bundle.js
- Chạy dự án với Live Server

Thêm nội dung sau vào vị trí như ảnh mô tả ở trên:
```
<script src="../build/bundle.js"></script>
```

Sau đó chạy Live Server và đạt được kết quả như sau là đã làm đúng:

Tiếp theo sẽ test xem webpack có đang lắng nghe thay đổi file không nhé (vì trong start chúng ta có sử dụng cờ --watch mà).

> Lưu ý không được tắt Terminal. Chạy dự án theo cách này phải luôn giữ cho Terminal chạy:

Thử đi sửa nội dung file src/index.js:


Nội dung website trên trình duyệt cũng thay đổi theo:


> Nhờ Live Server mà ta không cần F5 trang web

Tới đây hình dung flow chạy nó như này:

1. Webpack khi được chạy sẽ lắng nghe thay đổi của file
2. Khi file thay đổi Webpack sẽ biên dịch và update vào build/bundle.js
3. Website được chạy sẽ link file script từ build/bssundle.js
4. Live Server chạy web và lắng nghe thay đổi của build/bundle.js để F5 lại trang.


## 5. Cài đặt html-webpack-plugin

Tại sao phải cài thằng này làm gì? Ở phần trước chúng ta phải tự đi thêm thằng này vào index.html

Làm như này khá thủ công, chúng ta có thể tự động hoá nó vì rõ ràng ta đã mất công cấu hình trong Webpack rồi mà.

Chỗ này này:

Chính vì vậy html-webpack-plugin ra đời để giúp chúng ta "nhờ" Webpack sau khi build ra build/bundle.js thì thêm hộ chúng ta vào public/ index.html luôn.

Cài đặt:

npmin





## 3. Tài liệu tham khảo

<https://fullstack.edu.vn/blog/phan-1-tao-du-an-reactjs-voi-webpack-va-babel.html>
