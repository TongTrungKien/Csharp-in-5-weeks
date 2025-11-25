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

# Kết luận

- **Sử dụng khi**: Các điều kiện phụ thuộc lẫn nhau và cần kiểm tra chi tiết từng trường hợp.
- **Tránh khi**: Có thể sử dụng các cấu trúc điều khiển khác như `else if` hoặc `switch` để làm cho mã dễ đọc hơn.


# Toán tử điều kiện (toán tử 3 ngôi) `?:`
     Các bạn có thể đọc ở [Day 4](https://github.com/TongTrungKien/Csharp-in-5-weeks/blob/main/Day04-OPERATIONS%20IN%20C%23.md) cũng đã viết về toán tử 3 ngôi `?:`
### Vai trò và cú pháp tổng quát

Toán tử điều kiện, hay còn gọi là toán tử 3 ngôi (`?:`), được dùng để **lựa chọn giữa hai giá trị** tùy thuộc vào một biểu thức điều kiện. Đây là cách rút gọn của câu lệnh `if-else` trong một dòng, giúp mã ngắn gọn và dễ đọc hơn.

Cú pháp:

```csharp
condition ? valueIfTrue : valueIfFalse;
```
- **Thành phần**:
    - `condition`: Biểu thức điều kiện (true/false).
    - `valueIfTrue`: Giá trị trả về nếu `condition` true.
    - `valueIfFalse`: Giá trị trả về nếu `condition` false.
    
***Ví dụ***
```csharp
int number = 10;
string result = (number > 5) ? "Lớn hơn 5" : "Nhỏ hơn hoặc bằng 5";
Console.WriteLine(result); // Output: "Lớn hơn 5"
```
- **Giải thích**: Nếu `number > 5` đúng, `result` sẽ nhận giá trị `"Lớn hơn 5"`, ngược lại nhận `"Nhỏ hơn hoặc bằng 5"`.

### Ưu điểm
- **Gọn gàng**: Giảm số dòng mã so với `if-else` truyền thống.
- **Đọc dễ hiểu**: Khi biểu thức đơn giản, toán tử 3 ngôi có thể dễ đọc hơn.

### Nhược điểm
- **Khó đọc**: Nếu biểu thức phức tạp, toán tử 3 ngôi có thể làm mã khó hiểu hơn.
- **Không linh hoạt**: Chỉ có thể xử lý hai trường hợp (true/false), không thể lồng nhiều điều kiện như `if-else if-else`.

### Kết luận
- **Sử dụng khi**: Biểu thức điều kiện đơn giản, chỉ cần chọn giữa hai giá trị.
- **Tránh khi**: Biểu thức phức tạp hoặc cần nhiều trường hợp xử lý.

***Ví dụ***
```csharp
int a = 10, b = 20;
string max = (a > b) ? "a lớn hơn b" : (a == b) ? "a bằng b" : "b lớn hơn a";
Console.WriteLine(max); // Output: "b lớn hơn a"
```
- **Giải thích**: Nếu `a > b` đúng, `max` nhận giá trị `"a lớn hơn b"`. Nếu không, kiểm tra `a == b` và trả về `"a bằng b"`. Nếu cả hai điều kiện đều sai, trả về `"b lớn hơn a"`.
---

#### Toán tử điều kiện `?:` rất hữu ích trong các tình huống cần gán giá trị nhanh hoặc trả về kết quả dựa trên một điều kiện đơn giản. Tuy nhiên, khi điều kiện trở nên phức tạp hoặc có nhiều nhánh, bạn nên cân nhắc sử dụng các cấu trúc điều khiển khác như if-else để đảm bảo mã nguồn rõ ràng và dễ bảo trì.

### **Tóm lại**:

- **Ưu điểm**: Ngắn gọn, dễ hiểu khi sử dụng cho điều kiện đơn giản.
- **Nhược điểm**: Không phù hợp cho điều kiện logic phức tạp hoặc lồng nhau.

# Câu lệnh `switch`

Câu lệnh `switch` trong C# được sử dụng để kiểm tra một **biểu thức** (expression) và **so khớp** với một số **nhánh `case`**. Mỗi nhánh `case` đại diện cho một giá trị hoặc điều kiện cụ thể. Nếu biểu thức khớp với giá trị của một nhánh `case`, khối lệnh của nhánh đó sẽ được thực thi.

Cú pháp cơ bản của `switch`:

```csharp
switch (expression)
{
    case value1:
        // Câu lệnh thực thi khi expression == value1
        break;
    case value2:
        // Câu lệnh thực thi khi expression == value2
        break;
    default:
        // Câu lệnh thực thi nếu không khớp với bất kỳ case nào
        break;
}
```
- `expression`: là biểu thức được kiểm tra, có thể là kiểu dữ liệu như số nguyên, chuỗi, hay kiểu dữ liệu khác.

- `case value`: là các giá trị cụ thể cần so khớp với `expression`.

- `default`: là nhánh được thực thi nếu không có `case` nào khớp với `expression`.


***Ví dụ***

```csharp
DisplayMeasurement(-4);  // Output: Measured value is -4; too low.
DisplayMeasurement(5);  // Output: Measured value is 5.
DisplayMeasurement(30);  // Output: Measured value is 30; too high.
DisplayMeasurement(double.NaN);  // Output: Failed measurement.

void DisplayMeasurement(double measurement)
{
    switch (measurement)
    {
        case < 0.0:
            Console.WriteLine($"Measured value is {measurement}; too low.");
            break;

        case > 15.0:
            Console.WriteLine($"Measured value is {measurement}; too high.");
            break;

        case double.NaN:
            Console.WriteLine("Failed measurement.");
            break;

        default:
            Console.WriteLine($"Measured value is {measurement}.");
            break;
    }
}
```
- `case < 0.0`: Kiểm tra nếu `measurement` nhỏ hơn 0.0.
- `case > 15.0`: Kiểm tra nếu `measurement` lớn hơn 15.0.
- `case double.NaN`: Kiểm tra nếu `measurement` là `NaN` (Not a Number).
- `default`: Thực thi nếu không có trường hợp nào khớp.

**Lưu ý**:
- `switch` không hỗ trợ toán tử logic như `&&`, `||`, `!`, `==`, `!=`, `>`, `<`, `>=`, `<=`.
- `switch` không hỗ trợ kiểu dữ liệu `float` và `decimal`.
- `switch` không hỗ trợ kiểu dữ liệu `null`.
- `switch` không hỗ trợ kiểu dữ liệu `object`.
- `switch` không hỗ trợ kiểu dữ liệu `string` với toán tử `==` hoặc `!=`.

# Tổng kết

### So sánh `if`, `if-else`, `else if`, nested if

- **`if`**: Được sử dụng khi chỉ cần kiểm tra một điều kiện đơn giản. Nếu điều kiện đúng, câu lệnh trong `if` sẽ được thực thi.
  - Ví dụ: Kiểm tra số nguyên có dương hay không.
  
- **`if-else`**: Cho phép lựa chọn giữa hai nhánh điều kiện. Sử dụng khi có hai kết quả khả thi, một khi điều kiện đúng và một khi điều kiện sai.
  - Ví dụ: Kiểm tra xem một số là chẵn hay lẻ.
  
- **`else if`**: Dùng khi có nhiều điều kiện cần kiểm tra theo thứ tự ưu tiên. Giống như `if-else`, nhưng cho phép kiểm tra nhiều điều kiện khác nhau.
  - Ví dụ: Phân loại điểm số học sinh thành "Giỏi", "Khá", "Trung bình", "Yếu".
  
- **Nested if** (if lồng nhau): Dùng khi có nhiều điều kiện phụ thuộc vào nhau. Cấu trúc `if` được đặt trong một `if` hoặc `else` khác.
  - Ví dụ: Kiểm tra độ tuổi và quốc tịch để quyết định có được cấp visa hay không.

**Lưu ý**:
- **`if`** phù hợp cho điều kiện đơn giản.
- **`if-else`** và **`else if`** phù hợp khi có nhiều lựa chọn.
- **Nested if** có thể khiến mã trở nên khó đọc, nên tránh nếu không cần thiết. Dùng các cấu trúc khác khi có thể.

---

### So sánh `if` với `switch`

- **`if`**: Cấu trúc điều kiện rất linh hoạt, có thể xử lý mọi loại biểu thức điều kiện. Tuy nhiên, khi có quá nhiều điều kiện (nhất là kiểm tra nhiều giá trị của một biến), mã có thể trở nên dài dòng và khó đọc.
  - **Ưu điểm**: Linh hoạt, có thể kiểm tra bất kỳ điều kiện nào.
  - **Nhược điểm**: Khi điều kiện quá phức tạp hoặc có nhiều nhánh, dễ gây rối và khó bảo trì.

- **`switch`**: Dùng khi bạn cần kiểm tra một biểu thức với nhiều giá trị cụ thể. `switch` thường dễ đọc hơn và hiệu quả hơn khi có nhiều nhánh.
  - **Ưu điểm**: Rõ ràng, dễ hiểu khi có nhiều điều kiện cụ thể. Có thể hỗ trợ **pattern matching** trong các phiên bản C# mới.
  - **Nhược điểm**: Chỉ hữu ích khi các điều kiện là **giá trị cụ thể**. Nếu điều kiện quá phức tạp, `switch` sẽ không phải là lựa chọn tốt nhất.

**Khi nào dùng `if`**:  
- Khi bạn cần kiểm tra các điều kiện phức tạp hoặc không phải là các giá trị cụ thể.

**Khi nào dùng `switch`**:  
- Khi bạn cần kiểm tra một giá trị so với nhiều giá trị cụ thể, hoặc khi điều kiện là các giá trị hằng số hoặc kiểu dữ liệu có thể phân loại rõ ràng.

---

### Gợi ý lựa chọn cấu trúc phù hợp theo từng tình huống logic

- **Khi chỉ có hai lựa chọn** (true/false):  
  Sử dụng `if-else`. Ví dụ, kiểm tra một số dương hay âm.

- **Khi có nhiều điều kiện lựa chọn độc lập**:  
  Sử dụng `else if` hoặc `switch`, tùy thuộc vào số lượng điều kiện. `switch` thường dễ đọc và nhanh hơn nếu có nhiều điều kiện kiểm tra giá trị cụ thể (chẳng hạn tháng trong năm hoặc ngày trong tuần).

- **Khi có nhiều điều kiện phụ thuộc lẫn nhau**:  
  Sử dụng `nested if` để xử lý các tình huống mà điều kiện kiểm tra phụ thuộc vào nhau. Tuy nhiên, nếu điều kiện lồng nhau quá nhiều, có thể sử dụng **sớm return** hoặc **hàm phụ trợ** để làm cho mã nguồn dễ đọc và dễ bảo trì hơn.

- **Khi có điều kiện so sánh đơn giản (chọn giữa hai giá trị)**:  
  Dùng toán tử 3 ngôi (`?:`) để thay thế `if-else`, giúp mã ngắn gọn và dễ đọc hơn. Ví dụ: phân loại số chẵn/lẻ hoặc phân loại kết quả theo điểm số.

**Tóm lại**:
- Sử dụng **`if`** cho điều kiện đơn giản và linh hoạt.
- **`switch`** rất hữu ích khi cần kiểm tra nhiều giá trị của một biến.
- **`else if`** giúp kiểm tra các điều kiện phức tạp với nhiều nhánh.
- **`nested if`** dùng khi các điều kiện phụ thuộc lẫn nhau, nhưng cần tránh sử dụng quá nhiều.

Chọn cấu trúc điều kiện phù hợp giúp chương trình dễ đọc, dễ bảo trì và tránh lỗi logic.


> Hẹn gặp lại bạn trong những bài tiếp theo! 

# Link tham khảo
https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/statements#1382-the-if-statement

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/statements#1383-the-switch-statement

# HASHTAG

`Csharp-in-5-weeks` `Csharp`

# Author

[Dexter](https://github.com/TongTrungKien)
