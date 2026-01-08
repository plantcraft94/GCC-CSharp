# I. IEnumerable
#### Định nghĩa:
IEnumerable là một **interface** được cung cấp bởi thư viện **.NET** cho phép các **object implement** nó có thể được **duyệt tuần tự** thông qua **foreach** và có thể làm việc với **LINQ.** 

*Note: IEnumerable chỉ quy định khả năng duyệt, không yêu cầu **object** đó phải **lưu trữ dữ liệu** hay là một **data-container**
#### Cấu trúc:
Mã nguồn:
```Csharp
public interface IEnumerable 
{
    IEnumerator GetEnumerator();
}
```
Dạng Generics:
```Csharp
public interface IEnumerable<T>
{
    IEnumerator<T> GetEnumerator();
}
```

IEnumerable không lưu **trạng thái duyệt** mà chỉ đảm bảo **cung cấp** một **Enumerator** (thứ sẽ duyệt các đối tượng implement IEnumerable). Và một IEnumerable có thể được nhiều Enumerator độc lập duyệt cùng lúc.
Hàm `GetEnumerator()` **tạo ra và trả về một iterator** (IEnumerator hoặc IEnumerator\<T> với IEnumerable\<T>) có vị trí nằm ở trước phần tử đầu tiên của thứ tự duyệt.

#### Ví dụ:
```CS
public class MyIntergerCollection : IEnumerable
{
	private readonly int[] _listInt;

	public MyIntergerCollection(int[] listInt)
	{
		_listInt = listInt;
	}

	public IEnumerator GetEnumerator()
	{
		return _listInt.GetEnumerator();
	}
}
```
 khi thực hiện duyệt các phần tử từ đầu đến cuối như sau
``` CS
List<int> listInt = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
var customMyCollection = new MyIntergerCollection(listInt.ToArray());
foreach (var item in customMyCollection)
{
    Console.WriteLine(item);
}
```
kết quả
``` 
1
2
3
4
5
6
7
8
9
10
``` 
# II. IEnumerator
#### Định nghĩa:
IEnumerator là interface mô tả **enumerator**, đối tượng thực hiện việc **duyệt tuần tự** và **lưu trữ trạng thái** của quá trình liệt kê.

*Note: Có thể thấy nó khá giống con trỏ khi nó hiển thị trạng thái của phần tử đang duyệt nhưng về bản chất thì không phải vậy.  IEnumerator cho biết có thể di chuyển tới phần tử tiếp theo hay không và lấy giá trị / tham chiếu của phần tử hiện tại và có thể trở lại trạng thái ban đầu của nó (khi vừa được khởi tạo, vị trí ở trước phần tử đầu tiên trong thứ tự duyệt) chứ không thể di chuyển linh hoạt như con trỏ
#### Cấu trúc:
```Cs
public interface IEnumerator
{
    bool MoveNext();
    object Current { get; }
    void Reset();
}
```

Dạng Generics:
```Cs
public interface IEnumerator<T> : IDisposable
{
    bool MoveNext();
    T Current { get; }
}
```
Như ta đã thấy trong mã nguồn: 
- `MoveNext()` trả về **true** nếu có thể duyệt đến phần tử tiếp theo, ngược lại trả về **false**.
- `Current()` trả về phần tử hiện tại của danh sách đang duyệt.
- `Reset()` trả IEnumerator về trạng thái khởi tạo. Trên thực tế không có ai dùng hàm này do trong .NET hiện đại nó thường không được hỗ trợ
#### Ví dụ:
```CS
public class MyIntergerEnumerator : IEnumerator
{
	private readonly int[] _listInt;
	private int _currentIndex;

	public MyIntergerEnumerator(int[] listInt)
	{
		_listInt = listInt;
		_currentIndex = _listInt.Length;
	}

	public object Current
	{
		get
		{
			return _listInt[_currentIndex];
		}
	}

	public bool MoveNext()
	{
		_currentIndex--;

		return _currentIndex >= 0;
	}

	public void Reset()
	{
		_currentIndex = _listInt.Length;
	}
}
```

``` CS
public class MyIntergerCollection : IEnumerable
{
	private readonly int[] _listInt;

	public MyIntergerCollection(int[] listInt)
	{
		_listInt = listInt;
	}

	public IEnumerator GetEnumerator()
	{
		return new MyIntergerEnumerator(_listInt);
	}
}
```

``` CS
List<int> listInt = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
var customMyCollection = new MyIntergerCollection(listInt.ToArray());
foreach (var item in customMyCollection)
{
    Console.WriteLine(item);
}
```

Kết quả
```
10 
9
8
7
6
5
4
3
2
1
````

*Note: Ví dụ này cố tình cài đặt `IEnumerator` để duyệt **từ cuối về đầu**, nhằm cho thấy rằng thứ tự duyệt **không phụ thuộc vào dữ liệu gốc**, mà phụ thuộc vào **cách Enumerator được cài đặt**.


=> Kết luận:  có thể thấy IEnumerable định nghĩa “có thể duyệt”, còn IEnumerator định nghĩa “duyệt như thế nào” 