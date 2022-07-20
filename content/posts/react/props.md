---
title: "Props"
date: 2022-07-19T20:46:11+07:00
draft: true
description: "Props là gì? Dùng props khi nào?"
summary: "Props là gì? Dùng props khi nào?"
tags:
- React
- Tự học React
- JSX
- Props
---

## 1. Props là gì? Dùng props khi nào?

- Props là một dữ liệu mà được truyền từ thằng Component cha xuống cho Component con
- Props không thể nào tự động thay đổi trong component hiện tại
- Nếu như muốn thay đổi Props, bắt buộc phải có sự thay đổi từ Component cha (do cha truyển xuống), chính điều này sẽ giúp chúng ta tạo ra sự đa dạng cho Component

## 2. Props trong React elements

- Sử dụng props giống như với atribute của thẻ HTML
- Hai props class, for được chuyển thành className, htmlFor
- Phải tuân theo quy ước có sẵn.

## 3. Props  trong React components

- Sử dụng props giống như đối số cho Component
- Tự do đặt tên props
  - Đặt theo camelCase
  - Có thể bao gồm dấu gạch ngang


Ví dụ minh hoạ Props:

```
function PostItem(props) {
    return (
            <div className="post-item">
                <img src={props.image} alt={props.title} />
                <h2 className="post-title">{props.title}</h2>
                <p className="post-desc">{props.description}</p>
                <p className="post-published">{props.publishedAt}</p>
            </div>    
    )
}


function App(){
    return (
    <div class="posts-list">
        <PostItem
            title="C#(.NET) - Tương tác với file Excel"
            image="https://files.fullstack.edu.vn/f8-prod/blog_posts/311/6147eea9cef9c.png"
            description="Tiến hành đọc file dữ liệu => phân tích dữ liệu => Xuất ra file Excel theo mẫu cho sẵn."
            publishedAt="10 tháng trước"
        />
        <PostItem 
            title="C#(.NET) - Tương tác với file Excel"
            image="https://files.fullstack.edu.vn/f8-prod/blog_posts/311/6147eea9cef9c.png"
            description="Tiến hành đọc file dữ liệu => phân tích dữ liệu => Xuất ra file Excel theo mẫu cho sẵn."
            publishedAt="10 tháng trước"
        />
        <PostItem 
            title="C#(.NET) - Tương tác với file Excel"
            image="https://files.fullstack.edu.vn/f8-prod/blog_posts/311/6147eea9cef9c.png"
            description="Tiến hành đọc file dữ liệu => phân tích dữ liệu => Xuất ra file Excel theo mẫu cho sẵn."
            publishedAt="10 tháng trước"
        />
      
    </div>
)
}


ReactDOM.render(<App />, document.getElementById('root'))
```

## 4. Một số lưu ý

- Prop "key" là props đặc biệt
- Props cơ bản là đối số của Component => Props có thể là bất cứ kiểu dữ liệu gì
- Sử dụng destructuring