---
title: "My Ruby notes"
published: true
comments: true
---

### Comments trong Ruby

Comments có hai cách là từng dòng hoặc nhiều dòng:
- Với comments từng dòng: cấu trúc chúng ta có thể xem ví dụ bên dưới.

```ruby
# Đây là comments trong Ruby.
```

Như ta thấy comments được viết au kí tự “#”.

- Muốn comments nhiều dòng ta có thể viết trong khối có cấu trúc bắt đầu bằng =begin và kết thúc bằng =end.

```ruby
=begin
Đây là comments nhiều dòng trong Ruby.
...
=end
```

### Khai báo trong Ruby

Ruby sử dụng các chữ các, số, dấu gạch dưới để khái báo các biến, phương thức, lớp, … nhưng không được bắt đầu bằng chữ số hoặc trùng lặp với các keyword và cũng có thể bắt đầu bằng kí tự gạch dưới. Ruby cũng phân biệt chữ hoa với chữ thường.

Ngoài ra còn một số điều khá thú vị nữa đó là: Ruby sử dụng dấu câu trong định danh như: ?, !

### Keywords

 class do def if end begin next nil,… chúng ta cần tránh khai báo các hàm biến class trùng lặp với những từ khóa này.

### Khoảng trắng và tab

Thông thường Ruby sẽ bỏ qua các khoảng trắng.
Ví dụ: Hai câu lệnh dưới đây được Ruby hiểu theo nghĩa giống nhau.

```ruby
puts 8 + 5
puts 8+5
```

###  Cấu trúc block

Có hai cách viết block:
Cách 1: Trong cùng một dòng:
Ví dụ: In chuỗi “Ruby!” ba lần

```ruby
3.times { print "Ruby! " }
```

Block được giới hạn trong hai dấu ngoặc kép tương tác với các interator methods bên ngoài trước nó.
Cách 2: Trên nhiều dòng: block được giới hạn giữa các keywords do và end.
Ví dụ: In các số từ 1 tới 10.

```ruby
1.upto(10) do |x|
  print x
end
```

### Thực thi chương trình

Không như các ngôn ngữ khác như C hay Java Ruby là scripting language se không có chương trình hay phương thức main là ghi thực thi chương trình nó sẽ khởi chạy đầu tiên. Trong Ruby nó sẽ thực thi từ những dòng đầu tiên của file mã nguồn được chỉ định.

### Các kiểu dữ liệu và đối tượng trong Ruby

#### Number

Cũng giống như hầu hết các ngôn ngữ lập trình khác đều có các kiểu dữ liệu cơ bản như integer, float, … chúng đều được định nghĩa trong class Numeric. Đối tượng trong lớp Numeric.

Chú ý: +) Trong phép chia số nguyên integer không như các ngôn ngữ như C hay Java, nếu phép chia không hết Ruby sẽ tự động làm tròn và lấy cận trên của giá trị trả về của phép toán đó thay vì cận dưới như C hay Java.

Ví dụ: -7/3 thực thế bằng -2.33 nhưng đây là phép chia số nguyên vì vậy kết quả sẽ là -3.

+) -a/b tương đương với a/-b nhưng có thể không tương đương với (-a/b).

Mũ trong Ruby:
Ví dụ:
```ruby
x**2 => # x mũ hai hay x*x
x**-1 => # x mũ trừ 1 = 1/x
x**¼ => # x mũ (một phần tư), nhưng ¼ là chia số nguyên kết quả sẽ = 0 => kết quả cuối cùng là = 0 (x mũ không).
x**1.0/4.0 => # căn bậc bốn của x
```

#### Text

Text là đối tượng của lớp String.
Class String cung cấp một loạt các phương thức như: tìm kiếm, chèn, xóa, lấy chuỗi con, ghép các chuỗi với nhau,…
Chuỗi kí tự dễ dàng nhận thấy nhất đó là bên trong dấu nháy đơn hoặc nháy kép.

#### String Operators

```ruby
# - Sử dụng toán tử “+” (concatenates).
# Ví dụ: planet = “Earth”
# “Hello” + “” + planet # sẽ in ra đối tượng với nội dung: “Hello Earth”
# Nhưng ở đây có một vấn đề đó là chuỗi “Hello” được ghép nối với một đối tượng planet như vậy cần phải chuyển đổi đối tượng planet (toán hạng sau chuỗi Hello) thành định dạng chuỗi String. Mặc dù “Hello” + “” + planet vẫn in ra kết quả bình thường.
# Câu lệnh trên sẽ trở thành: “Hello” + “” + planet.to_s
# - Sử dụng block.
# Để đơn giản hơn: không cần convert planet object ta có thể sử dụng block chứa đối tượng trong đó và đặt nó vào trong khu vực dấu kép cùng với chuỗi “Hello” trước đó - “Hello #{planet}”.

# - Sử toán tử “<<” : planet = “Sun”
# planet << “ ” << “*” # kết quả là: “Sun *”
# Lợi thế của cách này đó là không phải tạo ra một object mới để lưu trữ chuỗi “Hello Earth” nữa mà nó ghép nối vào đối tượng đã khai báo trước đó rồi đó là planet.

# Lưu ý: - Cũng giống như sử dụng toán tử “+” khi sử dụng toán tử “<<” nó cũng sẽ không tự động chuyển đổi các toán hạng bên phải toán tử của nó nếu toán hạng bên phải toán tử đang sử dụng thì nó sẽ ngầm hiểu răng đó là mã hóa của một kí tự trong bảng mã kí tự ví dụ: 67 tương ứng với chữ cái C.

# - Sử dụng toán tử: “*” lặp lại các các kí tự phía bên trái “*” với số lần bằng số bên phải kí tự “*” ( planet = “Sun*”*3 ) => kết quả: “Sun*Sun*Sun*”.
```

#### Truy cập các kí tự và chuỗi con

```ruby
# - Toán tử [] được cung cấp cho các đối tượng lớp String để có thể truy cập các chỉ số (bắt đầu bằng 0 hoặc -s.lenght # s là đối tượng chứa một chuỗi nào đó) của chuỗi. Như vậy các chuỗi được tổ chức như một mảng các kí tự với thứ tự và chỉ số xác định.
```
