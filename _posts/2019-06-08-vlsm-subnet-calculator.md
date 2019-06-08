---
title: "VLSM - Ví dụ quy hoạch IP cho một công ty"
published: true
comments: true
---

### Một số lưu ý.

* Cấu trúc của địa chỉ IP:

Địa chỉ ipv4  có độ dài là 32 bits được chia làm 2 phần là host và phần network.
Tùy vào giải địa chỉ ip cũng như việc chia mạng con của từng lớp khác nhau mà ta sẽ có số bits của phần host cũng như phần network khác nhau.

<img src="{{ '/assets/images/708px-CPT-Network-IPAddressDivision.svg' | absolute_url }}" alt="IP Address Structure">

* Ip Address trước và sau khi chia mạng con.

<img src="{{ '/assets/images/sub.png' | absolute_url }}" alt="IP Address Structure">

* Private IP Addresses

   | Class | Private Networks | Subnet Mask | Address Range |
   |:-----:|:----------------:|:-----------:|:-------------:|
   |A|10.0.0.0|255.0.0.0|10.0.0.0 - 10.255.255.255|
   |B|172.16.0.0 - 172.31.0.0|255.240.0.0|172.16.0.0 - 172.31.255.255|
   |C|192.168.0.0|255.255.0.0|192.168.0.0 - 192.168.255.255|

### Quy hoạch IP.

> Giả sử công ty ABC nào đó có 7 phòng ban: P01, P02, P03, P04, P05, P06, P07
> với số lượng nhân viên tương ứng là: 54, 33, 18, 13, 8, 7, 3.
> Quy hoạch địa chỉ IP cho các phòng ban trên với giải địa chỉ là: 192.168.1.0/24.

Ta sẽ quy hoạch các giải địa chỉ ip cho các phòng ban có số lượng nhân viên nhiều nhất đến ít nhất.

P01: Để có thể cung cấp đủ 54 hosts cho phòng này cần: 6 hosts bit (2^6 - 2 = 62 hosts trên mạng con).
Bởi vì ta có 8 host bits tất cả (192.168.1.0/24 - 24 netid bits) vì vậy cần mượn 2 bits của phần host để tạo subnets (2^2 = 4 subnets). Bốn subnets đó là:

```console
   192.168.1.0/26 - 255.255.255.192 (Mask)
   192.168.1.64/26
   192.168.1.128/26
   192.168.1.192/26
```
Áp dụng giải ip 192.168.1.0/26 cho P01, như vậy còn lại 3 subnets. Tiếp tục áp dụng giải ip 192.168.1.64/26 cho P02.

Do P02 có 33 người tương ứng cần ít nhất 33 hosts cho phòng này, tương ứng với 6 hosts bit (2^6 - 2 = 62 hosts trên mạng con này). Như vậy 192.168.1.64/26 đáp ứng được yêu cầu đó. Vậy ta chọn giải ip này cho P02 và còn lại 2 giải địa chỉ ip là : 192.168.1.128/26 và 192.168.1.192/26.

Tiếp tục P03 cần 5 hosts bit (2^5-2=30 hosts treen mạng con). Bởi vì ta có 6 host bits tất cả từ giải ip 192.168.128/26 vì vậy cần mượn 1 bit của phần của host để tạo subnets (2^1 = 2 subnets) và 2 subnets đó là:

```console
   192.168.1.128/27 - 255.255.255.224 (Mask)
   192.168.1.160/27 - 255.255.255.224 (Mask)
```
Áp dụng giải ip 192.168.1.128/27 cho P03.

Cứ tiếp tục như vậy ta có bảng tổng kết quy hoạch giải địa chỉ ip cho tất cả các phòng ban trong bảng dưới đây.

<img src="{{ '/assets/images/subnettable.png' | absolute_url }}" alt="Subnet Table">

Như vậy với kỹ thuật chia mạng con này ta có thể tiết kiệm được tối đa việc cấp phát và sử dụng địa chỉ ip một cách tối ưu nhất.
