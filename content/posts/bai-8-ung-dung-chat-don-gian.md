+++
date = '2025-12-17T17:29:48+07:00'
draft = false
title = 'Socket Programming: Xây Dựng Ứng Dụng Chat Đa Người Dùng'
summary = 'Từ lý thuyết đến thực hành: Từng bước thiết lập Server và Client để tạo nên một hệ thống truyền tin thời gian thực bằng Java.'
+++

![Chat App Concept](https://images.unsplash.com/photo-1611746872915-64382b5c76da?auto=format&fit=crop&q=80&w=1470)
*Socket là nhịp cầu nối liền khoảng cách giữa các tiến trình trong mạng máy tính.*

---

## 1. Socket - Điểm Cuối Của Sự Giao Tiếp
Trong lập trình mạng, **Socket** được hiểu là một điểm cuối (endpoint) của một liên kết giao tiếp hai chiều giữa hai chương trình đang chạy trên mạng. Để một ứng dụng Chat hoạt động, chúng ta cần sự phối hợp nhịp nhàng giữa hai thành phần:

* **ServerSocket (Phía Server):** Đóng vai trò như một tổng đài viên, luôn ở trạng thái "lắng nghe" các yêu cầu kết nối từ phía khách hàng.
* **Socket (Phía Client):** Đóng vai trò như người gọi điện, chủ động thiết lập kết nối tới địa chỉ IP và Port của Server.



## 2. Luồng Dữ Liệu: InputStream và OutputStream
Khi kết nối đã được thiết lập, dữ liệu không tự nhiên di chuyển. Chúng ta cần sử dụng các "đường ống" dẫn dữ liệu:
- **OutputStream:** Để đẩy dữ liệu đi (gửi tin nhắn).
- **InputStream:** Để nhận dữ liệu về (đọc tin nhắn).

Để việc đọc/ghi dữ liệu hiệu quả hơn, mình sử dụng thêm `BufferedReader` và `PrintWriter` để xử lý văn bản theo từng dòng, tránh việc dữ liệu bị đứt quãng.

## 3. Hiện Thực Hóa Mã Nguồn (Demo Server)
Dưới đây là đoạn mã cốt lõi để khởi tạo một Server đơn giản, có khả năng nhận tin nhắn và phản hồi lại cho Client:

```java
import java.io.*;
import java.net.*;

public class SimpleServer {
    public static void main(String[] args) {
        try (ServerSocket serverSocket = new ServerSocket(5000)) {
            System.out.println("Server đang đợi kết nối tại cổng 5000...");
            
            Socket socket = serverSocket.accept(); // Chấp nhận kết nối
            System.out.println("Client đã kết nối thành công!");

            // Thiết lập luồng vào/ra
            BufferedReader input = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            PrintWriter output = new PrintWriter(socket.getOutputStream(), true);

            String message = input.readLine();
            System.out.println("Client gửi: " + message);
            
            output.println("Server đã nhận được tin: " + message);

        } catch (IOException e) {
            System.out.println("Lỗi Server: " + e.getMessage());
        }
    }
}