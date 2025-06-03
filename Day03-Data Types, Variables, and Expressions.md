# KIỂU DỮ LIỆU, BIẾN & BIỂU THỨC

- Các Kiểu dữ liệu trong C#
- Khái niệm về biến, cách thức và quy tắc đặt tên biến
- Cách thức ép kiểu trong C#
- Implicit type trong C#
- Khai báo hằng số
- Biểu thức 

# KIỂU DỮ LIỆU TRONG C#

**Kiểu dữ liệu** xác định kiểu giá trị mà một biến có thể chứa, giúp hệ thống hiểu cách lưu trữ và xử lý dữ liệu đó. C# hỗ trợ nhiều kiểu dữ liệu cơ bản như:

| Kiểu dữ liệu | Kích thước bộ nhớ | Mô tả                                                   | Giá trị mặc định | Phạm vi giá trị                                          |
| ------------ | ----------------- | ------------------------------------------------------- | ---------------- | -------------------------------------------------------- |
| **byte**     | 1 byte            | Số nguyên không dấu                                     | 0                | 0 đến 255                                                |
| **sbyte**    | 1 byte            | Số nguyên có dấu                                        | 0                | -128 đến 127                                             |
| **short**    | 2 bytes           | Số nguyên có dấu                                        | 0                | -32,768 đến 32,767                                       |
| **ushort**   | 2 bytes           | Số nguyên không dấu                                     | 0                | 0 đến 65,535                                             |
| **int**      | 4 bytes           | Số nguyên có dấu                                        | 0                | -2,147,483,648 đến 2,147,483,647                         |
| **uint**     | 4 bytes           | Số nguyên không dấu                                     | 0                | 0 đến 4,294,967,295                                      |
| **long**     | 8 bytes           | Số nguyên có dấu                                        | 0                | -9,223,372,036,854,775,808 đến 9,223,372,036,854,775,807 |
| **ulong**    | 8 bytes           | Số nguyên không dấu                                     | 0                | 0 đến 18,446,744,073,709,551,615                         |
| **float**    | 4 bytes           | Số thực dấu phẩy động đơn (độ chính xác thấp)           | 0.0f             | ±1.5 × 10^−45 đến ±3.4 × 10^38                           |
| **double**   | 8 bytes           | Số thực dấu phẩy động kép (độ chính xác cao)            | 0.0d             | ±5.0 × 10^−324 đến ±1.7 × 10^308                         |
| **decimal**  | 16 bytes          | Số thực thập phân chính xác cao (thường dùng tài chính) | 0.0m             | ±1.0 × 10^−28 đến ±7.9 × 10^28                           |
| **char**     | 2 bytes           | Ký tự Unicode                                           | '\0'             | Unicode ký tự                                            |
| **bool**     | 1 byte            | Giá trị logic (true hoặc false)                         | false            | true hoặc false                                          |
| **string**   | tham chiếu        | Chuỗi ký tự                                             | null             | Chuỗi Unicode                                            |
| **object**   | tham chiếu        | Kiểu cơ sở của tất cả các kiểu dữ liệu                  | null             | Có thể chứa bất kỳ kiểu nào                              |


# BIẾN (VARIABEL)

* Là tên gọi cho một vùng nhớ (bên trong bộ nhớ máy tính khi chương trình được chạy) có khả năng chứa được một giá trị = một dữ liệu. 
* Được khai báo và sử dụng để chứa dữ liệu của chương trình

## KHAI (TẠO) BÁO BIẾN 
**Cú pháp cơ bản**:

```typescript
<Kiểu_Dữ_Liệu> <tên_biến> [ = <giá_trị> ];
```
* Trong đó:

`Kiểu dữ liệu` có thể là: Kiểu dữ liệu cơ bản hoặc kiểu dữ liệu có cấu trúc

`Tên biến` Là tên do người dùng đặt. Phải tuân thủ theo quy tắc đặt tên (sẽ được trình bày ngay sau đây).

**Ví dụ**:

```csharp
int age;
string message = "Xin chào";
```

- Trong đó `int age;` chỉ khai báo biến `age` kiểu nguyên mà chưa có giá trị.
- `string message = "Xin chào";` khai báo biến `message` kiểu chuỗi và khởi tạo giá trị `"Xin chào"` ngay khi khai báo.

## QUY TẮC ĐẶT TÊN BIẾN
* Phân biệt chữ hoa chữ thường (tenBien khác TenBien)

* Không bắt đầu bằng số

* Không chứa ký tự đặc biệt như ~ ! @ # $ % ^ & * ( )

* Không đặt tên trùng với từ khóa của C# (string, int, private...)

* Nên dùng quy tắc [CamelCase](https://www.icantech.vn/kham-pha/camelcase-la-gi): chữ đầu từ biến thường viết thường, các từ tiếp theo viết hoa chữ cái đầu

## Khởi tạo giá trị mặc định
Nên khởi tạo biến khi khai báo để tránh lỗi hoặc giá trị rác:

```csharp
int nSize = 0;
string strName = "";
```
***Giải thích***:

- `int nSize = 0;` Khai báo biến `nSize` kiểu số nguyên (`int`) và khởi tạo giá trị ban đầu là 0.
Việc khởi tạo giúp tránh lỗi biến chưa được gán giá trị khi sử dụng.
- `string strName = "";`
Khai báo biến strName kiểu chuỗi (`string`) và khởi tạo giá trị là chuỗi rỗng `""`.
Điều này có nghĩa biến `strName` đã có giá trị hợp lệ, tránh trường hợp `null`.

# BIẾN TỰ SUY LUẬN KIỂU DỮ LIỆU (IMPLICIT TYPING)

C# cho phép khai báo biến mà không cần xác định kiểu dữ liệu, dùng từ khóa `var`. Trình biên dịch sẽ tự suy luận kiểu dữ liệu dựa trên giá trị gán đầu tiên.

**Ví dụ**:

```typescript
var x = 113;           // int
var y = "1/1/2012";    // string
var z = 1.7;           // double
var k = new DateTime(2012, 1, 1);  // DateTime
```

# ÉP KIỂU TRONG C#

 Ép kiểu là quá trình chuyển đổi một biến từ kiểu dữ liệu này sang kiểu dữ liệu khác. Có hai loại ép kiểu cơ bản trong C#:

### ÉP KIỂU RỘNG (Implicit Cast):

- Xảy ra khi chuyển từ kiểu có dung lượng bộ nhớ nhỏ sang kiểu có dung lượng bộ nhớ lớn hơn.

- Không có mất mát dữ liệu và C# sẽ tự động thực hiện.

- **Ví dụ**: `int` → `long` → `float` → `double`.

```csharp
int intValue = 100;
long longValue = intValue;  // Ép kiểu tự động từ int sang long
```
### ÉP KIỂU HẸP (Explicit Cast):

- Xảy ra khi chuyển từ kiểu có dung lượng bộ nhớ lớn sang kiểu có dung lượng bộ nhớ nhỏ hơn.

- Có thể mất dữ liệu nếu giá trị vượt quá phạm vi kiểu mới.

- Cần sử dụng toán tử (kiểu) để thực hiện ép kiểu.

```csharp
double doubleValue = 9.8;
int intValue = (int)doubleValue;  // Ép kiểu từ double sang int, mất phần thập phân
Console.WriteLine(intValue);  // In ra 9
```
### ***MỘT SỐ LƯU Ý KHI ÉP KIỂU TRONG C#***

### MẤT MÁT DỮ LIỆU:

- Khi ép kiểu từ kiểu dữ liệu lớn sang kiểu dữ liệu nhỏ (explicit cast), có thể gây mất mát dữ liệu. Ví dụ, khi chuyển từ `double` sang `int`, phần thập phân sẽ bị loại bỏ.

### KIỂM TRA LỖI KHI ÉP KIỂU:

Nếu bạn không chắc chắn về kiểu dữ liệu, bạn có thể sử dụng `try-catch` hoặc `as` để tránh lỗi runtime khi ép kiểu không hợp lệ.

```csharp
try
{
    string str = "123.45";
    int value = Convert.ToInt32(str); // Sẽ gây lỗi nếu str không phải số nguyên
}
catch (FormatException e)
{
    Console.WriteLine("Lỗi: " + e.Message);
}
```

## SỬ DỤNG `as` và `is`:

- Dùng từ khóa `as` để ép kiểu khi bạn không chắc chắn rằng kiểu dữ liệu có thể ép được.

- Dùng `is` để kiểm tra kiểu dữ liệu trước khi ép kiểu.

```csharp
object obj = "Hello";
string str = obj as string;  // Sẽ là null nếu obj không phải kiểu string
if (str != null)
{
    Console.WriteLine(str);  // "Hello"
}
```

# HẰNG SỐ (CONSTANT)

Trong C#, hằng số là các giá trị không thay đổi trong suốt thời gian chạy của chương trình. Chúng thường được sử dụng để lưu trữ các giá trị không thay đổi, giúp làm cho chương trình dễ đọc, dễ duy trì và tránh việc lặp lại các giá trị cố định.

Hằng số được khai báo bằng từ khóa `const`, và giá trị của chúng phải được xác định ngay khi khai báo. Sau khi được gán giá trị, hằng số không thể thay đổi trong suốt vòng đời của chương trình.

**CÚ PHÁP KHAI BÁO HẰNG SỐ**

```typescript
const <kiểu_dữ_liệu> <tên_hằng_số> = <giá_trị>;
```

`<kiểu_dữ_liệu>`: Kiểu dữ liệu của hằng số (ví dụ: `int`, `double`, `string`, v.v.).

`<tên_hằng_số>`: Tên của hằng số, theo quy tắc đặt tên thông thường.

`<giá_trị>`: Giá trị được gán cho hằng số và không thể thay đổi sau khi đã được khai báo.

## VÍ DỤ VỀ HẰNG SỐ

### HẰNG SỐ KIỂU SỐ NGUYÊN

```csharp
const int MaxUsers = 100;  // Hằng số kiểu int
Console.WriteLine(MaxUsers);  // Output: 100
```
### HẰNG SỐ KIỂU CHUỖI

```csharp
const string GreetingMessage = "Hello, World!";
Console.WriteLine(GreetingMessage);  // Output: Hello, World!
```
### HẰNG SỐ KIỂU SỐ THỰC (float, double)

```csharp
const double PI = 3.14159;
Console.WriteLine(PI);  // Output: 3.14159
```
###HẰNG SỐ KIỂU BOOLEAN

```csharp
const bool IsValid = true;
Console.WriteLine(IsValid);  // Output: True
```

## ĐẶC ĐIỂM CỦA HẰNG SỐ TRONG C#

Giá trị không thay đổi: Sau khi khai báo hằng số, bạn không thể thay đổi giá trị của nó.

```csharp
const int x = 10;
x = 20;  // Lỗi biên dịch: Không thể gán lại cho hằng số
```
Thời gian xác định giá trị: Hằng số phải có giá trị được xác định ngay khi khai báo, không thể để trống hoặc gán sau này.

```csharp
const int y;  // Lỗi biên dịch: Phải gán giá trị cho hằng số khi khai báo
```

**Tối ưu hiệu suất**: Sử dụng hằng số thay vì giá trị cố định trong mã giúp tối ưu hóa hiệu suất, vì trình biên dịch có thể thay thế trực tiếp giá trị hằng số trong mã nguồn thay vì phải truy vấn mỗi khi sử dụng.

**Không thể gán giá trị tại runtime**: Hằng số chỉ có thể được gán một lần, ngay khi khai báo, và không thể thay đổi trong quá trình thực thi chương trình.

## HẰNG SỐ SO VỚI BIẾN
`Hằng số`: Giá trị không thay đổi trong suốt thời gian chạy của chương trình. Thường dùng cho các giá trị cố định không thay đổi, như `PI`, `MAX_VALUE`, hoặc các tham số cấu hình.

`Biến`: Giá trị có thể thay đổi trong quá trình thực thi của chương trình. Biến được sử dụng để lưu trữ thông tin có thể thay đổi, ví dụ như kết quả tính toán, trạng thái ứng dụng.


## HẰNG SỐ TRONG CÁC LỚP
Bạn cũng có thể khai báo hằng số trong các lớp để sử dụng trong phạm vi lớp đó hoặc cho tất cả các đối tượng của lớp (nếu khai báo là static):

```csharp
class MyClass
{
    public const double TaxRate = 0.07;  // Hằng số trong lớp
}

Console.WriteLine(MyClass.TaxRate);  // Output: 0.07
```

## LỢI ÍCH CỦA VIỆC SỬ DỤNG HẰNG SỐ
- **Tăng tính rõ ràng**: Sử dụng hằng số giúp mã dễ đọc và dễ hiểu hơn, đặc biệt khi bạn cần sử dụng các giá trị không thay đổi nhiều lần trong mã.

- **Dễ bảo trì**: Khi bạn sử dụng hằng số, nếu giá trị thay đổi, bạn chỉ cần cập nhật một lần tại nơi khai báo, thay vì phải thay đổi ở nhiều vị trí trong mã nguồn.

- **Giảm sai sót**: Việc sử dụng hằng số thay vì giá trị "cứng" giúp giảm khả năng sai sót trong việc nhập lại giá trị giống nhau ở nhiều nơi.

# BIỂU THỨC

**Biểu thức** trong C# là một phần mã có thể tính toán hoặc thực hiện một phép toán và trả về một giá trị. Biểu thức có thể bao gồm các toán hạng, toán tử và đôi khi là các phương thức hoặc hàm. Biểu thức là một khái niệm rất quan trọng trong lập trình, vì hầu hết các phép toán hoặc tính toán trong chương trình đều được thực hiện thông qua biểu thức.

## CÚ PHÁP BIỂU THỨC TRONG C##

Biểu thức có thể là bất kỳ đoạn mã nào thực hiện phép toán hoặc tính toán một giá trị.

```csharp
<toán_hạng> <toán_tử> <toán_hạng>
```

Biểu thức có thể rất đơn giản hoặc phức tạp, tùy thuộc vào số lượng toán tử và toán hạng.

## CÁC LOẠI BIỂU THỨC TRONG C#


### BIỂU THỨC TOÁN HỌC CƠ BẢN
Đây là các biểu thức thực hiện các phép toán cơ bản như cộng, trừ, nhân, chia, v.v.

```csharp
int x = 5 + 3;   // Biểu thức cộng: x = 8
int y = 10 - 2;  // Biểu thức trừ: y = 8
int z = 4 * 6;   // Biểu thức nhân: z = 24
int w = 8 / 2;   // Biểu thức chia: w = 4
```

### BIỂU THỨC VỚI PHÉP TOÁN SO SÁNH
Biểu thức này so sánh các giá trị và trả về giá trị `true` hoặc `false`.

```csharp
bool result1 = 5 > 3;    // Biểu thức so sánh: true
bool result2 = 10 <= 7;  // Biểu thức so sánh: false
bool result3 = 5 == 5;   // Biểu thức so sánh: true
bool result4 = 7 != 8;   // Biểu thức so sánh: true
```

### BIỂU THỨC LOGIC
Biểu thức logic kết hợp các phép toán so sánh và trả về giá trị `true` hoặc `false`. Chúng sử dụng các toán tử logic như `&&` (và), `||` (hoặc), `!` (đảo ngược).

```csharp
bool isTrue = (5 > 3) && (7 < 10);  // Biểu thức logic: true
bool isFalse = (5 < 3) || (7 > 10); // Biểu thức logic: false
bool isNot = !(5 == 5);             // Biểu thức logic: false
```

### BIỂU THỨC KẾT HỢP PHƯƠNG THỨC
Biểu thức có thể kết hợp các phép toán với các phương thức hoặc hàm.

```csharp
int x = Math.Max(5, 10);  // Biểu thức kết hợp phương thức: x = 10
double area = Math.PI * Math.Pow(2, 2);  // Biểu thức kết hợp phương thức: area = 12.566370614359172
```

### BIỂU THỨC GÁN
Biểu thức gán dùng để gán giá trị cho một biến. Toán tử `=` là toán tử gán.

```csharp
int x = 10;    // Gán giá trị 10 cho x
x += 5;        // Tương đương với x = x + 5, x = 15
x *= 2;        // Tương đương với x = x * 2, x = 30
```

## BIỂU THỨC PHỨC TẠP

Biểu thức có thể kết hợp nhiều phép toán và toán hạng, tạo thành các biểu thức phức tạp.

```csharp
int result = (5 + 3) * (10 - 2) / 4;  // Biểu thức phức tạp: result = 16
```

Trong ví dụ trên:
- `(5 + 3)` là một biểu thức cộng, trả về `8`.
- `(10 - 2)` là một biểu thức trừ, trả về `8`.
- Sau đó kết quả của các phép toán này được nhân với nhau và chia cho `4`.

## BIỂU THỨC VỚI ĐIỀU KIỆN (Ternary Operator)

C# cũng hỗ trợ **biểu thức điều kiện** (ternary operator), một cách viết ngắn gọn của câu lệnh `if-else`.

**Cú pháp**:
```csharp
<condition> ? <value_if_true> : <value_if_false>;
```

**Ví dụ**:

```csharp
int x = 10;
string result = (x > 5) ? "Lớn hơn 5" : "Nhỏ hơn hoặc bằng 5";
Console.WriteLine(result);  // Output: Lớn hơn 5
```

## Link tham khảo
https://howkteam.vn/Course/C-Basics/Bien-trong-C-52
https://www.w3schools.com/cs/cs_variables.php
https://www.icantech.vn/kham-pha/camelcase-la-gi
## HASHTAG

`Csharp-in-5-weeks` `Csharp`

## Author

[Dexter](https://github.com/TongTrungKien)
