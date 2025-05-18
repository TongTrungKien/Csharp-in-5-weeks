## RUN YOUR FIRST PROGRAM
- Chạy được chương trình C# đầu tiên ("Hello World").
- Hiểu được vai trò của `Console.WriteLine()` và `Main()`.
- Biết cách khai báo biến và thao tác với chuỗi (`string`).
- Làm quen với các phương thức chuỗi như: `Trim()`, `Replace()`, `ToUpper()`, `Contains()`...
## BẮT ĐẦU VỚI CHƯƠNG TRÌNH ĐẦU TIÊN `HELLO WORLD `


Chương trình "Hello World" theo truyền thống được sử dụng để giới thiệu một ngôn ngữ lặp trình. dưới đây là chương trình trong **C#**

```typescript
//This line prints "Hello, World
Console.WriteLine("Hello, World");
```

- Dòng bắt đầu bằng `//` là một chú thích đơn. Chú thích dòng đơn của C# bắt đầu bằng `//` và tiếp tục đến cuối dòng.
- Hiện tại C# cũng hỗ trợ chú thích nhiều dòng. Chú thích nhiều dòng bắt đầu bằng `/*` và kết thúc bằng `*/`

`WriteLine` là phương thức (Method) của lớp (class) `Console` nằm trong `System` không gian tên (namespace), tạo ra đầu ra của chương trình. Lớp này được cung cấp bải các thư viện class chuẩn, theo mặc định, được tự động tham chiếu trong mọi chương trình **C#**

Một dạng chương trình khác yêu cầu bạn khai báo class và method chứa cho điểm vào của chương trình. Trình biên dịch tổng hợp các thành phần này khi bạn sử dụng các câu lệnh cấp cao nhất.
Định dạng thay thế này vẫn còn hiệu lực và chứa nhiều khái niệm cơ bản trong tất cả các chương trình **C#**. Nhiều mẫu **C#** hiện có sử dụng định dạng tương đương sau:

```typescript
using System;
using TourOfCsharp;

class Program
{
    static void Main()
    {
        // This line prints "Hello, World" 
        Console.WriteLine("Hello, World");
    }
}
```
- `Using System` Khai báo để sử dụng các lớp trong thư viện **.Net** (Trong đó có `Console`).
- `Class Program` Định nghĩa một tên lớp có tên là `Program` là nơi chứa điểm bắt đầu của ứng dụng.
- `Static void Main()` Là hàm chính nơi chương trình bắt đầu chạy
- `Console.WriteLine(...)` In nội dung ra màn hình console 

## KHAI BÁO VÀ SỬ DỤNG BIẾN
Chương trình đầu tiên của bạn in dòng chữ `string"Hello World!"` ra màn hình.

Chương trình đầu tiên của bạn chỉ giới hạn ở việc in một thông điệp. Bạn có thể viết nhiều chương trình hữu ích hơn bằng cách sử dụng biến . Biến là một ký hiệu bạn có thể sử dụng để chạy cùng một mã với các giá trị khác nhau. Hãy thử xem! Bắt đầu với mã sau:

```typescript
string aFriend = "Bill";
Console.WriteLine(aFriend);
```
Dòng đầu tiên khai báo một biến, `aFriend`, và gán cho nó một giá trị, "Bill". Dòng thứ hai in ra tên.

Bạn có thể gán các giá trị khác nhau cho bất kỳ biến nào bạn khai báo. Bạn có thể đổi tên thành một trong những người bạn của mình. Thêm hai dòng này vào cửa sổ tương tác trước đó theo sau mã bạn đã thêm. Đảm bảo bạn giữ nguyên khai báo `aFriend`biến và lệnh gán ban đầu của nó.

```typescript
aFriend = "Maira";
Console.WriteLine(aFriend);
```

Lưu ý rằng cùng một dòng mã sẽ in ra hai thông báo khác nhau, dựa trên giá trị được lưu trữ trong aFriendbiến.

Bạn có thể nhận thấy rằng từ "Hello" bị thiếu trong hai tin nhắn cuối cùng. Hãy sửa lỗi đó ngay bây giờ. Sửa đổi các dòng in tin nhắn thành mã sau:

```typescript
Console.WriteLine("Hello " + aFriend);
```

Bạn đã sử dụng `+` để xây dựng chuỗi từ các biến và chuỗi **hằng số** . Có một cách tốt hơn. Bạn có thể đặt một biến giữa `{`và `}`ký tự để yêu cầu C# thay thế văn bản đó bằng giá trị của biến.

Quá trình này được gọi là [nội suy chuỗi](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated).

Nếu bạn thêm a `$` trước dấu ngoặc kép mở đầu của chuỗi, bạn có thể bao gồm các biến, như `aFriend`, bên trong chuỗi giữa các dấu ngoặc nhọn. Hãy thử xem:

Chọn Chạy lại để xem kết quả. Thay vì "Xin chào {aFriend}", thông báo sẽ là "Xin chào Maira".

```typescript
Console.WriteLine($"Hello {aFriend}");
```

## LÀM VIỆC VỚI CHUỖI

Bạn có thể chèn nhiều biến vào cùng một chuỗi bằng cú pháp nội suy (`$"..."`):

```typescript
string firstFriend = "Maria";
string secondFriend = "Sage";
Console.WriteLine($"My friends are {firstFriend} and {secondFriend}");
```

 ***Nội suy chuỗi*** (String Interpolation) là cách chèn giá trị của biến trực tiếp vào trong chuỗi mà không cần dùng toán tử cộng (+). Từ C# 6.0 trở đi, cú pháp này giúp mã dễ đọc, ngắn gọn hơn.

**Cú pháp chuẩn**
```typescript
$"nội_dung_văn_bản {biến} nội_dung_tiếp_theo"
```
- Dấu $ đặt trước dấu nháy kép mở đầu của chuỗi.
- Các biến hoặc biểu thức được đặt bên trong {}.
- Chuỗi nội suy vẫn là kiểu string.

Chuỗi không chỉ là một tập hợp các chữ cái. Bạn có thể tìm độ dài của một chuỗi bằng cách sử dụng Length. Lengthlà một thuộc tính của một chuỗi và nó trả về số ký tự trong chuỗi đó. Thêm mã sau vào cuối cửa sổ tương tác:

```typescript
Console.WriteLine($"The name {firstFriend} has {firstFriend.Length} letters.");
Console.WriteLine($"The name {secondFriend} has {secondFriend.Length} letters.");
```

**Bạn đã sử dụng phương thức [Console.WriteLine](https://learn.microsoft.com/en-us/dotnet/api/system.console.writeline?view=net-9.0) để in tin nhắn. Phương thức là khối mã thực hiện một số hành động. Nó có tên để bạn có thể truy cập.**

## Các phương thức xử lý chuỗi
### `Trim()`, `TrimStart()`, `TrimEnd()`

Giả sử chuỗi của bạn có khoảng trắng đầu hoặc cuối mà bạn không muốn hiển thị. Bạn muốn cắt bớt khoảng trắng khỏi chuỗi. Phương thức **[Trim](https://learn.microsoft.com/en-us/dotnet/api/system.string.trim?view=net-9.0)** và các phương thức liên quan **[TrimStar](https://learn.microsoft.com/en-us/dotnet/api/system.string.trimstart)** và **[TrimEnd](https://learn.microsoft.com/en-us/dotnet/api/system.string.trimend)** thực hiện công việc đó. Bạn chỉ có thể sử dụng các phương thức đó để xóa khoảng trắng đầu và cuối. Hãy thử đoạn mã sau:

```typescript
string greeting = "      Hello World!       ";
Console.WriteLine($"[{greeting}]");

string trimmedGreeting = greeting.TrimStart();
Console.WriteLine($"[{trimmedGreeting}]");

trimmedGreeting = greeting.TrimEnd();
Console.WriteLine($"[{trimmedGreeting}]");

trimmedGreeting = greeting.Trim();
Console.WriteLine($"[{trimmedGreeting}]");
```
*Dấu ngoặc vuông `[`và `]` giúp hình dung các phương thức `Trim`, `TrimStart`,và , `TrimEnd` thực hiện chức năng gì. Dấu ngoặc vuông cho biết khoảng trắng bắt đầu và kết thúc ở đâu.*

| Phương thức           | Tác dụng                                                               |
| --------------------- | ---------------------------------------------------------------------- |
| `Trim()`              | Xóa **khoảng trắng** ở cả đầu và cuối chuỗi                            |
| `TrimStart()`         | Xóa **khoảng trắng đầu chuỗi** (bên trái)                              |
| `TrimEnd()`           | Xóa **khoảng trắng cuối chuỗi** (bên phải)                             |
| `Trim(params char[])` | Xóa **các ký tự tùy chọn** ở đầu/cuối chuỗi, không chỉ là khoảng trắng |


## THAY THẾ
Phương thức `Replace()` cho phép bạn tìm kiếm một chuỗi con trong một chuỗi và thay thế nó bằng chuỗi khác, tương tự như thao tác "Find and Replace" trong trình soạn thảo văn bản.
- Cú pháp
```typescript
originalString.Replace("chuỗi_cần_tìm", "chuỗi_thay_thế");
```
##### ***Trong ví dụ `originalString.Replace(...)`, `originalString` chỉ là một tên biến đại diện cho chuỗi ban đầu mà bạn muốn thao tác***
- Ví dụ

```typescript
string sayHello = "Hello World!";
Console.WriteLine(sayHello); // In ra: Hello World!

sayHello = sayHello.Replace("Hello", "Greetings");
Console.WriteLine(sayHello); // In ra: Greetings World!
```
| Phương thức                   | Tác dụng                                                            |
| ----------------------------- | ------------------------------------------------------------------- |
| `Replace(oldValue, newValue)` | Tìm tất cả chuỗi `oldValue` và thay bằng `newValue` trong chuỗi gốc |


## CHUYỂN ĐỔI CHỮ HOA/CHỮ THƯỜNG
Bạn có thể sử dụng hai phương thức sau để thay đổi toàn bộ ký tự trong chuỗi:

```typescript
Console.WriteLine(sayHello.ToUpper()); // In ra: GREETINGS WORLD!
Console.WriteLine(sayHello.ToLower()); // In ra: greetings world!
```
| Phương thức | Tác dụng                                      |
| ----------- | --------------------------------------------- |
| `ToUpper()` | Chuyển **toàn bộ chuỗi** thành chữ **IN HOA** |
| `ToLower()` | Chuyển **toàn bộ chuỗi** thành chữ **thường** |


## TÌM KIẾM CHUỖI
Phần khác của thao tác tìm kiếm và thay thế là tìm văn bản trong một chuỗi. Bạn có thể sử dụng phương thức Contains để tìm kiếm. Nó cho bạn biết liệu một chuỗi có chứa chuỗi con bên trong nó hay không. Hãy thử đoạn mã sau để khám phá Contains :

```typescript
string songLyrics = "You say goodbye, and I say hello";
Console.WriteLine(songLyrics.Contains("goodbye"));
Console.WriteLine(songLyrics.Contains("greetings"));
```
- Trả về `true` nếu chuỗi con xuất hiện trong chuỗi songLyrics.
- Trả về `false` nếu không tìm thấy.
- Kết quả trả về là kiểu [boolean(bool)](https://learn.microsoft.com/en-us/dotnet/api/system.boolean?view=net-9.0) (`true` / `false`).

| Phương thức  | Tác dụng                                                 | Kiểu trả về |
| ------------ | -------------------------------------------------------- | ----------- |
| `Contains()` | Kiểm tra xem chuỗi có chứa chuỗi con nhất định hay không | `bool`      |

## THỬ THÁCH
Có hai phương pháp tương tự, [StartsWith](https://learn.microsoft.com/en-us/dotnet/api/system.string.startswith) và [EndsWith](https://learn.microsoft.com/en-us/dotnet/api/system.string.endswith) cũng tìm kiếm các chuỗi con trong một chuỗi. Các phương pháp này tìm một chuỗi con ở đầu hoặc cuối chuỗi. Hãy thử sửa đổi mẫu trước đó để sử dụng [StartsWith](https://learn.microsoft.com/en-us/dotnet/api/system.string.startswith) và [EndsWith](https://learn.microsoft.com/en-us/dotnet/api/system.string.endswith) thay vì [Contains](https://learn.microsoft.com/en-us/dotnet/api/system.string.contains) . Tìm kiếm "You" hoặc `"goodbye" ở đầu chuỗi. Tìm kiếm "hello" hoặc "goodbye" ở cuối chuỗi.

*Bạn nên truebắt đầu bằng "You" và kết thúc bằng "hello" và falsebắt đầu hoặc kết thúc bằng "goodbye".*


## Link tham khảo
- https://learn.microsoft.com/en-us/dotnet/api/system.console.writeline
- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolatedinstall-visual-studio?view=vs-2022
- https://learn.microsoft.com/en-us/dotnet/api/system.string.trim
- https://learn.microsoft.com/en-us/dotnet/api/system.string.replace
- https://learn.microsoft.com/en-us/dotnet/api/system.string.contains
- https://learn.microsoft.com/en-us/dotnet/api/system.string.startswith
- https://learn.microsoft.com/en-us/dotnet/api/system.string.endswith
## HASHTAG

`Csharp-in-5-weeks` `Csharp`

## Author

[Dexter](https://github.com/TongTrungKien)
