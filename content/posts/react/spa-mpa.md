---
title: "SPA & MPA"
date: 2022-07-14T17:43:56+07:00
draft: true
description: "Mô tả SPA & MPA"
summary: "Mô tả SPA & MPA"
tags:
- SPA
- MPA
- SPA & MPA
- React
- Tự học React
---

## 1. SPA - Single Page Application

- SPA là một loại ứng dụng web được tải từ một trang và tất cả tương tác của người dùng với dịch vụ này được thực hiện, sử dụng trên một trang duy nhất.
- SPA là một cách tiếp cận hiện đại để phát triển ứng dụng
- SPA là một ứng dụng hoạt động bên trong trình duyệt và không yêu cầu tải lại trang trong quá trình sử dụng
- ReactJS là một trong những thư viện tạo ra SPA
- Các "ông lớn" sử dụng SPA: Google, Facebook, Twitter
- Các SPA khác: F8, Shoppe, 30shine, chotot, zingmp3
- SPA có thể được gọi là CSR - Client side rendering (Thực hiện việc render giao diện ở phía máy người dùng)

![SPA](/images/spa.png)

## 2. MPA - Multi Page Application

- MPA là một ứng dụng web bao gồm một số lượng lớn các trang được làm mới hoàn toàn mỗi khi dữ liệu thay đổi trên chúng. Mọi thay đổi dữ liệu hoặc chuyển dữ liệu đến máy chủ đều dẫn đến một trang mới được hiển thị trong trình duyệt.
- MPA là một cách tiếp cận cổ điển để phát triển trang web.
- MPA yêu cầu tải lại trang mỗi khi nội dung thay đổi.
- MPA là một lựa chọn ưu tiên cho các công ty lớn có danh mục sản phẩm phong phú, chẳng hạn như các doanh nghiệp thương mại điện tử.
- Các trang web sử dụng MPA như: vnExpress, dlu.edu.vn...

## 3. So sánh SPA & MPA

### Tốc độ

- SPA nhanh hơn khi sử dụng
  - Phần lớn tài nguyên được tải trong lần đầu
  - Trang chỉ tải thêm dữ liệu mới khi cần
- MPA chậm hơn khi sử dụng
  - Luôn tải lại toàn bộ trang khi truy cập và chuyển hướng

### Bóc tách

- SPA có phần Front-end riêng biệt
- MPA Front-end & Back-end phụ thuộc nhau nhiều hơn, được đặt trong cùng 1 dự án

### SEO

- SPA không thân thiện với SEO như MPA
- Trải nghiệm trên thiết bị di động tốt hơn

### UX (Trải nghiệm của người dùng)

- SPA cho trải nghiệm tốt hơn, nhất là các thao tác chuyển trang
- Trải nghiệm trên thiết bị di động tốt hơn

### Quá trình phát triển

- SPA dễ dàng tái sử dụng code (component)
- SPA bóc tách FE & BE
  - Chia team phát triển song song
  - Phát triển thêm mobile app dễ dàng

### Phụ thuộc Javascript

- SPA phụ thuộc hoàn toàn vào JS
- MPA có thể không cần JS
