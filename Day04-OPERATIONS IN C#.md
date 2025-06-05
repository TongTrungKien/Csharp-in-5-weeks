# OPERATIONS IN C#

* Toán tử gán
* Toán tử số học
* Toán tử 1 ngôi
* Toán tử so sánh
* Toán tử luận lý điều kiện
* Độ ưu tiên toán tử 

Trong lập trình C#, các phép toán là thành phần cơ bản và quan trọng để xử lý dữ liệu, tính toán, ra quyết định và điều khiển luồng chương trình. Việc hiểu rõ từng loại phép toán giúp bạn viết mã hiệu quả, dễ đọc và ít lỗi hơn.

# TOÁN TỬ GÁN (Assignment operators)

Toán tử gán `=` dùng để gán giá trị của toán hạng bên phải cho một biến, một thuộc tính hoặc một phần tử của chỉ mục (indexer) được chỉ định bởi toán hạng bên trái. Kết quả của một biểu thức gán chính là giá trị được gán cho toán hạng bên trái. Kiểu dữ liệu của toán hạng bên phải phải giống với hoặc có thể chuyển đổi ngầm định sang kiểu dữ liệu của toán hạng bên trái.

Toán tử gán = có tính kết hợp phải (right-associative), nghĩa là một biểu thức có dạng như sau:

```csharp
a = b = c
```
sẽ được đánh giá từ phải sang trái, tương đương với:

```csharp
a = (b = c);
```
Tức là `c` được gán cho `b` trước, sau đó giá trị của `b` (vốn bằng `c`) lại được gán tiếp cho `a`.

### CÚ PHÁP CƠ BẢN

```csharp
int x = 10;
string name = "John";
double pi = 3.14;
```
* `x` nhận giá trị `10`

* `name` nhận giá trị chuỗi `"John"`

* `pi` nhận giá trị `3.14`

## CÁC TOÁN TỬ GÁN KẾT HỢP
| Toán tử | Ý nghĩa             | Ví dụ     | Tương đương với |
| ------- | ------------------- | --------- | --------------- |
| `+=`    | Cộng rồi gán        | `x += 3;` | `x = x + 3;`    |
| `-=`    | Trừ rồi gán         | `x -= 2;` | `x = x - 2;`    |
| `*=`    | Nhân rồi gán        | `x *= 5;` | `x = x * 5;`    |
| `/=`    | Chia rồi gán        | `x /= 4;` | `x = x / 4;`    |
| `%=`    | Lấy phần dư rồi gán | `x %= 2;` | `x = x % 2;`    |

**Lưu ý**

* Toán tử gán không phải là phép so sánh.

    * Ví dụ: `x = 5` là gán, còn `x == 5` là so sánh.

* Các biểu thức có thể được gán theo chuỗi:

```csharp
int a, b, c;
a = b = c = 100; // gán 100 cho cả a, b và c
```

# TOÁN TỬ SỐ HỌC (Arithmetic operators)

* Các toán tử sau thực hiện các phép toán số học trên các toán hạng có kiểu số:

* Toán tử một ngôi:
`++` (tăng), `--` (giảm), `+` (dương), và `-` (âm)

* Toán tử hai ngôi:
`*`(nhân), `/` (chia), `%` (lấy phần dư), `+` (cộng), và `-` (trừ)

# TOÁN TỬ MỘT NGÔI ( Unary operator)

## TOÁN TỬ TĂNG & GIẢM `++` `--`

Toán tử tăng một đơn vị (++) và giảm một đơn vị (--) là các toán tử một ngôi, dùng để tăng hoặc giảm giá trị của toán hạng lên hoặc xuống 1 đơn vị.
Toán hạng phải là một biến, một truy cập [thuộc tính](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties) hoặc một truy cập [chỉ mục](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/indexers/).

Cả hai toán tử đều có **hai dạng**:

- **Dạng hậu tố** (`x++`, `x--`): giá trị được sử dụng trước, sau đó mới được thay đổi.

```csharp
int i = 3;
Console.WriteLine(i);   // output: 3
Console.WriteLine(i++); // output: 3
Console.WriteLine(i);   // output: 4
```

- **Dạng tiền tố** (`++x`, `--x`): giá trị được thay đổi trước, sau đó mới được sử dụng trong biểu thức.

```csharp
double a = 1.5;
Console.WriteLine(a);   // output: 1.5
Console.WriteLine(++a); // output: 2.5
Console.WriteLine(a);   // output: 2.5
```



## TOÁN TỬ DƯƠNG & ÂM `+` `-`
Toán tử dương một ngôi (`+`) trả về giá trị của toán hạng mà không thay đổi gì.
Toán tử âm một ngôi (`-`) tính giá trị đối (phủ định) của toán hạng, tức là đổi dấu số.

```csharp
Console.WriteLine(+4);     // output: 4

Console.WriteLine(-4);     // output: -4
Console.WriteLine(-(-4));  // output: 4

uint a = 5;
var b = -a;
Console.WriteLine(b);            // output: -5
Console.WriteLine(b.GetType());  // output: System.Int64

Console.WriteLine(-double.NaN);  // output: NaN
```
`+x`: toán tử dương – trả về chính giá trị `x`

`-x`: toán tử âm – trả về số đối của `x`

***Ví dụ***

```csharp
Console.WriteLine(+4);      // 4
Console.WriteLine(-4);      // -4
Console.WriteLine(-(-4));   // 4
```
- Khi uint a = 5, -a sẽ:

    - ép kiểu ngầm định từ uint sang long (System.Int64)

    - cho kết quả -5

- Console.WriteLine(-double.NaN); → vẫn là NaN, vì NaN không có dấu cụ thể.

***Lưu ý*** "Kiểu ulong không hỗ trợ `-` toán tử đơn ngôi." nghĩa là: bạn không thể viết -ulongValue, vì ulong không cho phép biểu diễn số âm.

## TOÁN  TỬ PHỦ ĐỊNH `!`

**Toán tử phủ định logic `!`** là một **toán tử một ngôi** dùng để **đảo ngược giá trị boolean** của toán hạng.

- Nếu toán hạng là `true`, kết quả là `false`.
- Nếu toán hạng là `false`, kết quả là `true`.

>Toán tử `!` **chỉ áp dụng cho kiểu `bool`** hoặc biểu thức trả về `bool`.
```csharp
bool isAdmin = false;

if (!isAdmin)
{
    Console.WriteLine("Bạn không có quyền truy cập.");
}
// Output: Bạn không có quyền truy cập.
```

# TOÁN TỬ HAI NGÔI ( Toán tử hai ngôi)

## TOÁN TỬ CỘNG `+` 

**Toán tử cộng** `+` thực hiện phép cộng tổng hai toán hạng của nó.


```csharp
Console.WriteLine(5 + 4);       // output: 9
Console.WriteLine(5 + 4.3);     // output: 9.3
Console.WriteLine(5.1m + 4.2m); // output: 9.3
```
Ngoài ra, toán tử `+` còn có thể dùng để nối chuỗi và kết hợp delegate.

## TOÁN TỬ TRỪ `-`
**Toán tử trừ** `-` thực hiện phép trừ toán hạng bên phải khỏi toán hạng bên trái.

```csharp
Console.WriteLine(5 + 4);       // output: 9
Console.WriteLine(5 + 4.3);     // output: 9.3
Console.WriteLine(5.1m + 4.2m); // output: 9.3
```
Toán tử `-` cũng được sử dụng để xóa delegate trong ngữ cảnh delegate và event.

## TOÁN TỬ NHÂN `*`

**Toán tử nhân** `*` thực hiện phép nhân hai toán hạng:

```csharp
Console.WriteLine(5 * 2);         // output: 10
Console.WriteLine(0.5 * 2.5);     // output: 1.25
Console.WriteLine(0.1m * 23.4m);  // output: 2.34
```

## TOÁN TỬ CHIA `/`
**Toán tử chia** `/` thực hiện phép chia toán hạng bên trái cho toán hạng bên phải.

### CHIA SỐ NGUYÊN (Integer Division)
- Với hai toán hạng là kiểu số nguyên, kết quả là số nguyên, được làm tròn về 0:

```csharp
Console.WriteLine(13 / 5);    // output: 2
Console.WriteLine(-13 / 5);   // output: -2
Console.WriteLine(13 / -5);   // output: -2
Console.WriteLine(-13 / -5);  // output: 2
```
Nếu muốn kết quả là số thực, hãy dùng kiểu `float`, `double` hoặc `decimal`:

```csharp
Console.WriteLine(13 / 5.0);       // output: 2.6

int a = 13;
int b = 5;
Console.WriteLine((double)a / b);  // output: 2.6
```
### CHIA SỐ THỰC (Floating-point Division)

Với kiểu `float`, `double` hoặc `decimal`, kết quả sẽ là thương số dấu phẩy động chính xác:

```csharp
Console.WriteLine(16.8f / 4.1f);   // output: 4.097561
Console.WriteLine(16.8d / 4.1d);   // output: 4.09756097560976
Console.WriteLine(16.8m / 4.1m);   // output: 4.0975609756097560975609756098
```
***Lưu ý*** về kiểu `decimal`:
- Nếu một trong hai toán hạng là `decimal`, thì toán hạng còn lại không được là `float` hoặc `double`

- Vì float và `double` không thể chuyển đổi ngầm định sang `decimal`

- Trong trường hợp đó, bạn phải ép kiểu rõ ràng:

```csharp
decimal x = 10m;
float y = 2.5f;
decimal result = x / (decimal)y;
```

## CHIA LẤY PHẦN DƯ `%`

**Toán tử phần dư** `%` thực hiện phép tính lấy phần dư sau khi chia toán hạng bên trái cho toán hạng bên phải.

### PHẦN DƯ SỐ NGUYÊN (Integer remainder)

Đối với các toán hạng là kiểu số nguyên, kết quả của `a % b` được tính theo công thức: `a % b = a - (a / b) * b`

- Dấu của phần dư khác 0 sẽ giống với dấu của toán hạng bên trái.

```csharp
Console.WriteLine(5 % 4);    // output: 1
Console.WriteLine(5 % -4);   // output: 1
Console.WriteLine(-5 % 4);   // output: -1
Console.WriteLine(-5 % -4);  // output: -1
```
Sử dụng phương thức [Math.DivRem()](https://learn.microsoft.com/en-us/dotnet/api/system.math.divrem) nếu bạn muốn tính cả thương và dư trong cùng một lần gọi hàm.

### PHẦN DƯ SỐ THỰC (Floating-point remainder)

Đối với toán hạng là `float` hoặc `double`, phép toán `x % y` (khi `x` và `y` hữu hạn) sẽ trả về một giá trị `z` sao cho:

- Nếu `z ≠ 0`, thì dấu của `z` sẽ giống với dấu của `x`

- Giá trị tuyệt đối của `z` được tính theo:

```csharp
|z| = |x| - n * |y|
```
***Trong đó:**

- `n` là số nguyên lớn nhất sao cho `n ≤ |x| / |y|`

- `|x|, |y|` là giá trị tuyệt đối của `x` và `y`

> **Ghi chú**  
> Phương pháp tính toán phần còn lại này tương tự như phương pháp được sử dụng cho các toán hạng số nguyên, nhưng khác với đặc tả IEEE 754.  
> Nếu bạn cần phép toán phần còn lại tuân thủ đặc tả IEEE 754, hãy sử dụng phương pháp [Math.IEEERemainder(x, y)](https://learn.microsoft.com/en-us/dotnet/api/system.math.ieeeremainder).


### PHẦN DƯ VỚI `DECIMAL`

- Khi toán hạng là kiểu `decimal`, toán tử % tương đương với toán tử phần dư của lớp `System.Decimal`

- Cách hoạt động tương tự như với `double`, nhưng chính xác hơn

**Ví dụ với số thực:**

```csharp
Console.WriteLine(-5.2f % 2.0f); // output: -1.2
Console.WriteLine(5.9 % 3.1);    // output: 2.8
Console.WriteLine(5.9m % 3.1m);  // output: 2.8
```

# TOÁN TỬ SO SÁNH (Relational / Comparison Operators)

**Toán tử so sánh** là các toán tử **hai ngôi**, dùng để **so sánh hai giá trị** và trả về **kết quả kiểu `bool`** (`true` hoặc `false`).


| Toán tử | Ý nghĩa                   | Ví dụ         | Kết quả |
|---------|----------------------------|---------------|---------|
| `==`    | Bằng nhau                  | `5 == 5`      | `true`  |
| `!=`    | Khác nhau                  | `5 != 3`      | `true`  |
| `<`     | Nhỏ hơn                    | `3 < 5`       | `true`  |
| `>`     | Lớn hơn                    | `7 > 4`       | `true`  |
| `<=`    | Nhỏ hơn hoặc bằng         | `5 <= 5`      | `true`  |
| `>=`    | Lớn hơn hoặc bằng         | `6 >= 2`      | `true`  |

## TOÁN TỬ BẰNG NHAU & KHÁC NHAU `==` `!=`

Toán tử bằng (`==`) và khác (`!=`) dùng để so sánh giá trị của hai toán hạng, trả về kết quả kiểu `bool`

