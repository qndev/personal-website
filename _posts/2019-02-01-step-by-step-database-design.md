---
title: "Thiết kế và tạo lập CSDL"
published: true
---

<img src="{{ '/assets/images/database.jpeg'}}" alt="" height="522px" width="700px">

### Quy trình thiết kế CSDL

##### Bước 1:
* Người thiết kế phải nghiên cứu kỹ nghiệp vụ của hệ thống sẽ phát triển. Bước này thường
được thực hiện thông qua việc gặp mặt nói chuyện và đặt câu hỏi với những người sẽ sử
dụng hệ thống.

##### Bước 2:
* Viết lên giấy mục đích cơ bản của hệ thống. Ví dụ, ta có thể viết “Hệ thống này sẽ được dùng
để xử lý đơn đặt hàng của khách hàng và theo dõi chúng để phục vụ cho các nghiệp vụ kế
toán và lưu kho.” Thêm vào đó, ta có thể liệt kê các yêu cầu của hệ thống. Các yêu cầu này sẽ
giúp chúng ta xây dựng cấu trúc của CSDL và các nghiệp vụ. Ví dụ, ta có thể xây dựng một
danh sách các yêu cầu như “Phải có khả năng truy xuất địa chỉ của khách hàng để gửi thư.”

##### Bước 3:
* Xây dựng các mẫu biểu nhập liệu tạm (lên giấy). (Nếu trong quá trình thiết kế các bảng xuất
hiện các ý tưởng về nghiệp vụ, ta nên ghi lại bào danh sách các yêu cầu như ở bước 2.) Cách
tiếp cận cụ thể tùy thuộc vào trạ ng thái của hệ thống hiện tại.

   * Nếu hệ thống hiện tại chưa được tin học hóa, ta có thể dùng hệ thống giấy tờ sẵn có để
thiết kế nháp các bảng dựa vào các biểu mẫu sẵn có. Các mẫu biểu này sẽ được chuẩn
hóa về sau.
   * Nếu CSDL phải được chuyển đổi từ hệ thống tin học hiện tại, dùng các bảng có sẵn để
bắt đầu.
   * Nếu ta phải xây dựng hệ thống từ đầu (ví dụ:, cho một doanh nghiệp hoàn toàn mới),
phác thảo qua trên giấy các biểu mẫu người sử dụng có thể dùng.

##### Bước 4:
* Dựa vào các biểu mẫu xây dựng ở bước 3, ta có thể phác thảo các bảng lên giấy. Nếu dữ liệu
chưa được chuẩn hóa ngay, ta có thể bắt đầu bằng cách tạo ra một bảng dữ liệu lớn, phi
chuẩn rồi sau đó tiến hành các bước chuẩn hóa.

##### Bước 5:
* Ta có thể tham khảo các giấy tờ có sẵn hoặc các báo cáo từ những hệ thống cũ. Đối với
những hệ thống hiện tại không đáp ứng được yêu cấu người sử dụng thường các báo cáo
quan trọng sẽ bị thiếu. Ta có thể tạo nháp các báo cáo này lên giấy.

##### Bước 6:
* Tiếp theo, phải đảm bảo rằng các bảng dữ liệu tạo ở bước 4 có chứa các dữ liệu của các mẫu
biểu ở bước 5. Nếu các thông tin này chưa có, cần phải thêm vào bảng hoặc tạo ra bảng dữ
liệu mới.

##### Bước 7:
* Trên giấy, ta đưa các bản ghi dữ liệu vào bảng đã phác thảo, cố gắng dùng dữ liệu thật nếu có
thể.

##### Bước 8:
* Bây giờ ta có thể bắt đầu quá trình chuẩn hóa. Đầu tiên là xác định các khóa ứng viên cho
mỗi bảng rồi chọn ra khóa chính. Chú ý phải chọn khóa chính nhỏ nhất, ổn đị nh, đơn giản và
phổ biến. Tốt nhất là mỗi bảng phải có một khóa chính!

##### Bước 9:
* Sau đó ta cần phải chọn khóa ngoại hoặc thêm vào bảng liên quan khóa ngoại nếu cần thiết.
Tiếp theo ta thiết lập mối quan hệ giữa các bảng, chú ý phân biệt các quan hệ 1-1 hay 1-
nhiều. Nếu tồn tại quan hệ nhiề u-nhiều ta cần tạo các bảng quan hệ.

##### Bước 10:
* Bước tiếp theo ta xác định xem các bảng hiện đã ở dạng chuẩn một chưa. Các trường dữ liệu
có đảm bảo tính đơn nhất chưa? Có tồn tại các nhóm dữ liệu lặp lại? Đưa dữ liệu về dạng
chuẩn 1 (1NF).

##### Bước 11:
* Kiểm tra xem các bả ng đã ở dạ ng chuẩn 2. Mỗi bảng chỉ mô tả một thự c thể? Các trường
không phải khóa chính đã phụ thuộc hoàn toàn vào khóa chính? Hay nói cách khác, trường
khóa chính có thể được dùng để truy xuất các trường của bảng? Phân rã để được dạng chuẩn
2 (2NF). Nếu bảng có khóa chính tổng hợp ta cần phân rã bằng cách chia khóa chính này và
các trường phụ thuộc vào mỗi phần của khóa chính vào mỗi bảng.

##### Bước 12:
* Kiểm tra xem các bảng đã ở dạng chuẩn 3. Có tồn tại các trường tính toán hay không? Có tồn
tại sự phụ thuộc lẫn nhau của các trường không phải là khóa chính. Loại bỏ các trường tính
toán. Loại bỏ các trường phụ thuộc lẫn nhau bằng cách tạo ra các bảng phụ tra cứu.

##### Bước 13:
* Dùng các bảng đã được chuẩn hóa ở bước 12, ta có thể xây dựng mối quan hệ giữa các bảng.

##### Bước 14:
* Tạo các bảng dùng Microsoft SQL Server. Nếu ta dùng Microsoft SQL Server, tạo quan hệ
giữa các bảng bằng Enterprise Manager (dùng công cụ trợ giúp tạo sơ đồ quan hệ). Nhập dữ
liệu mẫu vào các bảng.

##### Bước 15:
* Tạo ra các truy vấn, biểu nhập liệu và các báo cáo mẫu. Khi tạo các đối tượng này, các thiếu
xót trong thiết kế sẽ xuất hiện. Sửa chữa, cập nhật thiết kế nếu cần thiết.

##### Bước 16:
* Tham khảo ý kiến người dùng bằng cách yêu cầu họ đánh giá các biểu nhập liệu và các báo
cáo. Chúng có đáp ứng được yêu cầu của người sử dụng không? Nếu không ta cần phải sữa
lại. Chú ý chuẩn hóa lại dữ liệu nếu cần thiết (các bước 8-12).

##### Bước 17:
* Đến đây ta có thể trở lại màn hình thiết kế bảng để thêm vào các ràng buộc về nghiệp vụ.

##### Bước 18:
* Tạo các biểu nhập liệu, báo cáo và truy vấn cuối. Phát triển ứng dụng. Sửa lại thiết kế nếu
thấy cần thiết.

##### Bước 19:
* Yêu cầu người dùng chạy thử hệ thống. Cập nhật thiết kế nếu cần thiết.

##### Bước 20:
* Cuối cùng hệ thống đã sẵn sàng để triển khai.
