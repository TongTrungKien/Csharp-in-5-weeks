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
