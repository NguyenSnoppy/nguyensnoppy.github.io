+++
date = '2025-12-18T17:29:48+07:00'
draft = false
title = 'Java Networking: Kiên Trúc Kết Nối Trong Thế Giới Số'
summary = 'Khám phá gói thư viện java.net và cách Java thiết lập giao tiếp giữa các máy tính thông qua giao thức TCP/IP.'
+++

![Networking Concept](https://images.unsplash.com/photo-1544197150-b99a580bb7a8?auto=format&fit=crop&q=80&w=1470)
*Mạng máy tính không chỉ là những sợi cáp, đó là sự giao thoa của các luồng dữ liệu.*

---

## 1. Hệ Sinh Thái java.net
Java cung cấp một bộ công cụ cực kỳ mạnh mẽ để xử lý các tác vụ mạng thông qua gói `java.net`. Đây là nền tảng để xây dựng từ những ứng dụng đơn giản như gửi tin nhắn đến những hệ thống phân tán phức tạp. 

Để làm chủ lập trình mạng, chúng ta cần hiểu rõ 3 trụ cột:
- **IP Address (Định danh):** Địa chỉ duy nhất của mỗi thiết bị trong mạng.
- **Port (Cổng dịch vụ):** Các "cánh cửa" logic để phân loại dữ liệu (ví dụ: HTTP là cổng 80, HTTPS là 443).
- **Protocol (Giao thức):** Quy tắc giao tiếp, trong đó TCP và UDP là hai nhân vật chính.

## 2. Giao Thức TCP/IP: Sự Tin Cậy Tuyệt Đối
Trong các bài thực hành trên lớp, mình tập trung sâu vào **TCP (Transmission Control Protocol)**. Đây là giao thức hướng kết nối, đảm bảo dữ liệu gửi đi sẽ đến đích một cách toàn vẹn và đúng thứ tự.


*Cơ chế "Bắt tay 3 bước" giúp thiết lập một đường truyền an toàn trước khi dữ liệu chính thức được gửi đi.*

## 3. Quản Lý Địa Chỉ IP Trong Java
Java giúp việc thao tác với địa chỉ IP trở nên đơn giản thông qua lớp `InetAddress`. Đây là bước đầu tiên để chương trình của bạn biết nó đang nói chuyện với ai.

```java
import java.net.InetAddress;

public class NetworkInfo {
    public static void main(String[] args) {
        try {
            // Lấy thông tin IP từ tên miền
            InetAddress address = InetAddress.getByName("[www.google.com](https://www.google.com)");
            System.out.println("Host Name: " + address.getHostName());
            System.out.println("IP Address: " + address.getHostAddress());
        } catch (Exception e) {
            System.out.println("Không tìm thấy địa chỉ!");
        }
    }
}