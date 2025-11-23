# Conditional structures

Bài viết này sẽ hướng dẫn các bạn về:

- `if`, `if-else`, `if` lồng nhau (*nested if-else*)
- `switch`
- Toán tử 3 ngôi `?:`

Các cấu trúc điều kiện `if`, `if-else`, toán tử điều kiện (toán tử 3 ngôi `?:`) và câu lệnh `switch` được dùng để điều khiển luồng thực thi của chương trình dựa trên giá trị của một biểu thức.

- Câu lệnh `if` chỉ thực thi một câu lệnh (hoặc một khối lệnh) khi biểu thức Boolean đi kèm được đánh giá là `true`.
- Câu lệnh `if-else` cho phép lựa chọn một trong hai nhánh lệnh dựa trên kết quả của biểu thức Boolean.
- Câu lệnh `if` lồng nhau (*nested if-else*) là việc đặt một câu lệnh `if` hoặc `if-else` bên trong thân của một câu lệnh `if`/`else` khác, thường dùng khi cần kiểm tra nhiều điều kiện phụ thuộc lẫn nhau.
- Toán tử điều kiện `?:` là dạng rút gọn của `if-else`, giúp viết những biểu thức gán hoặc trả về giá trị trong một dòng, ví dụ: `var result = condition ? valueIfTrue : valueIfFalse;`.
- Câu lệnh `switch` chọn một danh sách câu lệnh để thực thi dựa trên việc so khớp (pattern match) giữa giá trị của biểu thức và các nhánh `case` được định nghĩa trước.

# Câu lệnh `if`

## Mục đích

Câu lệnh `if` được dùng để **thực thi có điều kiện** một câu lệnh (hoặc một khối lệnh).  
Khối lệnh chỉ được chạy khi **biểu thức điều kiện** đi kèm được đánh giá là `true`.

Nói ngắn gọn:

> “Nếu điều kiện đúng thì thực hiện khối lệnh, nếu không thì bỏ qua.”

Trong C#, điều kiện của `if` **bắt buộc** phải là một biểu thức kiểu `bool`.

---
## Cú pháp cơ bản

```csharp
if (condition)
{
    // Các câu lệnh sẽ được thực thi khi condition == true
}
```
## Điều kiện Boolean và cách đánh giá biểu thức

Điều kiện trong câu lệnh `if` **bắt buộc** phải là một biểu thức kiểu `bool`, tức là kết quả chỉ có thể là `true` hoặc `false`.

Cách hiểu:

- Nếu biểu thức điều kiện cho kết quả **`true`** → khối lệnh trong `if` được thực thi.
- Nếu biểu thức điều kiện cho kết quả **`false`** → khối lệnh trong `if` bị bỏ qua.

Ví dụ:

```csharp
int age = 20;

if (age >= 18)          // age >= 18 là một biểu thức Boolean
{
    Console.WriteLine("Đủ 18 tuổi trở lên");
}
```


## ***Ví dụ `if` không có `else`***

```csharp
int number = 10;

if (number > 0)
{
    Console.WriteLine("number là số dương");
}

Console.WriteLine("Kết thúc chương trình");
```
- Điều kiện `number > 0` là `true` (vì `10 > 0`).

***Kết quả***

```csharp
number là số dương
Kết thúc chương trình
```
- Nếu `number = -5`, điều kiện `number > 0` là `false`, nên:

***Kết quả***

```csharp
Kết thúc chương trình
```
## Một số lưu ý khi dùng `if`

- **Điều kiện phải là kiểu `bool`**  
  Trong C#, điều kiện của `if` bắt buộc phải là một biểu thức trả về `true` hoặc `false`.
- Phân biệt giữa gán (`=`) và so sánh (`==`)

```csharp
if (x = 5)   //  Sai: đang gán 5 cho x, không phải so sánh
if (x == 5)  //  Đúng: so sánh x có bằng 5 hay không
{
    Console.WriteLine("x == 5");
}
```

- **Nên luôn dùng dấu ngoặc nhọn `{ }`, kể cả khi chỉ có một câu lệnh**

```csharp
if (x > 0)
    Console.WriteLine("x > 0");
    Console.WriteLine("Dòng này luôn chạy"); // Không nằm trong if

// Viết an toàn hơn:
if (x > 0)
{
    Console.WriteLine("x > 0");
    Console.WriteLine("Dòng này chỉ chạy khi x > 0");
}
```
- **Tránh điều kiện quá dài và khó đọc**
Nếu biểu thức điều kiện phức tạp (nhiều `&&`, `||`), nên tách nhỏ hoặc dùng biến trung gian:

```csharp
bool isOutOfRange = value < 0 || value > 100;

if (isOutOfRange)
{
    Console.WriteLine("Giá trị không hợp lệ");
}
```

- **Chú ý thứ tự điều kiện với `&&` và `||` (short-circuit)**
C# đánh giá từ trái sang phải và dừng sớm khi có thể:

```csharp
if (obj != null && obj.Age > 18) // An toàn, chỉ kiểm tra Age khi obj != null
{
    Console.WriteLine("Hợp lệ");
}
```

- **Đừng lạm dụng `if` cho những trường hợp có thể dùng `switch` hoặc toán tử 3 ngôi `?:`**

    - Nhiều nhánh rẽ theo giá trị một biến → cân nhắc dùng `switch`.

    - Gán giá trị đơn giản theo điều kiện → có thể dùng toán tử `?:`.




