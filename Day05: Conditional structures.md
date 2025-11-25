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

# Câu lệnh `if-else` 

## Cách hoạt động của nhánh `else`

Câu lệnh `if-else` cho phép bạn **chọn một trong hai nhánh lệnh** để thực thi, tùy thuộc vào kết quả của biểu thức điều kiện.

- Nếu điều kiện trong `if` **đúng** (evaluates to `true`), thì khối lệnh trong `if` sẽ được thực thi.
- Nếu điều kiện trong `if` **sai** (evaluates to `false`), khối lệnh trong `else` sẽ được thực thi.

***Cú pháp:***

```csharp
if (condition)
{
    // Câu lệnh thực thi khi điều kiện đúng (true)
}
else
{
    // Câu lệnh thực thi khi điều kiện sai (false)
}
```

## Khi nào nên sử dụng `if-else` thay vì `if` đơn?

Dùng `if-else` khi cần kiểm tra và thực hiện hai hành động đối lập nhau (một cái thực thi khi đúng, cái còn lại khi sai).

Nếu chỉ có một hành động cần thực thi khi điều kiện đúng và không cần gì khi điều kiện sai, thì có thể dùng `if` đơn mà không cần else.

***Ví dụ:***

- Dùng if-else khi bạn cần xử lý hai trường hợp khác nhau:

```csharp
if (score >= 60)
{
    Console.WriteLine("Đạt yêu cầu");
}
else
{
    Console.WriteLine("Không đạt yêu cầu");
}
```
- Dùng if đơn nếu không cần làm gì khi điều kiện sai:

```csharp
if (score >= 60)
{
    Console.WriteLine("Đạt yêu cầu");
}
```
## Ví dụ minh họa

```csharp
DisplayWeatherReport(15.0);  // Output: Cold.
DisplayWeatherReport(24.0);  // Output: Perfect!

void DisplayWeatherReport(double tempInCelsius)
{
    if (tempInCelsius < 20.0)
    {
        Console.WriteLine("Cold.");
    }
    else
    {
        Console.WriteLine("Perfect!");
    }
}
```
***Kết quả***

```csharp
Nếu tempInCelsius nhỏ hơn 20 → in “Cold.”

Nếu không, sẽ in “Perfect!”
```

## So sánh logic giữa hai nhánh `true` / `false`

- Nhánh `true`: Sẽ thực thi khi biểu thức điều kiện trong if là `true`.

- Nhánh `false`: Sẽ thực thi khi biểu thức điều kiện trong if là `false`, nghĩa là điều kiện không được thỏa mãn.

***Ví dụ***

```csharp
int number = 10;

if (number > 0)               // Điều kiện đúng
{
    Console.WriteLine("Số dương");
}
else
{
    Console.WriteLine("Số không dương");
}

number = -5;

if (number > 0)               // Điều kiện sai
{
    Console.WriteLine("Số dương");
}
else
{
    Console.WriteLine("Số không dương");
}
```

***Kết quả***

```csharp

Với number = 10:

Điều kiện number > 0 là true, nên in "Số dương".
---------------------------------------------------------
Với number = -5:

Điều kiện number > 0 là false, nên in "Số không dương".
```

# Câu lệnh `if` lồng nhau (nested if)

Câu lệnh `if` lồng nhau (nested if) là khi một câu lệnh `if` hoặc `if-else` được đặt **bên trong thân của một câu lệnh `if` hoặc `else` khác**. Điều này thường xảy ra khi bạn cần kiểm tra nhiều điều kiện liên tiếp mà mỗi điều kiện phụ thuộc vào kết quả của điều kiện trước đó.

***Cú pháp***

```csharp
if (condition1)
{
    if (condition2)
    {
        // Các câu lệnh sẽ thực thi nếu cả condition1 và condition2 đều đúng
    }
}
```

## Khi nào sử dụng nested `if` thay vì `else if`

- Có thể sử dụng `if` lồng nhau (nested `if`) khi:

- Điều kiện bên trong phụ thuộc vào kết quả của điều kiện bên ngoài.

- Mỗi nhánh if cần kiểm tra thêm điều kiện con mà không thể kiểm tra đồng thời với các nhánh khác.

***Ví dụ***

```csharp
int age = 25;
bool hasPassport = true;

if (age >= 18)
{
    if (hasPassport)
    {
        Console.WriteLine("Bạn có thể đi du lịch.");
    }
    else
    {
        Console.WriteLine("Bạn cần có hộ chiếu để đi du lịch.");
    }
}
else
{
    Console.WriteLine("Bạn chưa đủ tuổi để đi du lịch.");
}
```

***Giai thích***:
- Nếu `age >= 18` là `true`, chương trình sẽ kiểm tra `hasPassport`.
- Nếu cả hai điều kiện đều đúng, chương trình sẽ in ra "Bạn có thể đi du lịch."
- Nếu `hasPassport` là `false`, chương trình sẽ in ra "Bạn cần có hộ chiếu để đi du lịch."
- Nếu `age < 18`, chương trình sẽ in ra "Bạn chưa đủ tuổi để đi du lịch."

***Lưu ý***: Nếu có thể, hãy sử dụng `else if` thay vì `if` lồng nhau để code dễ đọc hơn.

```csharp
if (age >= 18 && hasPassport)
{
    Console.WriteLine("Bạn có thể đi du lịch.");
}
else if (age >= 18 && !hasPassport)
{
    Console.WriteLine("Bạn cần có hộ chiếu để đi du lịch.");
}
else
{
    Console.WriteLine("Bạn chưa đủ tuổi để đi du lịch.");
}
```
## Ưu và nhược điểm

### Ưu điểm

- Rõ ràng và dễ hiểu: Nếu các điều kiện thực sự phụ thuộc lẫn nhau, sử dụng if lồng nhau có thể làm mã nguồn dễ hiểu và dễ theo dõi.

- Chính xác: Giúp thực thi các điều kiện kiểm tra chi tiết hơn.

## Nhược điểm

- Khó đọc: Khi có quá nhiều cấp lồng nhau, mã có thể trở nên khó đọc và bảo trì, nhất là khi điều kiện nhiều hoặc phức tạp.

- Cần nhiều dấu ngoặc nhọn: Nếu bạn lồng quá nhiều if, sẽ gây khó khăn trong việc theo dõi từng cấp lệnh.

- Có thể làm tăng độ phức tạp của chương trình: Quá nhiều if lồng nhau có thể dẫn đến lỗi logic hoặc lỗi không mong muốn trong quá trình bảo trì.


