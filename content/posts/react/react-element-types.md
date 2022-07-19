---
title: "React Element Types"
date: 2022-07-19T10:06:40+07:00
draft: true
description: "Tìm hiểu cách tạo ra React components thông qua việc hiểu bản chất đó là sử dụng React.createElement với type là function/class."
summary: "Tìm hiểu cách tạo ra React components thông qua việc hiểu bản chất đó là sử dụng React.createElement với type là function/class."
tags:
- React
- Tự học React
- JSX
- Component
- React Element Types
---
> Tại sao phải chia component?
>> Khi chia component hợp lý sẽ giúp dự án có cấu trúc rõ ràng, có tính kế thừa, các component chỉ cần viết 1 lần và có thể dùng ở nhiều chỗ.

## 1. Giới thiệu về Component

- Components cho phép bạn chia UI thành các phần độc lập, có thể tái sử dụng, và hoàn toàn tách biệt nhau.
- Chúng nhận vào bất kì đầu vào nào (còn được gọi là “props”) và trả về các React elements mô tả những gì sẽ xuất hiện trên màn hình.

## 2. Function Components

Cách đơn giản nhất để định nghĩa một component đó là viết một hàm JavaScript:

```
function Header() {
        return <div className="header">Header</div>
    }
```

Hàm này là một React component trả về một React element. Chúng ta gọi các components này là "function components" vì chúng là các hàm Javascript theo đúng nghĩa đen.

Render một component:

```
const app = <Header />
```

## 3. Class Components

Bạn cũng có thể sử dụng ES6 class để định nghĩa một component:

```
class Content extends React.Component {
        render() {
            return  <div className="content">Content</div>
        }
    }
```

Render một component:

```
const app = <Content />
```

Class component và Function component là tương đương nhau dưới góc độ của React.