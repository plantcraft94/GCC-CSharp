# I. Chương trình đầu tiên
## 1. Môi trường và IDE:

Cách 1 : Sử dụng các IDE như Visual Studio hoặc Jetbrain Rider
Cách 2: Tải ,Net và dùng Vs Code + các extension cần thiết (C#, C# Dev Kit,...)

## 2. Cách tạo 1 Console Project mới 

Với những bạn dùng Visual Studio/ Rider : 
 - tạo theo IDE nhưng nhớ tick cái "**Do not use top-level statements**"
Với những bạn dùng VS Code :
- Bước 1 : Mở Command Palette (dùng Ctrl + Shift + P) hoặc (Help > Show All Commands ở thanh trên cùng) và tìm và chọn ".NET: New Project"
- Bước 2 : Tìm và chọn "Console App" trong list
- Bước 3 : Đặt tên và Chọn "Default directory" (hoặc Chọn vị trí khác để lưu project)
- Bước 4 : Chọn "**Show all template options**" , chọn **Do not use top-level statements** và chọn **True**
- Bước 5 : Chọn "**Create Project**" và đợi
- Bước 6 : mở file *Program.cs* (đây là file các bạn viết code)

## 3. Tắt implicit `using` directives ( tắt cho chắc vì sợ nếu bật thì codeforce sẽ báo lỗi )

Mở file `<tênproject>.csproj`
Trong dòng
```xml
<ImplicitUsings>disable</ImplicitUsings>
```
chỉnh enable thành disable (hoặc xóa cả dòng đi)

## 4. Chương trình đầu tiên

1 chương trình C# thường có cấu trúc như sau:

```c#
using System;

namespace ConsoleApp1
{
	class Program
	{
	    static void Main(string[] args)
	    {
	        //code
	    }
	}
}
```

VD: Chương trình Hello World trong C#:

```c#
using System; // sử dụng class System

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```

# II.  C\# syntax

## 1. Xuất:

```csharp
Console.WriteLine("Hello World!"); // in ra dòng mới 
cout << "Hello World!" << endl;    // trong C++;
//-------------------------------------------------------------
Console.Write("Hello World!");     //in trên cùng dòng
cout << "Hello World!";            // trong C++
```

## 2. Kiểu dữ liệu

| C# type/keyword | Range                                                   | Size                    |
| --------------- | ------------------------------------------------------- | ----------------------- |
| `sbyte`         | -128 to 127                                             | Signed 8-bit integer    |
| `byte`          | 0 to 255                                                | Unsigned 8-bit integer  |
| `short`         | -32,768 to 32,767                                       | Signed 16-bit integer   |
| `ushort`        | 0 to 65,535                                             | Unsigned 16-bit integer |
| `int`           | -2,147,483,648 to 2,147,483,647                         | Signed 32-bit integer   |
| `uint`          | 0 to 4,294,967,295                                      | Unsigned 32-bit integer |
| `long`          | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | Signed 64-bit integer   |
| `ulong`         | 0 to 18,446,744,073,709,551,615                         | Unsigned 64-bit integer |

VD: những kiểu dữ liệu hay dùng
```csharp
int myNum = 5;
long myNum = 15000000000l; // lưu ý kết thúc = l
float myFloatNum = 3.14f;  // lưu ý kết thúc = f (hay dùng trong làm game)      
double myDoubleNum = 5.99; // số thực nếu ko có f ở cuối thì mặc định là double  
char myLetter = 'D';        
bool myBool = true;         
string myText = "Hello";
```

### Ép kiểu (type casting):

Có 2 loại chính:

#### Ép kiểu ngầm định (Implicit casting): xảy ra tự động, dùng khi muốn biến đổi từ kiểu dữ liệu nhỏ sang lớn :

`char` -> `int` -> `long` -> `float` -> `double`

Vd:
```csharp
int a = 10;
long b = a;      // int → long
float c = b;     // long → float
double d = c;    // float → double
```

#### Ép kiểu tường minh (Explicit casting): phải tự ép kiểu, dùng khi biến đổi từ kiểu dữ liệu lớn sang nhỏ

`double` -> `float` -> `long` -> `int` -> `char`

Cú pháp: `(<Kiểu dữ kiệu mới>) <tên biến>`
Vd:
```csharp
double x = 9.7;
int y = (int)x;   // y = 9 (mất phần thập phân)

long n = 10000000000;
int m = (int)n;   // tràn số (overflow)
```

#### Ép kiểu sử dụng `Convert`
Các hàm hay dùng:

`Convert.ToBoolean`
`Convert.ToDouble`
`Convert.ToSingle` ( `float` )
`Convert.ToString`
`Convert.ToInt32` (`int`)
`Convert.ToInt64` (`long`)


```csharp
double x = 5.9;
int y = Convert.ToInt32(x);  // y = 6 (làm tròn)
```

`Convert` sẽ làm tròn các số double/float thi chuyển về số int

#### Ép kiểu dùng `Parse`

Dùng khi chuyển từ string sang số (hoặc dùng convert)

cú pháp: `<kiểu dữ liệu>.Parse(string)`

VD:
```Csharp
int x = int.Parse("123");
double y = double.Parse("3.14");
```
## 3. Nhập:

`Console.ReadLine()` : Nhập vào 1 dòng, trả về string và giống với getline trong C++

## 4. String

Giống C++ nhưng có 1 số cái mới:

### String Interpolation

VD:
```csharp
string firstName = "John";
string lastName = "Doe";
string name = $"My full name is: {firstName} {lastName}";
Console.WriteLine(name);
```

### StringBuilder

Trong C#, **`string` là immutable** (bất biến), tức là mỗi lần bạn thay đổi chuỗi thì thực chất nó tạo ra một chuỗi mới → gây tốn bộ nhớ và chậm nếu thay đổi nhiều lần.

`StringBuilder` (trong namespace `System.Text`) được dùng để **xây dựng và chỉnh sửa chuỗi hiệu quả hơn** khi bạn cần nối, chèn, xóa, thay thế nhiều lần.

VD:

```C#
using System;
using System.Text;

class Program
{
    static void Main()
    {
        StringBuilder sb = new StringBuilder("Xin chào");

        sb.Append(" C#");          // Thêm vào cuối
        sb.AppendLine("!");        // Thêm + xuống dòng
        sb.Insert(0, "Nói: ");     // Chèn vào vị trí chỉ định
        sb.Replace("C#", "C Sharp"); // Thay thế chuỗi
        sb.Remove(0, 5);           // Xóa 5 ký tự từ đầu

        Console.WriteLine(sb.ToString()); // Chuyển về string
    }
}

```
#### Các phương thức hay dùng
- `Append(string)` → nối thêm.
    
- `AppendLine(string)` → nối thêm + xuống dòng.
    
- `Insert(vị trí, chuỗi)` → chèn vào vị trí.
    
- `Remove(vị trí, số lượng)` → xóa ký tự.
    
- `Replace(cũ, mới)` → thay thế chuỗi.
    
- `Clear()` → xóa toàn bộ nội dung.
    
- `ToString()` → trả về dạng `string`.

## 5. if - else;

Giống c++;

## 6. switch - case:

Giống C++ nhưng có thể hoạt động với string

## 7. while

Giống C++

## 8. for

Giống C++

### foreach

Dùng để duyệt các phần tử trong mảng

Cú pháp:
```csharp
foreach (type variableName in arrayName) 
{
  // code block to be executed
}
```

## 9. Mảng

Khởi tạo:

```c#
<kiểu dữ liệu>[] tên_biến;
```

VD:

```C#
int[] a = {1,2,3,4,5};
```

### Truy cập phần tử trong mảng

```c#
string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
Console.WriteLine(cars[0]);
// sẽ in ra "Volvo"
```

### Thay đổi phần tử trong mảng

```C#
string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
cars[0] = "Opel";
Console.WriteLine(cars[0]);
// sẽ in ra Opel thay vì Volvo
```

### Số lượng phần tử trong mảng

Bên C++ dùng: `tên_mảng.size()`

Bên C#
Dùng `tên_mảng.Length`:

```C#
string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
Console.WriteLine(cars.Length);
// sẽ in ra 4
```

### Cách tạo mảng biết trước số lượng phần tử:

Bên C++:
```
int a[4];
```

Bên C#:

```C#
int[] a = new int[4];
```

### Đảo ngược mảng:

Ta có mảng sau:

```C#
string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
```

Muốn đảo ngược mảng ta dùng `{Csharp} Array.Reverse(<tên mảng>) `

VD:
```C#
string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
Array.Reverse(cars);
// mảng hiện tại trở thành {"Mazda","Ford","BMW","Volvo"}
```

### Sắp xếp mảng

dùng Array.Sort(<tên mảng>)

VD
```C#
// bé -> lớn
int[] arr = { 5, 2, 9, 1, 7 };
Array.Sort(arr);
// mảng bây h trở thành {1,2,5,7,9}

// lớn -> bé
int[] arr = { 5, 2, 9, 1, 7 };
Array.Sort(arr);
// mảng bây h trở thành {9,7,5,2,1}
```

## 10. Hàm
### 1. Khái niệm
- Hàm là một tập hợp các câu lệnh sẽ được thực thi nối tiếp vào chương trình khi ta gọi nó. VD: hàm `Main()`.
- Ví dụ: Hành động bật máy tính sẽ chạy các việc như bật wifi, bật ánh sáng màn hình, kết nối đến pin,...
 ```csharp
using System;

class Program {
    static void Main(string[] args) {
        Console.WriteLine("Hello World");
    }
}
 ```

### 2. Khai báo và cách sử dụng
```csharp
<Phạm vi truy cập> <Kiểu trả về> <Tên hàm>(Danh sách tham số) {
    // Lệnh thực thi
}
```
- VD:
```csharp
public static bool IsPrime(int number) {
    if (number < 2) return false;
    for (int i = 2; i <= Math.Sqrt(number); i++) {
        if (number % i == 0) return false;
    }
    return true;
}
```
+ Lưu ý, bổ sung:
	+ Xác định kiểu trả về là gì và trả về phù hợp. Nếu không trả về thì dùng hàm void.
	+ Mỗi hàm nên thực thi các hành động duy nhất để tối ưu chương trình.
	+ Đặt tên hàm dễ nhớ, có ý nghĩa để dễ tái sử dụng.
### 3. Truyền tham số, tham trị
###  1. Truyền tham trị (Pass by Value)
- Mặc định trong C#, tham số là **tham trị** → truyền bản sao. 
- Thay đổi trong hàm không ảnh hưởng biến gốc.
- VD:
```csharp
static void ChangeValue(int n) {
    n += 100;
    Console.WriteLine("Trong hàm: " + n);
}

static void Main() {
    int x = 10;
    ChangeValue(x);
    Console.WriteLine("Ngoài hàm: " + x); // x vẫn = 10
}
```
- Giải thích: Khi truyền tham trị, đối số và tham số là hai biến độc lập. Việc thay đổi giá trị tham số trong hàm không ảnh hưởng đến đối số.
### 2. Truyền tham chiếu (Pass by Reference)
- Dùng từ khóa `ref`.
- Tham số trong hàm trỏ trực tiếp đến biến gốc → thay đổi ảnh hưởng ra ngoài.
- VD:
```csharp
static void ChangeValue(ref int n) {
    n += 100;
}

static void Main() {
    int x = 10;
    ChangeValue(ref x);
    Console.WriteLine(x); // 110
}
```
- Giải thích: Khi truyền tham chiếu, tham số và đối số cùng quản lý một ô nhớ. Việc thay đổi giá trị tham số sẽ ảnh hưởng trực tiếp đến đối số.
### 3. Tham số `out`

- Tương tự `ref`, nhưng bắt buộc phải gán giá trị trong hàm trước khi dùng.
- Thường dùng khi hàm trả về nhiều giá trị.
```csharp
static void Divide(int a, int b, out int q, out int r) {
    q = a / b;
    r = a % b;
}

static void Main() {
    Divide(10, 3, out int thuong, out int du);
    Console.WriteLine($"Thương: {thuong}, Dư: {du}");
}
```
### 5. Truyền mảng & đối tượng

- Mảng và `class` trong C# là **reference type**, truyền vào hàm sẽ thay đổi trực tiếp dữ liệu gốc.
- `struct` là **value type**, mặc định truyền bản sao.
- VD: 
```csharp
static void ChangeArr(int[] arr) {
    arr[0] = 999;
}

static void Main() {
    int[] nums = {1, 2, 3};
    ChangeArr(nums);
    Console.WriteLine(nums[0]); // 999
}
```
### BÀI TẬP

1. Viết hàm kiểm tra số nguyên tố.
2. Viết hàm hoán đổi 2 số bằng `ref`.   
3. Viết hàm tính giai thừa bằng đệ quy.
4. Viết hàm nhập mảng số nguyên, sắp xếp tăng dần.

---

## 11. Struct (Dạy Nhanh)
### 1. Khái niệm
- Struct hay cấu trúc là một kiểu dữ liệu mà tự bạn định nghĩa ra bằng cách gộp nhiều kiểu dữ liệu có sẵn.
- Trong C#: `struct` là **Value Type** (sao chép khi gán/truyền).
### 2. Khai Báo
- Lưu ý: Hàm Constructor: Cần khởi tạo TẤT CẢ field
```C#
struct Student {
    public int Age;
    public string Name;

    public Student(int age, string name) { //Constructor
        Age = age;
        Name = name;
    }
}

static void Main() {
    Student s1 = new Student(20, "Phuc");
    Console.WriteLine($"{s1.Name}, {s1.Age}");
}
```
### 3. Truy cập thuộc tính

```C#
Student s;
s.Age = 21;
s.Name = "Dong";
Console.WriteLine(s.Name);
```
### 4. Struct lồng nhau
```C#
struct Author {
    public string Name;
}

struct Book {
    public string Title;
    public Author Writer;
}
```
### 5. Mảng struct
```C#
Student[] list = new Student[3];
list[0] = new Student(20, "Phuc");
list[1] = new Student(22, "Dong");
list[2] = new Student(21, "Tung");

foreach (var s in list) {
    Console.WriteLine($"{s.Name}, {s.Age}");
}
```
### BÀI TẬP
1. Tạo struct `Rectangle` (Width, Height) → viết hàm tính diện tích.
2. Tạo mảng `Student` → nhập n sinh viên, sắp xếp theo tuổi.
3. Tạo struct `Fraction` → viết hàm rút gọn phân số.


