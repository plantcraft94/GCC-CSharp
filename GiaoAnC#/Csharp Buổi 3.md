# 1. Độ phức tạp thời gian BigO

## Khái niệm thời gian chạy của chương trình

- `Thời gian chạy của chương trình` là quãng thời gian mà máy tính cần để thực hiện toàn bộ những yêu cầu mà người dùng đặt ra.

Cùng tham khảo ví dụ:

``` Csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            for (int i = 0; i < 100; i++)
            {
                Console.WriteLine("GCC");
            }
        }
    }
}
```

- Kết quả:

![alt](https://i.imgur.com/FrL9YPy.png) Ở ví dụ trên, ta có thể thấy: **thời gian mà chương trình chạy đó là 0.5713s**.

> **Câu hỏi đặt ra là:** Không nhẽ cứ mỗi lần chúng ta muốn biết được xem liệu chương trình, thuật toán mà ta định viết nhanh hay chậm ta lại phải code thử rồi chạy để xem thời gian sao?

Đó chính là lúc chúng ta cần đến việc đánh giá độ phức tạp thời gian.

## Độ phức tạp thời gian BigO

### Độ phức tạp thời gian

- **Độ phức tạp thời gian** là toàn bộ tài nguyên về thời gian mà máy tính cần để thực thi một thuật toán nào đó, được thể hiện bằng hàm số y = f(x). Thông thường, độ phức tạp thời gian sẽ dựa vào số lần mà một câu lệnh cơ bản với thời gian thực thi là hằng số được thực thi.
- Tuy nhiên, do các hàm số thể hiện độ phức tạp thường rất khó tính toán nên chúng ta cần một phương pháp đánh giá hiệu quả hơn. Một cách được sử dụng phổ biến đó là **Độ phức tạp thời gian BigO**.

### Độ phức tạp thời gian BigO

- **Độ phức tạp thời gian BigO (Big O notation)** thể hiện sự thay đổi của độ phức tạp thời gian phụ thuộc vào sự thay đổi của dữ liệu đầu vào.

![alt](https://toidicodedao.com/wp-content/uploads/2020/11/screenshot-2020-11-14-at-3.43.23-pm.jpg)

đồ thị minh hoạ sự phụ thuộc của **số lệnh cơ bản được thực thi (N) trục Oy vào kích thước dữ liệu đầu vào (n) trục Ox**.

## Một số độ phức tạp thời gian cơ bản

| **Tên**                                      | **Định Nghĩa**                                                                                                                                                            | **Ví Dụ**                                                                                                                                                                |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Độ phức tạp hằng số **O(1)**                 | Một thuật toán được gọi là có độ phức tạp hằng số O(1) khi thời gian chạy **không phụ thuộc** vào kích thước dữ liệu đầu vào.                                             | các toán tử cơ bản, truy cập vào một phần tử của mảng, in ra 1 xâu, …                                                                                                    |
| Độ phức tạp tuyến tính **O(n)**              | Một thuật toán được gọi là có độ phức tạp tuyến tính O(n) khi thời gian chạy **thay đổi tuyến tính** phụ thuộc vào kích thước dữ liệu đầu vào                             | Kích thước dữ liệu đầu vào là 10, thời gian chạy mất 1s. Khi kích thước dữ liệu đầu vào là 100, thời gian chạy mất 10s thì khi đó ta nói thuật toán có độ phức tạp O(n). |
| Độ phức tạp theo hàm số logarit **O(log n)** | Một thuật toán được gọi là có độ phức tạp theo hàm số logarit O(log n) khi thời gian chạy **thay đổi theo dạng hàm số logarit** phụ thuộc vào kích thước dữ liệu đầu vào. | tìm kiếm nhị phân, các thao tác với cây nhị phân, ...                                                                                                                    |

## Cách đánh giá độ phức tạp của thuật toán

### Quy tắc

Đối với lập trình thi đấu, thường khi ta nói “**một thuật toán có độ phức tạp O(A)**” có nghĩa là có tối đa **A** câu lệnh **O(1)** được thực thi. Việc đánh giá độ phức tạp chính là tính số lần thực thi tối đa của một câu lệnh O(1).

Để đánh giá độ phức tạp của một thuật toán không đệ quy có thể tóm gọn lại như sau:

1. Tính số lần lặp tối đa của một vòng lặp
2. Nếu các vòng lặp nối tiếp nhau thì cộng số lần lặp tối đa của các vòng lặp với nhau
3. Nếu các vòng lặp lồng nhau thì nhân số lần lặp tối đa của các vòng lặp với nhau

Ta sẽ đi qua một số ví dụ để có thể hiểu hơn về cách đánh giá một thuật toán trong thực tế

### Ví dụ 1: Phụ thuộc vào giá trị n

Yêu cầu: In ra dòng chữ “GCC” với số lần phụ thuộc vào giá trị n nhập từ bàn phím.

```csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            int n = int.Parse(Console.ReadLine());
            for (int i = 0; i < n; i++)
            {
                Console.WriteLine("GCC");
            }
        }
    }
}
```

Từ đoạn code trên, ta có thể thấy:

- Lệnh in ra dòng chữ “GCC” là một lệnh có độ phức tạp hằng số **O(1)**.
- Vòng lặp này lặp lại tối đa **n** lần. Do đó, theo quy tắc 1 ở trên ta sẽ có độ phức tạp vòng lặp là **O(1 * n)** hay là **O(n)**

### Ví dụ 2: Phụ thuộc vào giá trị n và m

Yêu cầu: In ra dòng chữ “GCC” với số lần phụ thuộc vào giá trị n và m nhập từ bàn phím.

```csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            int n = int.Parse(Console.ReadLine());
            int m = int.Parse(Console.ReadLine());
            for (int i = 0; i < n; i++)
            {
                for (int j = 0; j < m; j++)
                {
                    Console.WriteLine("GCC");
                }
            }
        }
    }
}
```

Ở đoạn code phía trên, ta thấy có:

- Một vòng **for** lặp **m** lần in ra dòng chữ “GCC”. Do đó độ phức tạp của vòng for sẽ là **O(m)** như ví dụ 1.
- Vòng **for j** lại được lồng trong vòng **for i** lặp lại **n** lần. Do đó theo quy tắc 2, độ phức tạp hai vòng for này là **O(n * m)**

### Ví dụ 3

Yêu cầu: In ra dòng chữ “GCC” với số lần phụ thuộc vào giá trị n và m nhập từ bàn phím, tương tự ví dụ 2.

```csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            int n = int.Parse(Console.ReadLine());
            int m = int.Parse(Console.ReadLine());
            for (int i = 0; i < n; i++)
            {
                Console.WriteLine("GCC");
            }
            for (int i = 0; i < n; i++)
            {
                for (int j = 0; j < m; j++)
                {
                    Console.WriteLine("GCC");
                }
            }
        }
    }
}
```

Ví dụ này được gộp từ yêu cầu của hai ví dụ trên. Theo quy tắc 3, hẳn bạn cũng đã đoán được độ phức tạp là **O(n + n * m)** đúng không?

Thực tế thì đáp án này không sai, nhưng do sự khác biệt giữa **O(n * m)** và **O(n + n * m)** là không quá lớn nên để đơn giản ta sẽ nói chương trình có độ phức tạp **O(n * m)**.

# 2. Tách String

Sử dụng lệnh `Split(<kí tự tách>,<StringSplitOptions>)`

| **Giá Trị**          | **Ý Nghĩa**                                                                      |
| -------------------- | -------------------------------------------------------------------------------- |
| `None`               | **Mặc định**: giữ lại tất cả các phần, kể cả rỗng nếu có 2 delimiters liên tiếp. |
| `RemoveEmptyEntries` | Bỏ **chuỗi rỗng** trong kết quả (những phần không có ký tự giữa delimiters).     |
| `TrimEntries`        | Xóa khoảng trắng của các phần tử sau khi tách                                    |
Có thể kết hợp các option với nhau bằng `|`

VD:
```csharp
var s = "a,  ,b";
var arr = s.Split(',');
// arr = ["a", "   ", "b"]
```

VD2:
```csharp
var s = "a  , ,  b ";
var arr = s.Split(',', StringSplitOptions.RemoveEmptyEntries);
// arr = ["a  ", "  b "]
```
VD3:
```csharp
var s2 = "a , , b , c ";
var arr = s2.Split(',', StringSplitOptions.TrimEntries);
// arr = ["a", "", "b", "c"]
```
VD4:
```csharp
var s2 = "a , , b , c ";
var arr = s2.Split(',', StringSplitOptions.TrimEntries | StringSplitOptions.RemoveEmptyEntries);
// arr = ["a", "b", "c"]
```
# 3. Vào Ra File

- Có khá nhiều cách để nhập và in ra dữ liệu qua file trong C# nhưng cách đơn giản và thuận tiện nhất đó là dùng `StreamWriter` / `StreamReader`
    
- Thuộc thư viện **`include System.IO;`**
    

### **Cú Pháp đọc file** 

Bảo đảm file tồn tại và nằm trong thư mục "`.\bin\Debug\netx.x`"

1 dòng đầu tiên :
```Csharp
StreamReader sr = new StreamReader("<Tên file>");
string s = sr.ReadLine(); // đọc dòng đầu tiên
Console.WriteLine(s);
sr.Close(); // nhớ Close file
```
Đọc hết file:
```csharp
StreamReader sr = new StreamReader("<Tên File>");
string s;
while ((s = sr.ReadLine()) != null)
{
	Console.WriteLine(s);
}
sr.Close(); // nhớ Close file
```

### **Cú Pháp ghi file** 

```csharp
StreamWriter sw = new StreamWriter("<Tên file>",<bool ghi tiếp ?>);
```

Nếu file chưa tồn tại sẽ tự động tạo file trong thư mục "`.\bin\Debug\netx.x`"

VD:
```csharp
StreamReader sr = new StreamReader("data.in");
StreamWriter sw = new StreamWriter("data.out");// mặc định là ghi đè
string s;
sw.WriteLine(s);
sr.Close();      
sw.Close();
```

VD2: 
```csharp
StreamReader sr = new StreamReader("data.in");
StreamWriter sw = new StreamWriter("data.out",true);// ghi tiếp
string s;
sw.WriteLine(s);
sr.Close();      
sw.Close();
```
#### `LƯU Ý`:

Để đọc hoặc ghi dự liệu một file thì file đó phải ở trong thư mục "`.\bin\Debug\netx.x`". Nếu không ta có thể thay thế tên file bằng đường dẫn của file đó.