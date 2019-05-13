---
title: "Công cụ quản lý gói trong Debian"
published: true
comments: true
---

## Package management tools
### Main tools

- [Apt](#apt) - công cụ quản lý gói chính.
- [dpkg](#dpkg) - công cụ cài đặt tệp Debian.
- [apt-get](#apt-get) - công cụ xử lý gói APT - giao diện dòng lệnh.
- [Synaptic ](#synaptic ) - công cụ quản lý gói thông qua giao diện đồ hoạ.

### Apt
- APT ( Advanced Package Tool) là một bộ công cụ để quản lý các gói Debian.

- apt cung cấp giao diện dòng lệnh cấp cao cho hệ thống quản lý gói.

- Mục đích chính của apt là cung cấp một cách xử lý gói hiệu quả theo cách thức dễ dàng cho người dùng cuối, có nghĩa là nó có ít tùy chọn lệnh hơn nhưng đầy đủ và hiệu quả. Trên hết, nó cho phép một vài tùy chọn theo mặc định thực sự hữu ích cho người dùng cuối.

- apt có nhiều lợi thế hơn các công cụ quản lý gói khác có sẵn trong Debian dành cho quản trị viên máy chủ. Một số ưu điểm này bao gồm dễ sử dụng so với các kết nối đầu cuối đơn giản (SSH) và khả năng được sử dụng trong các tập lệnh quản trị hệ thống, do đó có thể được tự động hóa bởi tiện ích lập lịch cron. Một số trường hợp sử dụng apt là:

#### Update
- Để tải xuống, cập nhật thông tin gói từ tất cả các nguồn được cấu hình, thực hiện nâng cấp gói hoặc tìm kiếm và hiển thị chi tiết về tất cả các gói có sẵn để cài đặt.

```bash
$ sudo apt update
```
#### Search
- Các gói có thể được tìm kiếm thông qua:

```bash
$ apt search <packagename>
```

  <img src="{{ '/assets/images/apt_search.png' | absolute_url }}" alt="" height="489px" width="700px">

#### Show
- Hiển thị thông tin về gói bao gồm các gói phụ thuộc, kích thước cài đặt và tải xuống, nguồn của gói, mô tả nội dung gói, v.v. Sẽ hữu ích để xem thông tin này trước khi cho phép apt xóa gói hoặc trong khi tìm kiếm gói mới để cài đặt.

```bash
$ apt show <packagename>
```

  <img src="{{ '/assets/images/apt-show.png' | absolute_url }}" alt="" height="489px" width="700px">

#### Xử lý gói
- Thêm - cài đặt, xóa gói:

```bash
$ sudo apt install apt
$ sudo apt remove apt
$ sudo apt install </path/to/deb/file/debfile.deb>
```

#### Autoremove
- autoremove được sử dụng để loại bỏ các gói được cài đặt tự động để đáp ứng các phụ thuộc cho các gói khác và hiện không còn cần thiết vì các phụ thuộc đã thay đổi hoặc (các) gói cần chúng đã bị xóa trong thời gian đó.

```bash
$ sudo apt autoremove
```

#### Upgrade
- updrade được sử dụng để cài đặt các bản nâng cấp có sẵn của tất cả các gói hiện được cài đặt trên hệ thống từ các nguồn được định cấu hình qua sources.list. Các gói mới sẽ được cài đặt nếu được yêu cầu để đáp ứng các phụ thuộc, nhưng các gói hiện tại sẽ không bao giờ bị xóa. Nếu việc nâng cấp cho gói yêu cầu loại bỏ gói đã cài đặt thì việc nâng cấp cho gói này không được thực hiện.

```bash
$ sudo apt upgrade
```

### dpkg

dpkg là một công cụ để cài đặt, xây dựng, gỡ bỏ và quản lý các gói Debian.

Bản thân dpkg được điều khiển hoàn toàn thông qua các tham số dòng lệnh, bao gồm chính xác một hành động và không hoặc nhiều tùy chọn. Tham số hành động cho dpkg biết phải làm gì và các tùy chọn kiểm soát hành vi của hành động theo một cách nào đó.

```bash
$ sudo dpkg -i <--install> <package-file>
```

### apt-get

apt-get là một công cụ để tự động cập nhật Debian, nhận và cài đặt các gói / chương trình debian!

```bash
$ sudo apt-get install <packagename>
```
Cài đặt một hoặc nhiều package, mỗi package tượng ứng với tên chứ không cần phải là tệp đầy đủ (ví dụ: apt-utils chứ không cần chỉ rõ tệp: apt utils_1.4.9_amd64.deb).

Tệp /etc/apt/source.list được sử dụng để định vị các gói mong muốn.

### Synaptic

Synaptic được cài đặt theo mặc định trong Debian. Đây là công cụ với giao diện đồ hoạ, dễ dàng sử dụng đối với người dùng cuối.

  <img src="{{ '/assets/images/synaptic_02.png' | absolute_url }}" alt="" height="495px" width="700px">

### References

[1] [Wiki Package Management](https://wiki.debian.org/PackageManagement)

[2] [APT](https://manpages.debian.org/stretch/apt/apt.8.en.html)

[3] [dpkg](https://manpages.debian.org/stretch/dpkg/dpkg.1.en.html)

[4] [apt-get](https://manpages.debian.org/stretch/apt/apt-get.8.en.html)

[5] [Synaptic](https://manpages.debian.org/stretch/synaptic/synaptic.8.en.html)
