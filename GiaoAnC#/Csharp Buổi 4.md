# 1. ValueTuple<T1, T2>

- ValueTuple dùng để ghép từ 2 -> 7 kiểu dữ liệu (có thể khác nhau) lại thành một.
Cách khai báo:
```Csharp
// khai báo 1 ValueTuple
(<kiểu dữ liệu 1>, <Kiểu dữ liệu 2>,...,<kiểu dữ kiệu 7>) MyValueTuple;
// ví dụ khai báo 1 ValueTuple và gán giá trị
(string, int) vt2 = ("Hello",6);
```

Vẫn còn những cách khác, các em có thể tìm hiểu thêm

Gán giá trị:
```Csharp
MyValueTuple = ("GCC",3);
//Hoặc
MyValueTuple.Item1 = "3"
MyValueTuple.Item2 = 6;
```

```Csharp
//in cả ValueTuple ra màn hình
Console.WriteLine(MyValueTuple); // in ra theo kiểu (<giá trị 1>, <giá trị 2>,...)
//in 1 giá trị của ValueTuple ra màn hình
Console.WriteLine(MyValueTuple.Item1); //in ra giá trị đầu tiên
...
Console.WriteLine(MyValueTuple.Item7); //in ra giá trị thứ 7
```

**`Note: Lúc này ValueTuple giống như 1 kiểu dữ liệu, ta có thể sử dụng như 1 biến ta hay dùng.`**

# 2. List

Ở trong `using System.Collections.Generic;`

- **Đặc điểm**: Danh sách có thứ tự, truy cập bằng chỉ số.
    
- **Khi dùng**: Cần thêm/xóa/truy cập nhanh theo chỉ số, dữ liệu có thể trùng lặp.
    

```csharp
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        List<int> numbers = new List<int>() { 5, 1, 4, 2, 3 };
        numbers.Sort(); // Sắp xếp tăng dần
        Console.WriteLine(string.Join(", ", numbers));
    }
}
```

- Thao tác cơ bản:
	- Thêm phần tử: `numbers.Add(<value>);`
	- Thêm phần tử tại 1 vị trí nào đó `numbers.Insert(index, value);
	- Xóa phần tử theo index: `numbers.RemoveAt(index);`
	- Xóa phần tử theo giá trị: `numbers.Remove(value);`
	- Xóa toàn bộ : `numbers.Clear();`
	- Kích thước : `numbers.Count;`
	- Truy cập phần tử: `numbers[index];`
`
# 3. Dictionary

Ở trong `using System.Collections.Generic;`
- Lưu trữ cặp **khóa-giá trị**.

Cách sử dụng:

- Khởi tạo:

```Csharp
Dictionary<string,int> mp = new Dictionary<string, int>();
```

- thêm phần tử:

```Csharp
mp[1] = "One";      // giống mp[1] = "One"
mp.Add(2, "Two");  // giống insert
```

- Truy cập:

```Csharp
Console.WriteLine(mp[1]); // One
```

- Duyệt

```CSharp
foreach (KeyValuePair<string, int> p in mp) 
// khác với ValueTuple
{
    Console.WriteLine($"{p.Key} : {p.Value}");
}
```

### SortedDictionary<TKey, TValue>

Giống `Dictionary<TKey, TValue>` nhưng sắp xếp `Key` theo thứ tự tăng dần

# 4. HashSet

- Lưu trữ **các phần tử duy nhất**.

Cách sử dụng:

- Khởi tạo:

```Csharp
HashSet<int> s = new HashSet<int>();
```


- Thêm phần tử:

```Csharp
s.Add(30);
s.Add(20);
s.Add(30);
```

- Kiểm tra 1 phần tử tồn tại trong HashSet:

```Csharp
if (s.Contains(20))
{
	Console.WriteLine("Found");
}
```

- Duyệt

```Csharp
foreach (int x in s)
{
    Console.WriteLine(x);
}
```

- Xóa phần tử

```Csharp
s.Remove(20)
```

### SortedSet

Giống `HashSet` nhưng tự động sắp xếp phần tử theo thứ tự tăng dần