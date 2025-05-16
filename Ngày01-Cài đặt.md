# Day 1: PREPARE THE WORKING ENVIRONMENT

## GIỚI THIỆU

Ngôn ngữ C# là ngôn ngữ phổ biến nhất cho nền tảng .NET – một môi trường phát triển miễn phí, đa nền tảng và mã nguồn mở. Các chương trình C# có thể chạy trên nhiều thiết bị khác nhau, từ thiết bị Internet of Things (IoT), máy tính cá nhân cho đến nền tảng điện toán đám mây và mọi hệ thống trung gian giữa chúng. 

Dựa trên nguyên lý lập trình hướng đối tượng, C# tích hợp nhiều đặc điểm từ các mô hình lập trình khác, trong đó có cả lập trình hàm. Các tính năng cấp thấp cho phép xử lý hiệu quả cao mà không cần viết mã không an toàn. Phần lớn runtime và thư viện của .NET được viết bằng C#

C# thuộc họ ngôn ngữ C. Cú pháp của C# sẽ quen thuộc nếu bạn từng dùng C, C++, JavaScript, TypeScript hoặc Java. Giống như C và C++, dấu chấm phẩy (`;`) được dùng để kết thúc câu lệnh. Tên định danh (identifier) trong C# phân biệt chữ hoa và chữ thường. C# cũng sử dụng dấu ngoặc nhọn { và } tương tự, có các câu lệnh điều kiện như `if`, `else`, `switch`, và các cấu trúc lặp như `for`, `while`. Ngoài ra, C# còn có câu lệnh `foreach` để duyệt qua bất kỳ kiểu tập hợp (collection) nào.

## CHUẨN BỊ

Để bắt đầu lập trình với C#, bạn cần chuẩn bị một số công cụ sau tùy theo nhu cầu và nền tảng:

IDE/Editor:

Nếu bạn muốn một trình soạn thảo nhẹ, linh hoạt, đa nền tảng: sử dụng Visual Studio Code (VS Code).

Nếu bạn cần môi trường phát triển đầy đủ, hỗ trợ tất cả tính năng của .NET: sử dụng Visual Studio (Community/Pro/Enterprise).

.NET SDK: Đây là bộ công cụ giúp biên dịch và chạy ứng dụng C#.

| Lựa chọn | Ưu điểm | Gợi ý sử dụng |
|---------|---------|----------------|
| [Visual Studio Code](https://code.visualstudio.com/) | Nhẹ, đa nền tảng, dễ mở rộng | Dành cho người mới học hoặc phát triển nhanh |
| [Visual Studio](https://visualstudio.microsoft.com/) | Đầy đủ tính năng, mạnh mẽ | Dành cho ứng dụng lớn, giao diện đồ họa, ASP.NET |

### Tiện ích mở rộng (nếu dùng VS Code)
- `C# DevKit`
- `IntelliCode`
- `EditorConfig`
- `.NET Install Tool for Extension Authors` (nếu cần)

Gợi ý: Nếu bạn dùng Visual Studio thì các thành phần cần thiết thường được tích hợp ngay trong quá trình cài đặt.

## TIẾN HÀNH

### CÀI ĐẶT VỚI VISUAL STUDIO CODE

1. **Cài .NET SDK**
   - Truy cập: [https://dotnet.microsoft.com/download](https://dotnet.microsoft.com/download)
   - Tải về và cài đặt bản SDK phù hợp với hệ điều hành của bạn (Windows/macOS/Linux).

2. **Cài Visual Studio Code**
   - Truy cập: [https://code.visualstudio.com/](https://code.visualstudio.com/)
   - Cài đặt theo hướng dẫn.

3. **Cài các tiện ích mở rộng**
   - Mở VS Code > Tab Extensions (Ctrl + Shift + X)
   - Cài đặt:
     - `C# DevKit`
     - `IntelliCode`
     - `EditorConfig`
     - (Tùy chọn) `.NET Install Tool for Extension Authors`

4. **Xác minh**
   ```bash
   dotnet --version

### CÀI ĐẶT VỚI VISUAL STUDIO

1. **Tải và cài đặt Visual Studio**
   - Truy cập: [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com/)
   - Tải bản Community miễn phí hoặc bản có license nếu cần.

2. **Chọn workload khi cài**

    - Gợi ý chọn:
        - `.NET desktop development`
        - `ASP.NET and web development (nếu làm web)`
        - Nhấn Install để cài đặt.

3. **Tạo project C# đầu tiên**

    - Mở Visual Studio > “Create a new project”
    - Chọn Console App

      ![image](https://github.com/user-attachments/assets/dc9bf70e-1901-427f-82b9-bdf0b5b8ecb1)

    - Đặt tên project của bạn và nhấn `next` là có thể viết chương trình đầu tiên của bạn


## KHỞI TẠO DỰ ÁN

Bây giờ bạn đã sẵn sàng để viết những dòng code C# đầu tiên. Hãy thử tạo một file `Program.cs` và chạy lệnh:

```
Console.WriteLine("Hello, World!");
```

- Ấn run hoặc `ctrl` + `F5` màn hình sẽ hiển thị ra kết quả như sau 

![image](https://github.com/user-attachments/assets/fb0bc74f-fe76-4c9c-ad3b-79cb71ffe8a5)



## NÊN CHỌN CÔNG CỤ NÀO? 

| Bạn là...                          | Nên dùng             |
| ---------------------------------- | -------------------- |
| Người mới học / muốn setup nhanh   | ✅ Visual Studio Code |
| Làm ứng dụng lớn, giao diện đồ họa | ✅ Visual Studio      |
| Dùng Linux / macOS                 | ✅ Visual Studio Code |

## Link tham khảo
- https://code.visualstudio.com/docs/setup/setup-overview
- https://learn.microsoft.com/en-us/visualstudio/install/install-visual-studio?view=vs-2022

## HASHTAG

#Csharp-in-5-weeks #Csharp

## Author

[Dexter](https://github.com/TongTrungKien)

