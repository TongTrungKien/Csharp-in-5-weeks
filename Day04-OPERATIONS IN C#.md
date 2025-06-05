# OPERATIONS IN C#

Bài viết này sẽ hướng dẫn bạn từ cơ bản đến nâng cao về các nhóm toán tử phổ biến trong C#, bao gồm:

-  Toán tử gán
-  Toán tử số học
-  Toán tử một ngôi
-  Toán tử so sánh
-  Toán tử luận lý điều kiện
-  Toán tử điều kiện `?:`
-  Overload toán tử & lưu ý đặc biệt
-  Độ ưu tiên và kết hợp toán tử

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

## TOÁN TỬ BẰNG NHAU `==` 

Toán tử so sánh bằng `==` trả về `true` nếu hai toán hạng bằng nhau, ngược lại trả về `false`.

### SO SÁNH GIÁ TRỊ TRONG C#

- Các toán hạng của [kiểu giá trị dựng sẵn](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-types#built-in-value-types) được xem là bằng nhau nếu giá trị của chúng bằng nhau.

```csharp
int a = 1 + 2 + 3;
int b = 6;
Console.WriteLine(a == b);  // output: True
char c1 = 'a';
char c2 = 'A';
Console.WriteLine(c1 == c2);  // output: False
Console.WriteLine(c1 == char.ToLower(c2));  // output: True
```
> **Giải thích**:
> - `a == b`: So sánh hai giá trị `int` – bằng nhau nên kết quả là `True`.
> - `c1 == c2`: So sánh hai ký tự `'a'` và `'A'` – khác mã Unicode, kết quả là `False`.
> - `char.ToLower(c2)` chuyển `'A'` thành `'a'`, nên `c1 == char.ToLower(c2)` → `True`.
>  Kiểu `int` và `char` là **kiểu giá trị (value types)**, nên toán tử `==` so sánh **giá trị thật sự bên trong**, không phải địa chỉ bộ nhớ.

> **Lưu ý**: Đối với các toán tử `==`, [`!=`, `<`, `>`, `<=`, `>=`](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/comparison-operators), nếu một trong hai toán hạng là `NaN` ([`double.NaN`](https://learn.microsoft.com/en-us/dotnet/api/system.double.nan#system-double-nan), [`float.NaN`](https://learn.microsoft.com/en-us/dotnet/api/system.single.nan#system-single-nan)), kết quả luôn là `false`.  
> Nếu cần kiểm tra giá trị có phải `NaN` không, hãy dùng `Double.IsNaN(x)` hoặc `Single.IsNaN(x)`.

```csharp
double x = double.NaN;
Console.WriteLine(Double.IsNaN(x)); // True
```

### SO SÁNH KIỂU THAM CHIẾU (Reference types equality)

Mặc định, các đối tượng kiểu **tham chiếu** (trừ `record`) được xem là **bằng nhau (`==`) chỉ khi chúng cùng tham chiếu đến một đối tượng trong bộ nhớ** (tức là cùng địa chỉ).

**Ví dụ:**

```csharp
public class ReferenceTypesEquality
{
    public class MyClass
    {
        private int id;

        public MyClass(int id) => this.id = id;
    }

    public static void Main()
    {
        var a = new MyClass(1);
        var b = new MyClass(1);
        var c = a;

        Console.WriteLine(a == b);  // output: False
        Console.WriteLine(a == c);  // output: True
    }
}
```
- `a` và `b` là hai đối tượng khác nhau, mặc dù có cùng nội dung `(id = 1)` → `a == b` là `false
- `c` tham chiếu cùng đối tượng với `a` → `a == c` là `tru`e

> Lưu ý:
Như ví dụ cho thấy, các kiểu tham chiếu do người dùng định nghĩa hỗ trợ toán tử `==` theo mặc định.
Tuy nhiên, một kiểu tham chiếu có thể định nghĩa lại (overload) toán tử `==`.
Nếu điều đó xảy ra, hãy sử dụng phương thức [Object.ReferenceEquals](https://learn.microsoft.com/en-us/dotnet/api/system.object.referenceequals) để kiểm tra xem hai tham chiếu có trỏ tới cùng một đối tượng hay không.

### SO SÁNH KIỂU `record` (Record types equality)

Kiểu `record` trong C# hỗ trợ toán tử `==` và `!=` mặc định với ngữ nghĩa **so sánh theo giá trị**. Hai record được xem là bằng nhau khi cả hai cùng `null` hoặc tất cả các trường và thuộc tính tự động có giá trị tương ứng bằng nhau. Trong ví dụ dưới đây, `p1` và `p2` khác nhau vì giá trị các trường khác nhau, còn `p1` và `p3` bằng nhau vì mọi trường đều giống nhau:

```csharp
public class RecordTypesEquality
{
    public record Point(int X, int Y, string Name);
    public record TaggedNumber(int Number, List<string> Tags);

    public static void Main()
    {
        var p1 = new Point(2, 3, "A");
        var p2 = new Point(1, 3, "B");
        var p3 = new Point(2, 3, "A");

        Console.WriteLine(p1 == p2);  // output: False
        Console.WriteLine(p1 == p3);  // output: True

        var n1 = new TaggedNumber(2, new List<string>() { "A" });
        var n2 = new TaggedNumber(2, new List<string>() { "A" });
        Console.WriteLine(n1 == n2);  // output: False
    }
}
```

- Tuy nhiên, nếu record chứa thành viên là kiểu tham chiếu như `List<string>`, thì phần đó vẫn được so sánh theo địa chỉ bộ nhớ, chứ không so sánh nội dung. Vì `n1.Tags` và `n2.Tags` là hai danh sách khác nhau, dù có cùng phần tử "`A`", thì `n1 == n2` vẫn là `false`.

- Muốn so sánh nội dung của các thành viên tham chiếu trong record, bạn cần override logic so sánh hoặc kiểm tra từng phần tử bằng cách thủ công (ví dụ dùng `SequenceEqual()` cho danh sách).

### SO SÁNH CHUỖI (String equality)

Hai chuỗi [`string`](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/reference-types#the-string-type) được xem là bằng nhau khi cả hai đều `null`, hoặc chúng có cùng độ dài và từng ký tự tại mỗi vị trí đều giống nhau (theo mã Unicode). So sánh mặc định là **phân biệt chữ hoa/thường** (case-sensitive, ordinal). Trong ví dụ dưới đây, `s1` và `s2` khác nhau về chữ hoa/thường nhưng khi chuyển `s2` về chữ thường thì hai chuỗi bằng nhau:

```csharp
string s1 = "hello!";
string s2 = "HeLLo!";
Console.WriteLine(s1 == s2.ToLower());  // output: True

string s3 = "Hello!";
Console.WriteLine(s1 == s3);  // output: False
```
- Nếu muốn so sánh không phân biệt hoa thường hoặc theo tiêu chí văn hóa cụ thể, bạn có thể dùng `string.Equals(s1, s2, StringComparison.OrdinalIgnoreCase)` hoặc [các so sánh chuỗi trong C#](https://learn.microsoft.com/en-us/dotnet/csharp/how-to/compare-strings) khác


### SO SÁNH DELEGATE (Delegate equality)

Hai [delegate](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/delegates/) được xem là bằng nhau khi cả hai cùng `null`, hoặc khi chúng có cùng kiểu, cùng số lượng phần tử trong danh sách thực thi (`invocation list`) và từng phần tử ở các vị trí tương ứng bằng nhau. Ví dụ dưới đây cho thấy hai delegate `b` và `c` khác nhau về tham chiếu (object.ReferenceEquals là false) nhưng bằng nhau về nội dung nên `b == c` là `true`:

```csharp
Action a = () => Console.WriteLine("a");

Action b = a + a;
Action c = a + a;
Console.WriteLine(Object.ReferenceEquals(b, c)); // output: False
Console.WriteLine(b == c);                       // output: True
```
- Tuy nhiên, nếu danh sách gọi của delegate chứa các phương thức từ hai đối tượng khác nhau (receiver khác nhau), thì hai delegate sẽ không bằng nhau:

```csharp
var o1 = new object();
var o2 = new object();
var d1 = o1.ToString;
var d2 = o2.ToString;
Console.WriteLine(Object.ReferenceEquals(d1, d2)); // output: False
Console.WriteLine(d1 == d2);                       // output: False
```
- Để biết thêm thông tin, hãy xem phần [Toán tử so sánh delegate](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/expressions#12129-delegate-equality-operators) trong [đặc tả ngôn ngữ C#](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/readme).
- Ngoài ra, hai [lambda](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-expressions) giống hệt nhau về logic nhưng được tạo độc lập cũng sẽ không bằng nhau:

```csharp 
Action a = () => Console.WriteLine("a");
Action b = () => Console.WriteLine("a");

Console.WriteLine(a == b);             // output: False
Console.WriteLine(a + b == a + b);     // output: True
Console.WriteLine(b + a == a + b);     // output: False
```
- So sánh delegate rất nhạy cảm: chỉ bằng nhau khi toàn bộ danh sách gọi giống nhau về số lượng, thứ tự và cả “receiver” (đối tượng chứa phương thức).

## TOÁN TỬ SO SÁNH KHÁC NHAU `!=` (Inequality operator)

Toán tử `!=` trả về `true` nếu hai toán hạng **không bằng nhau**, và trả về `false` nếu chúng bằng nhau.  
Đối với các kiểu dữ liệu dựng sẵn (built-in types), biểu thức `x != y` tương đương với `!(x == y)`.

**Ví dụ:**

```csharp
int a = 1 + 1 + 2 + 3;
int b = 6;
Console.WriteLine(a != b); // output: True

string s1 = "Hello";
string s2 = "Hello";
Console.WriteLine(s1 != s2); // output: False

object o1 = 1;
object o2 = 1;
Console.WriteLine(o1 != o2); // output: True
```

- `!=` là toán tử ngược logic với `==`, và hành vi phụ thuộc vào loại dữ liệu:

- Với `value type`: so sánh giá trị

- Với `reference type`: mặc định so sánh địa chỉ bộ nhớ (trừ khi overload)


## TOÁN TỬ NHỎ HƠN (Less than operator) `<`

Trả về `true` nếu toán hạng bên trái **nhỏ hơn** toán hạng bên phải trả về `false` nếu không đúng.

```csharp
Console.WriteLine(1 < 2);           // True
Console.WriteLine(1.1 < 1.1);       // False
Console.WriteLine(2.1 < 1.1);       // False
Console.WriteLine(double.NaN < 1.1); // False
```

## TOÁN TỬ LỚN HƠN (Greater than) `>`

Trả về true nếu toán hạng bên trái lớn hơn toán hạng bên phải.

```csharp
Console.WriteLine(2 > 1);           // True
Console.WriteLine(1.1 > 1.1);       // False
Console.WriteLine(1.1 > 2.1);       // False
Console.WriteLine(double.NaN > 1.1); // False
```

## TOÁN TỬ NHỎ HƠN HOẶC BẰNG (Less than or equal) `<=`
Trả về `true` nếu toán hạng bên trái nhỏ hơn hoặc bằng toán hạng bên phải.

```csharp
Console.WriteLine(1 <= 2);           // True
Console.WriteLine(1.1 <= 1.1);       // True
Console.WriteLine(2.1 <= 1.1);       // False
Console.WriteLine(double.NaN <= 1.1); // False
```

## TOÁN TỬ LỚN HƠN HOẶC BẰNG (Greater than or equal) `>=`

Trả về `true` nếu toán hạng bên trái lớn hơn hoặc bằng toán hạng bên phải.

```csharp
Console.WriteLine(2 >= 1);           // True
Console.WriteLine(1.1 >= 1.1);       // True
Console.WriteLine(1.1 >= 2.1);       // False
Console.WriteLine(double.NaN >= 1.1); // False
```
>Lưu ý: Nếu bất kỳ toán hạng nào là NaN (Not a Number), thì kết quả của các phép so sánh đều là false, bao gồm cả == và !=.

## KHẢ NĂNG OVERLOAD CỦA CÁC TOÁN TỬ SO SÁNH (Operator overloadability)

Các kiểu do người dùng định nghĩa (`class`, `struct`) **có thể overload** các toán tử so sánh như `==`, `!=`, `<`, `>`, `<=`, `>=` để tùy chỉnh hành vi so sánh.

- Nếu bạn [overload](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/operator-overloading) một trong hai toán tử `==` hoặc `!=`, thì **bắt buộc phải overload cả hai** để đảm bảo tính nhất quán.
- Tương tự, nếu bạn overload một trong hai toán tử `<` hoặc `>`, thì **cũng phải overload cả hai**.  
- Và nếu overload `<=` hoặc `>=`, thì **cả hai cũng phải được định nghĩa lại cùng lúc**.

> Nếu bạn chỉ overload một toán tử mà bỏ qua toán tử còn lại, chương trình sẽ **không biên dịch được**.

---

### Với kiểu `record`:
Các kiểu `record` **không thể override trực tiếp** toán tử `==` và `!=`.  
Nếu bạn cần tùy chỉnh cách so sánh của record, hãy cài đặt interface [`IEquatable<T>`](https://learn.microsoft.com/en-us/dotnet/api/system.iequatable-1.equals) và ghi đè phương thức `Equals` theo mẫu:

```csharp
public virtual bool Equals(T? other);
```

# TOÁN TỬ LUẬN LÝ ĐIỀU KIỆN

- `&&`: Phép toán luận lý **VÀ** (AND) – trả về `true` nếu **cả hai đều đúng**
- `||`: Phép toán luận lý **HOẶC** (OR) – trả về `false` nếu **cả hai đều sai**

## TOÁN TỬ `&&` (AND logic có rút gọn – short-circuit)


Toán tử `&&` thực hiện phép toán **VÀ logic** giữa hai toán hạng.  
Biểu thức `x && y` sẽ trả về `true` **chỉ khi cả `x` và `y` đều là `true`**, ngược lại sẽ trả về `false`.

Điểm đặc biệt của `&&` là **short-circuit evaluation** – nếu `x` đã là `false`, thì **`y` sẽ không được đánh giá (không chạy)** vì kết quả chắc chắn là `false` rồi.

**Ví dụ:**

```csharp
bool SecondOperand()
{
    Console.WriteLine("Second operand is evaluated.");
    return true;
}

bool a = false && SecondOperand();
Console.WriteLine(a);
// Output:
// False

bool b = true && SecondOperand();
Console.WriteLine(b);
// Output:
// Second operand is evaluated.
// True
```
- Dòng false && SecondOperand() → vế trái đã false, nên vế phải không được thực thi

- Dòng true && SecondOperand() → cần kiểm tra cả hai, nên SecondOperand() được gọi và in ra dòng chữ

> Nếu bạn muốn [toán tử AND](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-and-operator-) nhưng luôn đánh giá cả hai vế, dùng toán tử & (logical AND không rút gọn)

## TOÁN TỬ `||` (OR logic có rút gọn – short-circuit)

Toán tử `||` thực hiện phép toán **HOẶC logic** giữa hai toán hạng.  
Biểu thức `x || y` trả về `true` nếu **ít nhất một trong hai** (`x` hoặc `y`) là `true`.  
Ngược lại, nếu cả hai đều `false`, kết quả là `false`.

Toán tử `||` cũng hỗ trợ **short-circuit evaluation** – nếu `x` đã là `true`, thì **`y` sẽ không được đánh giá (không chạy)** vì kết quả chắc chắn là `true`.

**Ví dụ:**

```csharp
bool SecondOperand()
{
    Console.WriteLine("Second operand is evaluated.");
    return true;
}

bool a = true || SecondOperand();
Console.WriteLine(a);
// Output:
// True

bool b = false || SecondOperand();
Console.WriteLine(b);
// Output:
// Second operand is evaluated.
// True
```
- Dòng `true || SecondOperand()` → vế trái đã là `true`, nên `SecondOperand()` không được gọi

- Dòng `false || SecondOperand()` → cần kiểm tra cả hai → `SecondOperand()` được gọi → in dòng chữ

>Nếu bạn muốn thực hiện phép [OR logic](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-or-operator-) nhưng luôn đánh giá cả hai vế, hãy dùng toán tử | (logical OR không rút gọn)

# TOÁN TỬ ĐIỀU KIỆN `?:`(Ternary Conditional Operator)

Toán tử `?:`, còn gọi là **toán tử điều kiện ba ngôi (ternary operator)**, là một cú pháp rút gọn của `if-else`, dùng để trả về **một trong hai biểu thức** tùy theo điều kiện `bool`.  
Nó thường được dùng khi bạn cần **tính ra một giá trị** theo điều kiện, mà không cần cả khối `if`.

**Cú pháp**

```csharp
condition ? consequent : alternative;
```

- `condition`: biểu thức logic (`bool`)
- Nếu `condition == true`, biểu thức `consequent` sẽ được thực thi và trả về kết quả.
- Nếu `condition == false`, biểu thức `alternative` sẽ được thực thi.

> **Chỉ một trong hai biểu thức (consequent hoặc alternative) được đánh giá.**

---

**Ví dụ:**

```csharp
string GetWeatherDisplay(double tempInCelsius) =>
    tempInCelsius < 20.0 ? "Cold." : "Perfect!";

Console.WriteLine(GetWeatherDisplay(15));  // Output: Cold.
Console.WriteLine(GetWeatherDisplay(27));  // Output: Perfect!
```

---

### GHI NHỚ NHANH

```text
is this condition true ? yes : no
```

---

## TƯƠNG THÍCH KIỂU DỮ LIỆU (Target typing)

Toán tử `?:` có thể suy ra kiểu kết quả nếu kiểu mong đợi (target type) đã rõ.

###  TRƯỜNG HỢP TARGET TYPE RÕ RÀNG:

```csharp
bool condition = true;
int? x = condition ? 12 : null; // hợp lệ vì target type là int?
```

### TRƯỜNG HỢP DÙNG `var`: 

- Khi dùng [`var`](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/declarations#implicitly-typed-local-variables), **kiểu của hai nhánh phải tương thích**, hoặc có ép kiểu rõ ràng.

```csharp
var x = condition ? 12 : (int?)null; // hợp lệ
```

> Nếu hai nhánh không có kiểu chung, hoặc không ép kiểu, sẽ bị lỗi biên dịch.

---

## TÍNH KẾT HỢP PHẢI (Right-associative)

Biểu thức `?:` có tính kết hợp phải → nghĩa là:

```csharp
a ? b : c ? d : e;
```

sẽ được hiểu như:

```csharp
a ? b : (c ? d : e);
```

---

## BIỂU THỨC THAM CHIẾU `ref` CÓ ĐIỀU KIỆN (Conditional `ref` expression)

Toán tử `?:` cũng hỗ trợ truy xuất hoặc gán **theo tham chiếu** bằng cách thêm từ khóa `ref`.

**Ví dụ:**

```csharp
int[] smallArray = { 1, 2, 3, 4, 5 };
int[] largeArray = { 10, 20, 30, 40, 50 };

int index = 7;
ref int refValue = ref (index < 5 ? ref smallArray[index] : ref largeArray[index - 5]);
refValue = 0;

index = 2;
(index < 5 ? ref smallArray[index] : ref largeArray[index - 5]) = 100;

Console.WriteLine(string.Join(" ", smallArray));  // 1 2 100 4 5
Console.WriteLine(string.Join(" ", largeArray));  // 10 20 0 40 50
```

- Biểu thức `ref` có điều kiện cũng chỉ đánh giá **một nhánh**.
- `consequent` và `alternative` phải có cùng kiểu và đều là **tham chiếu (`ref`)**.
- Biểu thức `ref` có điều kiện **không hỗ trợ target typing**.

---

## SO SÁNH VỚI CÂU LỆNH `if`

Toán tử `?:` thường được dùng để rút gọn biểu thức [`if-else`](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements#the-if-statement) đơn giản trả về giá trị:

```csharp
int input = new Random().Next(-5, 5);

// Cách dùng if:
string classify;
if (input >= 0)
    classify = "nonnegative";
else
    classify = "negative";

// Dùng toán tử ?:
classify = (input >= 0) ? "nonnegative" : "negative";
```

> Ưu điểm: **gọn hơn**, dễ đọc khi xử lý giá trị nhanh.  
> Không phù hợp cho logic phức tạp hoặc nhiều dòng lệnh.

---

## KHẢ NĂNG OVERLOAD TOÁN TỬ `?:`

- Các **kiểu do người dùng định nghĩa** (`class`, `struct`, `record`) **không thể overload** toán tử `?:`.
- Nếu cần thay đổi hành vi lựa chọn giá trị theo điều kiện, hãy dùng `if` hoặc pattern matching.

---
## Tài liệu liên quan

- [Tài liệu chính thức về `?:`](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator)
- [Tài liệu về `if` statement](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements#the-if-statement)
- [Tài liệu về `??`, `??=`, `?.`, `?[]` operators](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/)
- [IDE0075 - Gợi ý dùng toán tử `?:`](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/style-rules/ide0075)

---

>**Mẹo**: Dùng `?:` trong nội suy chuỗi, trong các biểu thức gán ngắn gọn, hoặc khi cần gán giá trị mặc định theo điều kiện — nhưng tránh lồng quá nhiều vì dễ làm giảm tính rõ ràng.

# ĐỘ ƯU TIÊN GIỮA CÁC TOÁN TỬ
Trong một biểu thức có nhiều toán tử, các toán tử có độ ưu tiên cao hơn sẽ được đánh giá trước các toán tử có độ ưu tiên thấp hơn.
Trong ví dụ sau, phép nhân được thực hiện trước vì nó có độ ưu tiên cao hơn phép cộng:

```csharp
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```
Sử dụng dấu ngoặc đơn để thay đổi thứ tự đánh giá mặc định do độ ưu tiên của toán tử quy định.

```csharp
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

Bảng sau liệt kê các toán tử C# bắt đầu từ mức ưu tiên cao nhất đến thấp nhất. Các toán tử trong mỗi hàng có cùng mức ưu tiên.


| **Toán tử**                                                                                              | **Nhóm / Mô tả**                                         |
|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| `x.y`, `f(x)`, `a[i]`, `x?.y`, `x?[i]`, `x++`, `x--`, `x!`, `new`, `typeof`, `checked`, `default`, `nameof`, `delegate`, `sizeof`, `stackalloc`, `x => y` | **Primary** (ưu tiên cao nhất)                         |
| `+x`, `-x`, `!x`, `~x`, `++x`, `--x`, `^x`, `(T)x`, `await`, `&x`, `*x`, `true`, `false`                  | **Unary**                                               |
| `x..y`                                                                                                    | **Range**                                               |
| `switch`, `with`                                                                                          | **Switch và With expressions**                          |
| `x * y`, `x / y`, `x % y`                                                                                 | **Multiplicative**                                      |
| `x + y`, `x - y`                                                                                          | **Additive**                                            |
| `x << y`, `x >> y`, `x >>> y`                                                                             | **Shift**                                               |
| `x < y`, `x > y`, `x <= y`, `x >= y`, `is`, `as`                                                          | **Relational và Type-testing**                         |
| `x == y`, `x != y`                                                                                        | **Equality**                                            |
| `x & y`                                                                                                   | **Boolean logic AND** hoặc **bitwise AND**             |
| `x ^ y`                                                                                                   | **Boolean logic XOR** hoặc **bitwise XOR**             |
| `x \| y`                                                                                                  | **Boolean logic OR** hoặc **bitwise OR**               |
| `x && y`                                                                                                  | **Conditional AND** (AND rút gọn)                      |
| `x \|\| y`                                                                                                 | **Conditional OR** (OR rút gọn)                        |
| `x ?? y`                                                                                                  | **Null-coalescing operator**                           |
| `x ? y : z`                                                                                               | **Toán tử điều kiện ba ngôi (ternary)**                |
| `x = y`, `x += y`, `x -= y`, `x *= y`, `x /= y`, `x %= y`, `x &= y`, `x ^= y`, `x \|= y`, `x <<= y`, `x >>= y`, `x >>>= y`, `x ??= y`, `=>` | **Assignment & Lambda** (ưu tiên thấp nhất)         |

- Biểu thức trong C# được đánh giá từ trái sang phải hoặc phải sang trái tùy vào nhóm toán tử.

- Để ưu tiên đánh giá theo ý bạn, nên dùng dấu ngoặc `()`.

# TÍNH KẾT HỢP CỦA TOÁN TỬ TRONG c# (Operator Associativity)

Khi các toán tử có **cùng độ ưu tiên**, **tính kết hợp (associativity)** sẽ xác định **thứ tự đánh giá** của các toán tử trong biểu thức.

---

## **Left-associative** (Kết hợp trái sang phải)

Hầu hết các toán tử nhị phân trong C# là **kết hợp trái** — tức là **được đánh giá từ trái sang phải**.

**Ví dụ:**

```csharp
a + b - c  // được hiểu là: (a + b) - c
```

-  Ngoại lệ: [các toán tử gán](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/assignment-operator) (`=`), [null-coalescing](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/null-coalescing-operator) (`??`, `??=`) không thuộc nhóm này.

## Right-associative (Kết hợp phải sang trái)

- Các toán tử sau là kết hợp phải — được đánh giá từ phải sang trái:

- Toán tử gán (`=`, `+=`, `-=`, v.v.)

- Toán tử `??`, `??=`

- Lambda (`=>`)

- Toán tử điều kiện `?:`

**Ví dụ**
```csharp
x = y = z; // được hiểu là: x = (y = z)
```

### Ghi chú quan trọng về toán tử null-chaining (`?.`)

```csharp
P?.A0?.A1
```

Nếu `P` là `null`, **thì cả `A0` và `A1` đều không được đánh giá**.  

Tương tự, trong:

```csharp
P?.A0.A1
```

→ Nếu `P` là `null`, **`A0` cũng không được đánh giá**.

Tham khảo thêm: [C# language specification - operator associativity](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/expressions#operator-associativity)

---

###  Ví dụ về ảnh hưởng của kết hợp

```csharp
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");
// Output: a = 1, b = 6
```

- Dòng `int a = 13 / 5 / 2;` thực hiện theo **kết hợp trái**:
  → `(13 / 5) / 2 = 2 / 2 = 1`

- Dòng `int b = 13 / (5 / 2);` có dấu ngoặc → thay đổi thứ tự thực hiện:
  → `5 / 2 = 2 → 13 / 2 = 6`

---

###  Mẹo

> **Luôn dùng dấu ngoặc `()` nếu bạn muốn kiểm soát rõ ràng thứ tự đánh giá toán tử**, đặc biệt trong biểu thức dài, dễ gây hiểu nhầm.
---

# Kết
Qua bài học hôm nay, bạn đã nắm được **hệ thống toàn diện các toán tử trong C#** — từ cơ bản như **gán, số học, so sánh**, cho đến nâng cao như **toán tử điều kiện `?:`**, **overload**, **kết hợp**, và **ưu tiên toán tử**.

Việc hiểu rõ từng loại toán tử không chỉ giúp bạn **viết mã hiệu quả hơn**, mà còn tránh được những lỗi logic khó phát hiện trong thực tế.  
Đặc biệt, những khái niệm như **short-circuit**, **target typing**, hay **conditional `ref`** sẽ rất hữu ích khi bạn làm việc với các biểu thức phức tạp trong các dự án thực tế.

> 💡 **Hãy nhớ:** Viết code tốt không chỉ là làm cho nó chạy được — mà là **làm cho nó rõ ràng, đúng, và dễ bảo trì**.  
> Và toán tử, chính là công cụ quan trọng để đạt được điều đó.

Hẹn gặp lại bạn trong những bài tiếp theo! 
# Link tham khảo
https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/comparison-operators#less-than-or-equal-operator-

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/equality-operators#code-try-0

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#code-try-6

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/pointer-related-operators#pointer-indirection-operator-

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/arithmetic-operators#code-try-6

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/assignment-operator#code-try-3

https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/

# HASHTAG

`Csharp-in-5-weeks` `Csharp`

# Author

[Dexter](https://github.com/TongTrungKien)
