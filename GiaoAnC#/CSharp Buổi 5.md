# 1. Stack
### Khái niệm

- Là một loại cấu trúc dữ liệu như mảng, vector (dùng để lưu trữ và quản lý, thao tác dữ liệu).
- Tuân theo nguyên tắc **LIFO (Last In First Out)**: phần tử cuối cùng được thêm vào sẽ lấy ra đầu tiên.
### Sử dụng

**Khai báo:**

```Csharp
using System;
using System.Collections.Generic;

Stack<int> st = new Stack<int>();
```

Hàm thường dùng:

`Push(<value>)` : thêm phần tử
`Pop()` : Lấy và xóa phần tử cuối cùng
`Peek()` : Lấy và không xóa phần tử cuối cùng
`Count` : Số lượng phần tử trong Stack

# 2. Queue
### Khái niệm

- Là một loại cấu trúc dữ liệu
- Tuân theo nguyên tắc **FIFO (First In First Out)**: phần tử đầu tiên được thêm vào sẽ là phần tử đầu tiên được lấy ra.

### Sử dụng:

**Khai báo**:

```Csharp
using System;
using System.Collections.Generic;

Queue<int> q = new Queue<int>();
```

Hàm thường dùng:

- `Enqueue(<value>)`: Thêm một phần tử mới vào cuối queue.
- `Dequeue()` : Lấy và xóa phần tử đầu queue
- `Peek()`: Lấy và không xóa phần tử đầu queue
- `Count`: Số lượng phần tử trong queue

# 3. PriorityQueue

### Khái niệm

- Là một loại cấu trúc dữ liệu
- Tuân theo nguyên tắc **FIFO (First In First Out)**: phần tử đầu tiên được thêm vào sẽ là phần tử đầu tiên được lấy ra.
- Ưu tiên số priority thấp trước
### Sử dụng:

**Khai báo**:

```Csharp
using System;
using System.Collections.Generic;

PriorityQueue<int, int> pq = new PriorityQueue<int, int>();
```

Hàm thường dùng:

- `Enqueue(<value>, <priority>)`: Thêm một phần tử mới vào cuối queue.
- `Dequeue()` : Lấy và xóa phần tử đầu queue
- `Peek()`: Lấy và không xóa phần tử đầu queue
- `Count`: Số lượng phần tử trong queue
