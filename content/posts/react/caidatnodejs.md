---
title: "NodeJS"
date: 2022-07-21T14:58:21+07:00
draft: true
description: "NodeJS là gì? Tại sao phải sử dụng NodeJS? Cài đặt môi trường NodeJS."
summary: "NodeJS là gì? Tại sao phải sử dụng NodeJS? Cài đặt môi trường NodeJS."
tags:
- React
- Tự học React
- Create React App
- NodeJS
---

## 1. NodeJS là gì?

- NodeJS là một Javascript runtime.
- Khi cài NodeJS sẽ tạo ra môi trường độc lập để có thể thực thi code Javascript.
- Để NodeJS có thể chạy được Javascript thì bên trong nó, nó sử dụng Chrome's V8 JavaScript engine được phát triển bởi Google.

## 2. Tại sao phải sử dụng NodeJS?

- NodeJS giúp bật lên một web server mà không cần dùng đến live server nữa.
- NodeJS sẽ giải quyết được một số vấn đề lặp đi lặp lại code, khi cài NodeJS nó sẽ tự động cài quản lý thư viện npm mà npm có đầy đủ thư viện liên quan đến dự án React vậy nên không cần phải thêm react, reactdom, bable... trong từng dữ án nữa, mỗi dự án chỉ cần import rồi dùng thôi.

## 3. Cài đặt môi trường NodeJS

Cài trên máy Windown:

- Bước 1: Tắt VSCode
- Bước 2: Mở trình duyệt gõ từ khoá "NodeJS", sau đó vào trang nodejs.org, nếu thấy nút downloads thì click vào luôn.
- Bước 3: Tải bản Windows Installer (.msi), tuỳ vào hệ điều hành là 32 bit hay là 64 bit
- Bước 4: Sau khi tải về được tập tin cài đặt. Bạn hãy tiến hành cài đặt theo từng bước.
- Bước 5: Đọc và chấp nhận các yêu cầu của NodeJS về bản quyền
- Bước 6: Trong các bước tiếp theo thực hiện lần lượt theo hướng dẫn gợi ý mặc định của chương trình cài đặt.
- Bước 7: Sau khi đã thiết lập, chương trình được cài đặt vào máy tính. Trong bước cuối cùng nhấn Finish để hoàn thành bước cài đặt.
- Bước 8: Kiểm tra phiên bản, mở terminal ra rồi gõ các lệnh sau nếu ra số phiên bản thì thành công:
  - node -v
  - npm -v
  - npx -v
