+++
date = '2025-12-20T17:29:48+07:00'
draft = false
title = 'DOM Manipulation: Phù Thủy Điều Khiển Giao Diện'
summary = 'Tìm hiểu cách JavaScript tương tác với HTML thông qua DOM để tạo ra những phản hồi tức thì cho người dùng.'
+++

![Code on Screen](https://images.unsplash.com/photo-1498050108023-c5249f4df085?auto=format&fit=crop&q=80&w=1470)
*DOM là cầu nối biến các mã lệnh khô khan thành những chuyển động tinh tế.*

---

## 1. DOM Là Gì?
**DOM (Document Object Model)** là một cấu trúc dạng cây đại diện cho toàn bộ trang web. Khi JavaScript "chạm" vào DOM, nó có thể thay đổi bất kỳ nội dung hoặc màu sắc nào mà không cần tải lại trang.



## 2. Cách Mình "Giao Tiếp" Với Trang Web
Để điều khiển Blog, mình sử dụng các câu lệnh cơ bản nhưng quyền năng:

* **Lấy phần tử:** `document.querySelector()` giúp mình nhắm chính xác vào thẻ HTML cần đổi.
* **Lắng nghe sự kiện:** `addEventListener()` giúp trang web biết khi nào bạn nhấp chuột hoặc cuộn trang.

```javascript
// Thay đổi tiêu đề khi người dùng click
const title = document.querySelector('.article-title');
title.addEventListener('click', () => {
    title.style.color = '#d63384';
    alert('Cảm ơn bạn đã đọc bài viết!');
});