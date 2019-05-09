---
title: "Dạng chuẩn NF trong Database"
published: true
---


### Chuẩn hóa

Chuẩn hóa là một kỹ thuật giúp người thiết kế nhóm các dữ liệu và đặt chúng trong các bảng phù
hợp. Do vậy việc chuẩn hóa một CSDL là hết sức quan trọng trước khi ta bắt đầu làm việc với
nó. Các dạng chuẩn có những quy tắc chỉ rõ các yêu cầu tạo một CSDL quan hệ.

##### Dạng chuẩn 1 (1NF):
* Bảng dữ liệu thỏa mãn các đặc tính của một quan hệ (relation) được coi là ở dạng chuẩn 1. Một
relation không thể chứa các thuộc tính tập hợp hay có nhiều giá trị. Dưới đây là quy tắc của dạng
chuẩn 1.

> Một quan hệ được coi là ở dạng chuẩn 1 khi và chỉ khi các miền giá trị của quan hệ chứa
> các giá trị đơn nhất.

##### Dạng chuẩn 2 (2NF):
* Điều kiện để đạt được dạng chuẩn 2 là bả ng dữ liệu phải ở dạng chuẩn 1. Mục đích của dạng
chuẩn 2 là đảm bảo rằng thông tin chứa trong quan hệ chỉ mô tả một thực thể duy nhất.

> Chú ý: Một quan hệ ở dạng chuẩn 2 khi và chỉ khi nó ở dạng chuẩn 1 và tất cả các trường
> không phải khóa chính phải phụ thuộc hoàn toàn vào khóa chính của quan hệ.

Để hiểu rõ hơn đị nh nghĩa dạng chuẩn 2 ở trên ta cần định nghĩa khái niệm key attribute. Mỗi
thuộc tính của quan hệ tham gia vào ít nhất một khóa ứng viên (candidate key) được coi là key
attribute của quan hệ. Tất cả các thuộc tính khác được gọi là non-key.

Dạng chuẩn 2 quy định rằng tất cả các thuộc tính không phải thành phần của khóa ứng viên phải
phụ thuộc hoàn toàn vào khóa ứng viên.

##### Dạng chuẩn 3 (3NF):
* Mặc dù dạng chuẩn 2 đã loại bỏ được các bất thường có thể xuất hiện trong các bảng chưa ở
dạng chuẩn 1, nhưng không phải đã loại bỏ được tất cả và cần thiết phải thực hiện dạng chuẩn
hóa tiếp theo để đảm bảo loại bỏ hết những bất thường đó. Các tính bất thường này có thể xảy ra do dạng ch uẩn 2 có thể chứa những thuộc tính không liên quan trực tiếp đến thực thể được mô tả
bởi các khóa ứng viên trong quan hệ. Dạng chuẩn 3 được mô tả dưới đây:

> Chú ý: Một quan hệ R được coi là ở dạng chuẩn 3 khi và chỉ khi nó ở dạng chuẩn 2 và các
> thuộc tính không phải là khóa chính của R phải phụ thuộc vào mỗi khóa ứng viên của R.

Để hiểu rõ hơn về dạng chuẩn 3 chúng ta tìm hiểu khái niệm sự phụ thuộc ngoại suy (transitive
dependence), khái niệm này dựa vào một trong những tiên đề của Armstrong. Coi A, B và C là
ba thuộc tính của quan hệ R, ta có các mối quan hệ sau A->B và B->C. Từ các mối quan hệ này
ta suy ra là A->C. Như đã đề cập ở trên, mối quan hệ giữa A->C là phụ thuộc ngoại suy
(transitive).
Dạng chuẩn 3 khác với dạng chuẩn 2 ở chỗ tất cả các thuộc tính không phải khóa chính trong
dạng chuẩn 3 phải phụ thuộc trực tiếp vào khóa ứng viên của mỗi quan hệ. Nếu có thuộc tính phụ
thuộc vào trường khóa theo quan hệ ngoại suy điều đó có ý nghĩa là các thuộc tính đó mô tả
không chỉ trường khóa mà còn mô tả thuộc tính không phải khóa. Do đó thông tin không phụ
thuộc trực tiếp vào khóa chính mặc dù rõ ràng thuộc tính này có quan hệ với khóa chính.

### Các quy tắc xây dựng CSDL chuẩn hóa

##### Quy tắc 1- Loại bỏ các nhóm dữ liệu lặp lại

Tạo bảng riêng cho mỗi tập thuộc tính lặp lại và gán cho mỗi bảng một khóa chính. Chúng ta
xem lại ví dụ về CSDL Customers-Order.

| Dữ liệu chưa chuẩn hóa trong CSDL |
| --------------------------------- |
| Order ID 1..n                     |
| Orderdate                         |
| CustomerID 1..n                   |
| Orderdate                         |
| Requireddate                      |
| Shippeddate                       |
| Quantity                          |
| Discount                          |
| Company name                      |
| Address                           |
| City                              |
| Product ID 1..n                   |
| Productname                       |
| UnitPrice                         |

Trong danh sách dữ liệu gốc, mỗi một mô tả về khách hàng theo sau là một danh sách các thuộc
tính liên quan đến khách hàng đó. Một khách hàng có thể đặt 10 món hàng nhưng cũng có nguời
chỉ đặt 1 món hàng. Để tìm lời giải cho câu hỏi, "Khách hàng A có mua món hàng B hay không?"
trước tiên chúng ta cần tìm các chi tiết đặt hàng của khách hàng A, sau đó ta phải duyệt qua danh
sách hàng hóa đó. Đây là phương pháp không hiệu quả và rất rườm rà.

Vấn đề này được giải quyết nếu ta đưa dữ liệu về chi tiết đơn hàng sang một bảng khác. Tách các
nhóm dữ liệu lặp lại trong thông tin về chi tiết đơn hàng của khách hàng sẽ cho ta dữ liệu ở dạng
chuẩn 1. Trường Customer id trong bảng Orders trùng với khóa chính trong bảng Customer, co
ta khóa ngoại liên kết hai bảng. Lúc này ta có thể giải quyết câu hỏi trên bằng cách truy xuất trực
tiếp: kiểm tra xem giá trị customer id của khách hàng A và giá trị ID của mặt hàng B có cùng
nằm trong bảng Orders hay không.


| Customer Table                   | Orders Table                     |
| -------------------------------- | -------------------------------- |
| Customer ID        Primary Key   | Customer ID        Foreign Key   |
| Company Name                     | Order ID Item                    |
| Address                          | ID Itemname                      |
| City                             | Unitprice                        |
|                                  | Order date                       |
|                                  | Required date                    |


##### Quy tắc 2- Loại bỏ dữ liệu dư thừa

Nếu một trường chỉ phụ thuộc vào một phần của trường khóa chính chứa nhiều giá trị, đưa dữ
liệu đó sang một bảng.

Một phần của bảng Orders như sau:


| Order ID | Customer   | ItemID     | Itemname | Unitprice |
| -------- | ---------- | ---------- | -------- | --------- |
| 1        | A          | 101        | E        | 10        |
| 2        | B          | 102        | F        | 15        |
| 3        | C          | 101        | G        | 10        |
| 4        | D          | 101        | H        | 10        |

Với cấu trúc bảng Orders trên, các chi tiết mặt hàng xuất hiện lặp lại với mỗi khách hàng đặt
cùng một món hàng. Sẽ khả thi hơn nếu ta chỉ lưu trường Item ID.
Nếu ta muốn định nghĩa lại một mặt hàng, có nghĩa là phải cung cấp giá trị itemID mới, sự thay
đổi này phải thực hiện cho mọi đơn đặt hàng có chứa mặt hàng đó! Nếu chúng ta bỏ qua một số
bản ghi, ta sẽ có các đơn đặt hàng có cùng mặt hàng nhưng lại khác ID. Đây được gọi là Cập
nhật bất thường (Update anomaly).

Giả sử mặt hàng cuối cùng hết hàng và không được sản xuất tiếp – nghĩa là mặt hàng đó đã lỗi
thời. Các bản ghi đó sẽ bị xóa khỏi CSDL và như vậy mặt hàng đó sẽ không được lưu ở bất kỳ
đâu thậm chí không được lưu trong lịch sử mua hàng của khách hàng! Đây được gọi là Xóa bât
thường (Delete anomaly). Để tránh lỗi này ta cần có dạng chuẩn 2.

Để đạt được dạng chuẩn 2, tách các trường phụ thuộc vào cả 2 phần của khóa chính khỏi các
trường chỉ phụ thuộc vào trường Item ID. Kết quả ta được 2 bảng: bảng “Items” chứa tên, giá và
các chi tiết khác của mặt hàng; và bảng “Orders” liệt kê danh sách các mặt hàng đặt bởi mỗi
khách hàng.

| Customer Table                   | Orders Table                     | Item Table                       |
| -------------------------------- | -------------------------------- | -------------------------------- |
| CustomerID        Primary Key    | CustomerID        Foreign Key    | ItemID        Primary Key        |
| CompanyName                      | OrderID                          | Itemname                         |
| Address                          | ItemID                           | Unitprice                        |
| City                             | Required date                    |
|                                  | Shippeddate                      |
|                                  | Quantity                         |
|                                  | Discount                         |


##### Quy tắc 3 – Loại bỏ các trường không phụ thuộc vào khóa chính

Nếu các trường không tham gia mô tả khóa chính, tách chúng sang một bảng khác.

Bảng Orders

* OrderID
* CustomerID
* ItemID
* Requireddate
* Shippeddate
* Quantity
* Discount

Bảng Orders thỏa mãn dạng chuẩn 1 do không còn chứa các dữ liệu lặp lại. Nó cũng thỏa mãn
dạng ch uẩn 2 do không tồn tại khóa chính nhiều giá trị. Nhưng khóa chính của bảng là Order ID,
và các trường quantity và discount của mỗi mặt hàng không cần được lưu trong bảng này. Để
đạt được dạng chuẩn 3, chúng phải được đưa sang một bảng khác. Do các trường này mô tả chi
tiết đơn hàng nên bảng mới là Order Details phù hợp nhất để lưu dữ liệu này. Do các trường này
mô tả mặt hàng và chi tiết đơn hàng nên khóa chính sẽ là kết hợp của hai trường Item ID và
Order ID.


| Customer Table                   | Orders Table                     | Item Table                       | Order Details                    |
| -------------------------------- | -------------------------------- | -------------------------------- | -------------------------------- |
| CustomerID        Primary Key    | CustomerID        Foreign Key    | ItemID        Primary Key        | OrderID                          |
| CompanyName                      | OrderID                          | Itemname                         | CustomerID                       |
| Address                          | ItemID                           | Unitprice                        | ItemID                           |
| City                             | Required date                    |                                  | Requireddate                     |
|                                  | Shippeddate                      |                                  | Shippeddate                      |
|                                  |                                  |                                  | Quantity                         |
|                                  |                                  |                                  | Discount                         |

### References

[1] [Normalization of Database](https://www.studytonight.com/dbms/database-normalization.php)

[2] [Wiki Database normalization](https://en.wikipedia.org/wiki/Database_normalization)

[3] [ What is Normalization? 1NF, 2NF, 3NF & BCNF with Examples](https://www.guru99.com/database-normalization.html)

[4] [Introduction to Data Normalization: A Database "Best" Practice](http://agiledata.org/essays/dataNormalization.html)
