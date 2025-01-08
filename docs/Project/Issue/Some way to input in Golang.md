---
Created: 13:04 07-01-2025
tags:
  - issue
---
Go cung cấp nhiều cách khác nhau để nhập dữ liệu từ người dùng. Mỗi phương thức có ưu điểm và ứng dụng riêng. Dưới đây là các cách phổ biến để nhập dữ liệu và khi nào bạn nên sử dụng chúng:

### 1. **`fmt.Scan` và `fmt.Scanln`**

- **`fmt.Scan`**: Đọc dữ liệu từ đầu vào chuẩn (stdin) và phân tích theo các tham số đã chỉ định, tách các giá trị bằng khoảng trắng. Cách này có thể đọc nhiều giá trị cùng lúc, nhưng yêu cầu các giá trị phải được phân tách bởi khoảng trắng hoặc newline.
- **`fmt.Scanln`**: Tương tự như `fmt.Scan`, nhưng chỉ đọc cho đến khi gặp ký tự newline (`\n`), do đó, nó sẽ không đọc thêm dữ liệu sau dấu newline. Sử dụng khi bạn muốn đọc một dòng duy nhất.

**Ví dụ:**

```go
var name string
var age int
fmt.Print("Enter your name and age: ")
fmt.Scan(&name, &age)  // Đọc cả tên và tuổi
fmt.Println("Name:", name, "Age:", age)
```

**Khi nào dùng?**

- Dùng `fmt.Scan` hoặc `fmt.Scanln` khi bạn cần nhập dữ liệu từ người dùng và phân tích chúng theo kiểu cơ bản (ví dụ: string, int).
- Phù hợp khi bạn muốn đọc dữ liệu từ một dòng (cho `Scanln`).

### 2. **`fmt.Fscan`, `fmt.Fscanln`, `fmt.Fscanf`**

Những hàm này hoạt động tương tự như `Scan`, nhưng cho phép bạn chỉ định nguồn nhập liệu từ một `io.Reader` khác thay vì nhập từ stdin. Ví dụ: bạn có thể sử dụng chúng với một tệp thay vì đọc từ bàn phím.

**Ví dụ:**

```go
var name string
var age int
input := strings.NewReader("John 25")
fmt.Fscan(input, &name, &age)
fmt.Println(name, age)
```

**Khi nào dùng?**

- Khi bạn muốn đọc dữ liệu không phải từ stdin, ví dụ như từ tệp hoặc chuỗi (string).
- Thích hợp cho các ứng dụng làm việc với tệp hoặc đọc từ các nguồn khác.

### 3. **`bufio.Scanner`**

- **`bufio.Scanner`** là một công cụ mạnh mẽ để đọc từng dòng hoặc từng từ trong một tệp hoặc stdin. Nó cung cấp các phương thức để đọc từng dòng dữ liệu (mỗi dòng là một chuỗi) hoặc theo từng từ (tách bởi khoảng trắng).

**Ví dụ:**

```go
scanner := bufio.NewScanner(os.Stdin)
fmt.Print("Enter your name: ")
scanner.Scan()
name := scanner.Text()  // Lấy dữ liệu vừa nhập
fmt.Println("Hello, " + name)
```

**Khi nào dùng?**

- Dùng khi bạn cần xử lý từng dòng hoặc từng từ riêng biệt, ví dụ khi đọc từ một tệp hoặc nhập dữ liệu từ bàn phím.
- Cũng rất hữu ích khi cần đọc dữ liệu lớn theo từng đoạn (chẳng hạn với tệp lớn).

### 4. **`os.Stdin` và `ioutil.ReadAll` (hoặc `io.ReadAll` từ Go 1.16)**

- **`os.Stdin`** có thể được sử dụng kết hợp với các hàm như `io.Reader` để đọc dữ liệu từ stdin. Bạn có thể sử dụng `ioutil.ReadAll` (hoặc `io.ReadAll` nếu sử dụng Go 1.16+) để đọc tất cả dữ liệu đầu vào và lưu vào một biến.

**Ví dụ:**

```go
data, err := ioutil.ReadAll(os.Stdin)
if err != nil {
    log.Fatal(err)
}
fmt.Println(string(data))
```

**Khi nào dùng?**

- Sử dụng khi bạn muốn đọc tất cả dữ liệu đầu vào từ stdin (ví dụ, khi nhận một chuỗi dài hoặc một tệp).
- Được dùng trong các ứng dụng yêu cầu đọc toàn bộ nội dung đầu vào một lần, không phải từng dòng.

### 5. **`strconv` (Chuyển đổi giữa chuỗi và kiểu dữ liệu khác)**

- Go không tự động chuyển đổi giữa chuỗi và các kiểu dữ liệu khác. Bạn cần sử dụng các hàm từ gói `strconv` để chuyển đổi dữ liệu nhập vào từ chuỗi sang kiểu dữ liệu khác (ví dụ: số nguyên, số thực).

**Ví dụ:**

```go
var input string
fmt.Print("Enter a number: ")
fmt.Scanln(&input)
number, err := strconv.Atoi(input)  // Chuyển chuỗi thành số nguyên
if err != nil {
    fmt.Println("Invalid number:", err)
} else {
    fmt.Println("You entered:", number)
}
```

**Khi nào dùng?**

- Sử dụng khi bạn cần chuyển đổi giữa các kiểu dữ liệu, chẳng hạn như từ chuỗi sang số nguyên (`strconv.Atoi`), từ chuỗi sang số thực (`strconv.ParseFloat`), v.v.

### 6. **`os.Args` (Nhận đối số từ dòng lệnh)**

- Nếu bạn muốn nhận đầu vào từ dòng lệnh (trong các ứng dụng CLI), bạn có thể sử dụng `os.Args` để lấy các tham số được truyền vào khi chạy chương trình.

**Ví dụ:**

```go
fmt.Println("Command line arguments:", os.Args)
```

**Khi nào dùng?**

- Dùng khi bạn muốn nhận các tham số từ dòng lệnh khi chạy chương trình, ví dụ: truyền đối số khi chạy chương trình từ terminal.

---

### Tóm tắt các cách nhập dữ liệu trong Go:

1. **`fmt.Scan`, `fmt.Scanln`**: Dùng khi bạn cần nhập dữ liệu từ bàn phím theo từng giá trị (chuỗi, số nguyên, v.v.).
2. **`fmt.Fscan`, `fmt.Fscanln`, `fmt.Fscanf`**: Dùng khi bạn cần đọc dữ liệu từ nguồn khác ngoài stdin, ví dụ từ tệp.
3. **`bufio.Scanner`**: Dùng khi bạn cần đọc dữ liệu từng dòng hoặc từng từ.
4. **`ioutil.ReadAll` hoặc `io.ReadAll`**: Dùng khi bạn muốn đọc toàn bộ dữ liệu đầu vào từ stdin (thích hợp cho tệp hoặc dữ liệu lớn).
5. **`strconv`**: Dùng để chuyển đổi giữa chuỗi và các kiểu dữ liệu khác.
6. **`os.Args`**: Dùng để nhận đối số từ dòng lệnh.

### Nên dùng cái nào khi nào?

- **Sử dụng `fmt.Scan`/`fmt.Scanln`** khi bạn chỉ cần đọc một hoặc một vài giá trị từ người dùng.
- **Sử dụng `bufio.Scanner`** khi bạn muốn đọc từng dòng dữ liệu (ví dụ khi đọc một tệp lớn hoặc khi cần đọc dữ liệu từ stdin theo từng đoạn).
- **Sử dụng `ioutil.ReadAll` hoặc `io.ReadAll`** khi bạn muốn đọc toàn bộ đầu vào một lần.
- **Sử dụng `strconv`** khi bạn cần chuyển đổi dữ liệu nhập vào từ chuỗi thành các kiểu dữ liệu khác như số nguyên, số thực, v.v.
- **Sử dụng `os.Args`** khi bạn cần xử lý đối số dòng lệnh khi chạy chương trình.