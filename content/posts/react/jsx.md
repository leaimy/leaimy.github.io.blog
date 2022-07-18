---
title: "Tổng quan JSX"
date: 2022-07-18T14:18:41+07:00
draft: true
description: "JSX là gì? Tại sao cần JSX?"
summary: "JSX là gì? Tại sao cần JSX?"
tags:
- React
- Tự học React
- JSX
- Tổng quan JSX
---

> JSX là viết tắt của JavaScript XML.
>
> JSX cho phép chúng ta viết HTML trong React.
>
> JSX giúp viết và thêm HTML trong React dễ dàng hơn.
>
> JSX không phải là HTML

## 1. JSX là gì?

- JSX viết tắt là Javascript XML
- Nó transform cú pháp dạng gần như XML về thành Javascript. Giúp người lập trình có thể code ReactJS bằng cú pháp của XML thay vì sử dụng Javascript. Các XML elements, attributes và children được chuyển đổi thành các đối số truyền vào React.createElement.
- JSX cho phép chúng ta viết các phần tử HTML bằng JavaScript và đặt chúng trong DOM mà không cần bất kỳ phương thức createElement () và / hoặc appendChild () nào.
- Bạn không bắt buộc phải sử dụng JSX, nhưng JSX giúp bạn viết các ứng dụng React dễ dàng hơn.

## 2. Cú pháp của JSX

Ví dụ:

```
const title = 'Javascript'
        const ul =  <ul className="myclass" style={{color: 'pink', fontSize: '30px'}}>
            <li id='li-1'>{title}</li>
            <li>ReactJS</li>
        </ul>

ReactDOM.render(ul, document.getElementById('root'))
```

Một số lưu ý:

- Vì JSX gần với JavaScript hơn là so với HTML, React DOM sử dụng chuẩn quy tắc đặt tên camelCase cho thuộc tính thay vì dùng tên thuộc tính gốc của HTML. Ví dụ, class trở thành className trong JSX, và tabindex trở thành tabIndex.
- Bạn có thể nhúng bất kỳ biểu thức JavaScript hợp lệ bên trong JSX bằng cặp dấu ngoặc nhọn. Ví dụ, 2 + 2, user.firstName, hoặc formatName(user) đều là các biểu thức hợp lệ của JavaScript.
- Nếu tag rỗng (không có thẻ con), bạn có thể đóng nó ngay lập tức với />, giống XML:
`const element = <img src={user.avatarUrl} />;`

## 3. Babel là gì? Cách cài đặt Babel

> Các bạn có thể thử test Babel ở đây nhé: <https://bit.ly/2VOIMN7>

Minh hoạ:

![Babel](/images/babel.png)

Babel là một chuỗi công cụ chủ yếu được sử dụng để chuyển đổi mã ECMAScript 2015+ thành phiên bản JavaScript tương thích ngược trong các trình duyệt hoặc môi trường hiện tại và cũ hơn. Tóm lại những điều chính mà Babel có thể làm cho bạn:

- Babel là một trình biên dịch JavaScript có thể dịch các ngôn ngữ đánh dấu hoặc lập trình sang JavaScript.
- Với Babel, bạn có thể sử dụng các tính năng mới nhất của JavaScript (ES6 - ECMAScript 2015).
- Babel có sẵn cho các chuyển đổi khác nhau. React sử dụng Babel để chuyển đổi JSX thành JavaScript.

Các bước cài đặt Babel:

- Bước 1: thêm thẻ `<script>` vào trang của bạn: `<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>`
- Bước 2:  Thêm thuộc tính `type="text/babel"` vào bên trong thẻ `<script>`

Như code mẫu bên dưới:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JSX</title>
    <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
</head>
<body>

<script type="text/babel">

</script>
</body>
</html>
```

## 4. Tại sao cần JSX?

- Code JSX ngắn hơn, dễ hiểu hơn code JS.
- JSX không làm thay đổi ngữ nghĩa của Javascript
- Với cách viết gần với các thẻ HTML, nó giúp những developers thông thường (ví dụ như các designer) có thể hiểu được một cách dễ dàng, từ đó có thể viết hoặc sửa code mà không gặp nhiều khó khăn.
