---
title: "My git notes"
published: true
comments: true
---

### 1: Hệ thống quản lý phiên bản phân tán (DVCS).

<img src="{{ '/assets/images/DVCS.png' | absolute_url }}" alt="DVCS">

* #### VCS (Quản lý phiên bản mã nguồn)

Thưc chất đó là hệ thống các máy chủ, local lưu lại các thông tin thay đổi của các file/tập tin.

* #### DVCS (Quản lý phiên bản mã nguồn phân tán)

Mô hình này sinh ra để giải quyết các vấn đề mà các phiên bản VCS trước đó gặp phải hay quản lý các phiên bản mã nguồn thông thường chúng ta hay làm (sao lưu các phiên bản ra một thư ).

VCS cục bộ đó là tạo lập một cơ sở dữ liệu riêng cho nó để lưu lại các phiên bản mã nguồn.

VCS tập trung đó là khi máy chủ gặp sự cố hoặc không có kết nối internet thì các thành viên trong nhóm không thể cộng tác được với nhau.

Do vậy mà DVCS ra đời đã giải quyết mọi những vấn đề từ các phiên bản VCS trước đó.

Câu hỏi đặt ra về vấn đề máy chủ trong hệ thống gặp vấn đề như không có kết nối internet hoặc dữ liệu trên đó bằng cách nào đó đã bị mất hết. Như vậy vấn đề backup lại data cho server (máy chủ) cần kết hợp các máy local lại với nhau. Đến đây lại có vấn đề nữa nảy sinh đó là: cần có bao nhiêu các local trong hệ thống cần thiết để backup lại máy chủ đó với phiên bản mã nguồn tương ứng đã mất?

Lại còn trường hợp một số máy local cũng mất data trong cùng thời điểm với server thì việc backup lại data trên server có được không và nếu được thì data có toàn vẹn.

### 2: Thông tin cơ bản về hệ thống.

* #### Snapshot: Tiếng việt được dịch ra đó là – bức ảnh – lưu lại một khoảnh khắc tại một thời gian xác định.

* #### Git lưu trữ dữ liệu dưới dạng snapshot, một tập hợp các snapshot nhỏ của các tập tin nhưng có một điểm đặc biệt đó là chỉ có những tập tin nào đó có sự thay đổi nó mới lưu lại thông tin, còn các snapshot còn lại nó sẽ tạo một tham chiếu tới snapshot đã tồn tại trước đó. Như vậy không gian lưu trữ sẽ được tối ưu hơn các phiên bản VCS trước đó.

* #### Trạng thái của git:

  <div style="text-align:center"><img src="{{ '/assets/images/state.png' | absolute_url }}" alt="Working area, Staging area, Repisitory area."></div>

  * #### Các trạng thái cơ của git: Modified, Staged, Commited.

  * #### Working area trạng thái của các tập tin có thể là: traced, untracked, modified, unmodified.

  * #### Staging area (khu vực quan sát theo dõi tập tin): staged, unstaged.

  * #### Repository area (khu vực git): commited →unmodified

Các trạng thái này chúng ta sẽ tìm hiểu sâu hơn ở các phần tiếp theo đó là File Status LifeCyle.

### 3: Cài đặt git.

Tài liệu tham khảo cách cài đặt git trên các nền tảng hệ điều hành khác nhau.

[1] [Install Git](https://www.atlassian.com/git/tutorials/install-git)

[2] [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
