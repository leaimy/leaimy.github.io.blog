---
title: "Tạo phần tử trong React"
date: 2022-07-15T20:28:57+07:00
draft: true
description: "React.createElement()"
summary: "React.createElement()"
tags:
- React
- Tự học React
- Tạo phần tử trong React
---

## 1. React.createElement() (React element)

> Cú pháp: React.createElement(component, props, ...children)

React.createElement() chấp nhận 3 tham số:

- Component hoặc Tag để sử dụng tạo element
- Props của component
- Children

Ví dụ:

```
React.createElement('div', { className: 'container' }, 'Hello World')
 ```

## 2. So sánh với document.createElement() (DOM element)

#### DOM element

Ví dụ có 1 thẻ `body` như sau

```
<body> </body>
```

Bây giờ muốn thêm

```
 <h1 title="Hello" class="heading">Hello Hà!</h1>
 ```

 vào thẻ body đó có thể sử dụng DOM element của javascript như sau:

 ```
        const h1DOM = document.createElement('h1')

         h1DOM.title = "Hello"
         h1DOM.className = "heading"

         h1DOM.innerText = "Hello guys!"

         document.body.appendChild(h1DOM)
 ```

 Những gì đang làm ở đây là:

- Tạo một element div mới bằng cách sử dụng `document.createElement` và sau đó đặt `class` và `innerText` của nó
- Nối element mới tạo này vào body element

 Đoạn HTML sau sẽ được tạo ra:

 ```
<body>
    <h1 title="Hello" class="heading">Hello Hà!</h1>
</body>
 ```

#### React element

Bây giờ để tạo phần tử này

```
 <h1 title="Hello" class="heading">Hello Hà!</h1>
 ```

 vào bằng React chúng ta thực hiện như sau:

 ```
      const h1React = React.createElement('h1', {
             title: 'Hello',
             className: 'heading'
         }, 'Hello guys!')
 ```

 Để xem kết quả hiển thị trong cửa sổ console chúng ta gõ lệnh in ra:
`console.log(h1React)`

## 3. Thay đổi: id, className, style

Cho đoạn HTML sau:

```
  <ul style="color: pink; font-size:30px">
        <li id='li-1'>Javascript</li>
        <li>ReactJS</li>
  </ul>
```

Tạo phần tử bằng React như sau:

```
 const ulReact = React.createElement(
            'ul',
            {
                style: 'color: pink; font-size: 30px'
            },
            React.createElement('li', { id: 'li-1'}, 'Javascript'),
            React.createElement('li', {}, 'ReactJS'),
)

console.log(ulReact)
```

Vào cửa sổ console để xem kết quả

## 4. Bài tập

Cho một đoạn HTML:

```
<div class="post-item">
    <h2 title="Học React tại F8">Học ReactJS</h2>
    <p>Học ReactJS từ cơ bản tới nâng cao</p>
</div>
```

Yêu cầu dùng React.createElement() tạo ra đoạn HTML trên.
